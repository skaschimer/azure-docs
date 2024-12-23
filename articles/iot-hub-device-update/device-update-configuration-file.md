---
title: Understand Device Update for Azure IoT Hub Configuration File
description: Understand Device Update for Azure IoT Hub  Configuration File.
author: eshashah-msft
ms.author: eshashah
ms.date: 12/15/2024
ms.topic: concept-article
ms.service: azure-iot-hub
ms.subservice: device-update
---

# Device Update for IoT Hub configuration file

The Device Update agent gets its configuration information from the `du-config.json` file on the device. The agent reads these values and reports them to the Device Update service:

* AzureDeviceUpdateCore:4.ClientMetadata:4.deviceProperties["manufacturer"]
* AzureDeviceUpdateCore:4.ClientMetadata:4.deviceProperties["model"]
* DeviceInformation.manufacturer
* DeviceInformation.model
* additionalProperties
* connectionData
* connectionType

## File location

When installing Debian agent on an IoT Device with a Linux OS, modify the `/etc/adu/du-config.json` file to update values. For a Yocto build system, in the partition or disk called `adu`, create a json file called `/adu/du-config.json`.

## List of fields

| Name |Description |
|-----------|--------------------|
| SchemaVersion | The schema version that maps the current configuration file format version. |
| aduShellTrustedUsers | The list of users that can launch the **adu-shell** program. Note, adu-shell is a broker program that does various update actions as 'root'. The Device Update default content update handlers invoke adu-shell to do tasks that require super user privilege. Examples of tasks that require this privilege are `apt-get install` or executing a privileged script. |
| manufacturer | Reported by the **AzureDeviceUpdateCore:4.ClientMetadata:4** interface to classify the device for targeting the update deployment. |
| model | Reported by the **AzureDeviceUpdateCore:4.ClientMetadata:4** interface to classify the device for targeting the update deployment. |
| iotHubProtocol| Accepted values are `mqtt` or `mqtt/ws` to change the protocol used to connect with IoT hub. Default value is 'mqtt' |
| compatPropertyNames | These properties are used to check for compatibility of the device to target the update deployment. For all the properties specified to be used for compatibility, the values must be in lower case only |
| additionalProperties | Optional field. Additional device reported properties can be set and used for compatibility checking . Limited to five device properties. These properties should be in lower case only. |
| connectionType | Accepted values are `string` or `AIS`. Use `string` when connecting the device to IoT Hub manually for testing purposes. For production scenarios, use `AIS` when using the IoT Identity Service to connect the device to IoT Hub. For more information, see [understand IoT Identity Service configurations](https://azure.github.io/iot-identity-service/configuration.html). |
| connectionData  |If connectionType = "string", add your IoT device's device or module connection string here. If connectionType = "AIS", set the connectionData to empty string (`"connectionData": ""`). |
| manufacturer | Reported by the Device Update agent as part of the **DeviceInformation** interface. |
| model | Reported by the Device Update agent as part of the **DeviceInformation** interface. |
|extensionsFolder| Optional field. This sets path for the ADU Extensions folder. Default path is '/var/lib/adu/extensions'|
|downloadsFolder| Optional field. This sets path for the ADU Downloads folder. Default path is '/var/lib/adu/downloads'|
|aduShellFilePath| Optional field. This sets path for the ADU shell. Default path is '/usr/lib/adu'|
|downloadTimeoutInMinutes| Optional field. This sets download timeout in minutes for update payload. A value of zero means to use the default which is 8 hours.|

'Datafolder' field can be used to set path for the ADU Data folder.CheckDataDir() in the [health management check](https://github.com/Azure/iot-hub-device-update/blob/develop/src/agent/src/health_management.c) needs to be be updated to point to the value in the config file. The default path is '/var/lib/adu' is used otherwise. 

## Example "du-config.json" file contents

```json

{
  "schemaVersion": "1.1",
  "aduShellTrustedUsers": [
    "adu",
    "do"
  ],
  "iotHubProtocol": "mqtt",
  "compatPropertyNames":"manufacturer,model,location,environment" <The property values must be in lower case only>,
  "manufacturer": <Place your device info manufacturer here>,
  "model": <Place your device info model here>,
  "agents": [
    {
      "name": <Place your agent name here>,
      "runas": "adu",
      "connectionSource": {
        "connectionType": "string", //or “AIS”
        "connectionData": <Place your Azure IoT device connection string here>
      },
      "manufacturer": <Place your device property manufacturer here>,
      "model": <Place your device property model here>,
      "additionalDeviceProperties": {
        "location": "usa",
        "environment": "development"
      }
    }
  ]
}

```
