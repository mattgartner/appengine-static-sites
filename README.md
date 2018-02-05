# Google Cloud Platform - App Engine Static Website Hosting Starter Kit
This repo provides a basic set of files and instructions to deploy a static website to Google Cloud Platform's App Engine. 

## Demo Site on App Engine
https://static-sites-demo.appspot.com/

## Why?
When deciding where to host a static website, there are a couple different options:
1. Shared hosting providers (Dreamhost, GoDaddy, 1and1, etc)
2. Virtual Private Servers (VPS - like DigitalOcean or Linode)
3. Infrastructure as a Service (IaaS - like Amazon's EC2 or Google Compute Engine)
4. Platform as a Service (PaaS - like Heroku, or App Engine)

Most people tend to lean towards Option 1, shared hosting providers, as they're typically the most user-friendly and cheapest option. One problem people experience, whether they realize it or not, is noisy-neighbors that are sharing the same server as you that aren't as separate as you may think. 

Virtual Private Servers are a good option for a little more separation from other customers, but often require much more knowledge to setup and maintain the server. Similarly, Infrastructure as a Service options are often too complicated for the average user that just wants their website online.

Platform as a Service (PaaS) offerings are a good intermediate option, but can become costly since they're typically comprised of many different services (including monitoring, logging, scaling, etc) that you don't have to setup or manage yourself.

What if we could utilize a PaaS solution, built on top of one of the most scalable cloud infrastructure providers in the world, but not have to spin up even a single instance? 

What this repo/tutorial will enable is to effectively host your website from Google's Cloud Storage offering at extremely low costs (most likely free for most sites), but reap the benefits of it's PaaS offering, App Engine. For example, if you were to simply upload your static site files to Google Cloud Storage, they could all be publicly accessible, but there's currently no way to specify root access to your site through a custom domain. In layman's terms, this means your customers could see the site fine from www.example.com, but if they went to example.com directly, they would see nothing. By utilizing App Engine, we'll not only get the ability to use www and non-www URLs, but Google will also manage the SSL certificates and automatically renew them. Now your customers can visit https://example.com and https://www.example.com as well 

## How?
If you already have a Google Cloud Platform account setup with the Google Cloud SDK installed, you can skip below to step 4.
1. First, you need a Google Account to get started on Google Cloud Platform. Head over to https://cloud.google.com/, and click the "Try it Free" button.
2. Create a new project: https://console.cloud.google.com/projectcreate
You can name this whatever you'd like, but the project ID needs to be unique and can't be changed later.
3. Install the Google Cloud SDK: Follow the guide here (https://cloud.google.com/appengine/docs/standard/python/download) to install Python locally if you don't already have it. If you don't know Python, don't worry, you won't need to understand it to follow along here. MacOS comes pre-installed with it, so if you're on a Mac you can open up a Terminal and type "python -v" to see if it's installed". Then, follow steps 2-4 on the link above to download and install the Google Cloud SDK, the Python components, and Git if you don't already have it installed locally. 
4. Clone this repo into your editor of choice (I'm using Visual Studio Code) 
5. If you want to upload this template as-is, open your terminal, make sure you're in the top-level directory of this repository which has the app.yaml file in it, and type "gcloud app deploy app.yaml". If you've never setup the Google Cloud SDK, you may be prompted to authenticate and select a project. There are a few flags you can add to the command that make things a bit easier, especially if you manage multiple projects on Google Cloud. By adding --project [project-name] you can specify which project to deploy to. I would recommend this in case your SDK configuration is defaulting to a different project. You can also specify a version number with the --version flag. For simplicity, you can start with "v0" or "v1" and increment each time you upload a new version of the site. If you want to do any sort of A/B testing, you may want to name your versions differently. My commands typically end up looking something like "gcloud app deploy app.yaml --project my-project-name --version v3". 
If you want to modify the template before uploading it, feel free to make any HTML, CSS or JS changes in your editor before deploying. 
6. That's it! Your new site will be available immediately on your appspot.com site (https://[your-project-name].appspot.com). You can also add a custom domain (e.g. example.com) - more info on that here: https://cloud.google.com/appengine/docs/standard/python/mapping-custom-domains

## Additional Resources 
Google App Engine Python Standard Environment Documentation: https://cloud.google.com/appengine/docs/standard/python/ 
App Engine Documentation for other languages: https://cloud.google.com/appengine/docs/ 

## Pricing
You can monitor the pricing of your site on the App Engine Dashboard: https://console.cloud.google.com/appengine
If you set everything up properly, App Engine should never need to launch an instance, saving you from the $.05/hr instance charges, and you will only be charged for things like Bandwidth and Storage access. You can monitor it all under the Billing Status section of the dashboard. Google Cloud has a generous Always Free tier which will enable many small static sites to run for free!