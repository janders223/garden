# Patterns

## continuousdelivery.com

#articles
#pocket

![](https://readwise-assets.s3.amazonaws.com/static/images/article3.5c705a01b476.png)

[source](https://continuousdelivery.com/implementing/patterns)

### Highlights from July 26, 2021

- Only build packages once. We want to be sure the thing we’re deploying is the same thing we’ve tested throughout the deployment pipeline, so if a deployment fails we can eliminate the packages as the source of the failure.
- Deploy the same way to every environment—including development. This way, we test the deployment process many, many times before it gets to production, and again, we can eliminate it as the source of any problems.
- Keep your environments similar. Although they may differ in hardware configuration, they should have the same version of the operating system and middleware packages, and they should be configured in the same way.
- Smoke test your deployments. Have a script that validates all your application’s dependencies are available, at the location you have configured your application. Make sure your application is running and available as part of the deployment process.
