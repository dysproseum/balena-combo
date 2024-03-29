# balenaDash/balenaSense Combo

Deploy multiple applications per device on balenaCloud

## balenaSense DHT11

Take readings from a BME680 or similar sensors on a Raspberry Pi, store with InfluxDB and view with Grafana.
- Updated to add support for DHT11/DHT22 devices.

## balenaDash

Raspberry Pi-powered digital signage or website viewer, remotely accessible from anywhere

![logo](https://raw.githubusercontent.com/dysproseum/balena-combo/master/images/logo.png)

**Starter project that lets anyone start monitoring envrionmental sensor data from a beautiful, remotely accessible dashboard.**

## Highlights

- **Monitor temperature, humidity, and air quality**: Supports a variety of I2C sensors to build your own monitoring system for your environment.
- **Visualize data from one remote dashboard**: Access your customizable environmental data dashboard from anywhere.
- **Compatible with other automation tools**: Integrate balenaSense with home automation tools, such as Home Assistant.

## Setup and configuration

Run balenaSense quickly by deploying it to a balenaCloud application. Log in and deploy the application with just one click by using the button below:

[![](https://balena.io/deploy.svg)](https://dashboard.balena-cloud.com/deploy?repoUrl=https://github.com/dysproseum/balena-combo)

Or add your device to the [balenaSense Open Fleet](https://hub.balena.io/balenalabs/balenasense) to try the project out without a balenaCloud account.

## Documentation 

Head over to our [docs](https://sense.balenalabs.io/docs) for detailed installation and usage instructions, customization options and more!

Or, check out our detailed build guide on the [balena blog](https://www.balena.io/blog/balenasense-v2-updated-temperature-pressure-and-humidity-monitoring-for-raspberry-pi/).

## Motivation

![](https://assets.balena.io/blog-common/2021/07/sensev2.png)

balenaSense is a Raspberry Pi [balenaCloud](https://www.balena.io/cloud/) starter project that takes readings from a supported sensor (such as the Bosch BME680), stores them using InfluxDB and generates a dashboard using Grafana. The Bosch BME680 is recommended as it includes sensors for temperature, humidity, pressure and gas content and is available on a breakout board from a few different places for around $10-$20.

We want to create a project that motivates users to build their own environmental sensor project whether for home or for professional use with privacy and customization in mind.

### What changed?
Version 2 of balenaSense is built using [blocks](https://www.balena.io/blog/introducing-balenablocks-jumpstart-your-iot-app-development/), which are intelligent, drop-in chunks of functionality. This is a major change from earlier versions of balenaSense which used a number of configuration files to tie together the InfluxDB database, Grafana dashboards and sensor readings. Blocks are designed to work together and use auto-discovery (which can be overridden) to pass data amongst themselves.

### How it works
The task of reading data from the sensors is now handled by our new [sensor block](https://github.com/balenablocks/sensor). Instead of installing separate drivers and using custom code for each type of sensor, the sensor block utilizes Industrial IO (IIO) and relies on the variety of sensor drivers already included in the Linux kernel itself. (You can learn more about the sensor block and its use of IIO in [this recent blog post](https://www.balena.io/blog/balenablocks-in-depth-sensor-and-pulse/).) This means balenaSense now supports a wider variety of sensors as well as multiple connected sensors. 

Currently, only I2C sensors that are not mounted on a HAT are supported by the sensor block. This means 1-wire sensors, the Raspberry Pi Sense-HAT, and Pimoroni Enviro+ Air Quality HAT are no longer supported by balenaSense. 

The indoor air quality (IAQ) readings in previous versions of balenaSense were dependent on propriatery software that had recurring breaking changes. On multiple occasions, the entire project was broken while new changes were investigated and merged. In addition, to obtain accurate air quality readings on the BME680, specific burn in procedures are required that balenaSense did not support. For these reasons, air quality readings are no longer a part of balenaSense.

## Contributing

Do you want to help make balenaSense better? Take a look at our [Contributing Guide](contributing). Hope to see you around!

## Getting Help

If you're having any problem, please [raise an issue](https://github.com/balenalabs/balena-sense/issues/new) on GitHub and we will be happy to help. You can also find help on the balenaForums, in a special section [dedicated to balenaSense](https://forums.balena.io/c/project-help/balenasense/86).

## License

balenaSense is free software, and may be redistributed under the terms specified in the [license](https://github.com/balenalabs/balena-sound/blob/master/LICENSE).
