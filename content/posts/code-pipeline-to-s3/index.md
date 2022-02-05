---
title: "How To Set Up an AWS CodePipeline for Uploading Your Static Site To S3 On Every Commit"
date: 2019-08-12 20:10:12-08:00
draft: false
tags: [tech, tutorial, aws]
author: Brittany Ellich
resources:
  - name: "featured-image"
    src: "featured-image.jpeg"
---

One of the best traits for a Software Engineer is to be lazy. Lazy engineers tend to find ways to make their lives easier, by automating menial tasks to reduce the amount of time they need to spend on trivial things, so that they can focus on things that are more important.

Today, I'm going to help you be lazy.

If you stuck with me through my last tutorial on hosting a static website on AWS, you now have a static website that is hosted from an AWS S3 bucket. While that is an excellent way to get your content on the web, you likely don't want to manually build and upload your files into S3 every time you make a change to your website. Today I will give you an overview on how to build a pipeline through AWS, so that every time you commit code to your master branch those changes get automatically deployed into your S3 bucket.

---

![Pipeline](pipeline.jpeg)

First, let's review a little bit of terminology, in case you aren't familiar with deployment pipelines.

## CI/CD - Continuous Integration/Continuous Delivery

Continuous Integration/Continuous Delivery (CI/CD) refer to a set of practices for designing infrastructure. Continuous Integration refers to the ability for a development team to check in small changes on an ongoing basis into code repositories. It shouldn't take a lot of effort to get your code into whatever source code repository you prefer to use.

Continuous Delivery does the rest of the work, taking code from the source code repository and deploying it in an automated way. The whole process is designed so that when code is committed to whichever branch you specify, it is taken from the repository through all of the testing and whatever other steps are required to end up showing up in your application. This is also referred to as a deployment pipeline.

For professional teams, this generally also includes some different environments, such as a staging environment to view and test changes before they end up in production. This tutorial is designed for the small team or individual projects that don't necessarily require multiple environments, but could easily be adapted for it.

---

## Step One: Set Up Your Repository For CodeBuild

AWS CodeBuild is a continuous integration service from Amazon Web Services. It can be used to compile your code, run tests, and even deploy in certain cases like publishing to S3. It's relatively simple to set up, and once it is set up you can customize your build to include many different steps. In our case, we're just going to work on getting static files into an Amazon S3 bucket.

1. CodeBuild works off of files called buildspec.yml. Yaml is a commonly used language for configuration files, which is relatively easy to read. Add a new file to the highest folder of your repository called buildspec.yml.
2. In the buildspec.yml file, add the following code, assuming you are following the tutorial I outlined for creating your static site with GatsbyJS. Replace brittanyellich.com with whatever you have named your S3 bucket:

```version: 0.2
phases:
  install:
    runtime-versions:
      nodejs: 8
    commands:
    - npm install --global yarn
    - npm install --global gatsby-cli
    - yarn
    - gatsby build
    - aws s3 sync public s3://brittanyellich.com --delete --acl public-read
```

Edit the buildspec.yml file for your needs. For example, if you aren't creating a Gatsby site, you can remove the second and fourth commands that are Gatsby specific.

## Step Two: Set Up CodeBuild From Your Repository To S3

This next step will create a project in AWS that will be responsible for building from your source code repository into your S3 bucket.

1. Login to the [AWS Console](https://aws.amazon.com/console/) and use the search function to find CodeBuild.
2. Ensuring you are in the same region as your S3 bucket, select "Create build project" from the CodeBuild dashboard.
3. Enter the relevant details about your project and then click submit. The relevant details you will need to enter include the following:

- The name of the project
- Which source code repository you are using (ex. GitHub). If you're not using an AWS specific source code repository, you will have to log in and allow AWS access to your account.
- Which repository in your source code account to build from.
- The environment you plan to use. For example, for my project I chose the Ubuntu, standard, 2.0 image, which should work for any node projects you're building.
- Select "Use a buildspec file" (that's what you created in step one).

Once the CodeBuild section is configured, you should be able to click on "Start build" and see your project building into your S3 bucket.

### Step Three: Set Up Code Pipeline Between Your Repository and Your CodeBuild

Once CodeBuild is set up and successfully running, the last step is to set up a [CodePipeline](https://aws.amazon.com/codepipeline/). The goal here is that whenever you commit to your specified branch (ex. master), the pipeline will take your new source code and trigger the build in CodeBuild. This creates true Continuous Delivery, you no longer have to worry about deploying your changes!

1. Log in to the AWS Console and use the search function to navigate to CodePipeline.
2. Click on "Create pipeline".
3. Name your pipeline and select "New service role". This will create a role that will eventually need to permissions to publish to S3. Click "Next".
4. On the next page, choose your source provider. This is the same source provider that you used in CodeBuild (ex. GitHub). Connect your account if you haven't already done so, and select your repository and your branch. Typically this will be the "master" branch, if that is the main branch you commit to. Keep the recommended change detection options for your source provider.
5. On the "Add build stage" page, select AWS CodeBuild as the build provider. In the region you chose to create your CodeBuild project in, select the "Project name" in the drop down and select "Next".
6. Click on "Skip deploy stage". This isn't necessary for this project since the deployment is being done to S3 in the last step of the buildspec.yml file. If you were not building a static site and had something that needed to be deployed to EC2 or any other server, this is where you would configure it.
7. Review your options and click "Create pipeline".

You're done! You should now be able to commit new code to your master branch and see it show up on your website afterward. How cool is that?

As an extra note, if you're using CloudFront to deliver your code you will need to invalidate your CloudFront cache whenever code is pushed to your S3 bucket. If you'd like, you can do this by adding the following step to your buildspec.yml file under the "Commands" section after you do your S3 deploy:

`- aws cloudfront create-invalidation --distribution-id DISTRIBUTION-ID --paths /*`

Replace DISTRIBUTION-ID with your CloudFront distribution id. This will invalidate all paths in your code, which can be a little bit time consuming, but for a small website shouldn't take very long.
