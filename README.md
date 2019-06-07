# About
This is a skeleton repository that you can use as a starting point for your gateway projects when choosing to use a multi-module structure.

In order to use this as a starting point for you projects follow these steps:
1) Select the `Clone of download` dropdown in the top left then click `Download ZIP`.
2) Create a local folder for your project and extract the contents of the downloaded zip into it.
3) Fill in details in the following files:
   * `build.gradle`: On line [30](build.gradle#L27) replace the default URL with the proper gateway URL (and add possible credentials - documentation [here](https://github.com/ca-api-gateway/gateway-developer-plugin/wiki/Gateway-Export-Plugin#specifying-gateway-export-and-gateway-connection-properties))
   * `settings.gradle`: On line [7](settings.gradle#L7) replace `<project.name>` with any chosen name for your project.

See more detail on using the gateway-developer-plugin here: [gateway-developer-plugin](https://github.com/ca-api-gateway/gateway-developer-plugin/wiki)

# Starting your project.
Put a valid gateway license in the `docker` folder. The license file should be called `license.xml`. For information on getting a license see the [License Section from the Gateway Container readme](https://hub.docker.com/r/caapim/gateway/).

## Exporting from your Gateway
First of all, create local folders to match the structure from your Gateway folders.
* for each folder in your Gateway, create one locally (they don't need the same name)
* for each local folder, add a `build.gradle` file and a `settings.gradle` file to make them gradle modules
* in each `settings.gradle` file, set the module name by adding `rootProject.name = '<module_name_of_your_choice>'`
* in each `build.gradle` file, link it to a Gateway policy folder by adding the `GatewayExportConfig` section, as documented [here](https://github.com/ca-api-gateway/gateway-developer-plugin/wiki/Gateway-Export-Plugin#specifying-gateway-export-and-gateway-connection-properties)
* edit the `settings.gradle` file in the root project folder and add your new modules in the `include` statement, each one single-quoted and comma-separated. A sample can be found [here](https://github.com/ca-api-gateway-examples/gateway-developer-example/blob/master/settings.gradle)

After the structure setup, you can export the policies and services from the Gateway by running:

```./gradlew export```

This will export the changes to the various project folders. Note that your local edits will be overridden by changes from the gateway

## Building a Solution
In order to package the solution into something that can be applied to the CA API Gateway run the following Gradle command:

```./gradlew build```

## Running the Solution
In order to run the solution you need to do the following:

1) Put a valid gateway license in the `docker` folder. The license file should be called `license.xml`. For information on getting a license see the [License Section from the Gateway Container readme](https://hub.docker.com/r/caapim/gateway/).
2) Make sure you have already built the solution by running `./gradlew build`
3) Start the Gateway Container by running: `docker-compose up --force-recreate`

After the container is up and running you can connect the CA API Gateway Policy Manager to it.

## Stopping Docker container
To stop the running Gateway Container, run the following command:

`docker-compose  down`

# Giving Back
## How You Can Contribute
Contributions are welcome and much appreciated. To learn more, see the [Contribution Guidelines][contributing].

## License

Copyright (c) 2018 CA. All rights reserved.

This software may be modified and distributed under the terms
of the MIT license. See the [LICENSE][license-link] file for details.


 [license-link]: /LICENSE
 [contributing]: /CONTRIBUTING.md
