---
title: "Deploying Astro to AWS Amplify"
description: "Here are the basic steps to deploy your Astro site to AWS Amplify."
pubDate: "29 Mar 2023"
---

Here are the basic steps to deploy your Astro site to AWS Amplify.
It is assumed that you have already created an AWS account and have installed the Amplify CLI.
In addition, you should also have an Astro GitHub repository.

## Steps
1. Create an AWS Amplify App: Log in to your AWS account and navigate to the Amplify Console. Click on the "Create App" button and follow the prompts to create a new app.  In my case, I created a Website app.

1. Connect your Git repository: Once your app is created, you'll need to connect it to your Git repository where your Astro site is hosted. Follow the instructions to connect your repository to the Amplify App.

1. Set up a build environment: Amplify needs to know how to build your site. You'll need to create a build environment using the Amplify Build settings. This environment should include your build command, which for Astro is typically ```npm run build```.  *ALSO* Astro will build your site in a subdirectory named 'dist'.  In order for the deployment to distribute the proper files, change the 'baseDirectory' artifact to '/dist', like this:  ```baseDirectory: /dist```

1. Configure the deployment settings: Under the "Deploy" tab in Amplify, select the deployment settings for your site. For an Astro static site, you'll want to choose the "Amazon S3" option.

1. Set up DNS and SSL: Finally, you'll need to configure DNS and SSL for your site. Amplify can automatically set up both of these for you using its built-in tools.


