This is a HAP-NodeJS accessory I have developed to allow Nest devices to be used with HomeKit
HomeKit Secure Video is supported on doorbells and/or camera devices

## Supported Devices

The following pre-2019 Nest devices are support with this project

Nest Thermostats
    Gen 1
    Gen 2
    Gen 3
    E
Nest Protects
    Gen 1
    Gen 2
Nest Temp Sensors
Nest Cams
    Cam Indoor/IQ Indoor
    Cam Outdoor/IQ Outdoor
Nest Hello
    Wired Gen 1

The accessory supports connection to Nest using a Nest account OR a Google (migrated Nest account) account.

## Configuration

Nest_config.json is the configuration file where various options can be. An example of a basic configuration is below

```
{
    "RefreshToken" : "<nest session token>",
    "HKSV" : true,
    "H264Encoder" : "copy"
}
```

An advanced configuration example is below

```
{
    "RefreshToken" : "<nest session token>",
    "HKSV" : false,
    "H264Encoder" : "copy",
    "SERIAL1" : {
        "Exclude" : true
    },
    "SERIAL2" : {
        "HKSV" : true,
        "MotionCoolDown" : 2
    },
}
```

The options available are within the configuration file are listed below. Some of these options can also be on specific devices only

| Option           | Values                  | Description                                                                               | Global/Local |
|------------------|-------------------------|-------------------------------------------------------------------------------------------|--------------|
| Refresh Token    |                         | Google account refresh token                                                              | global       |
| Session Token    |                         | Nest session token. Obtain from home.nest.com/session                                     | global       |
| Debug            | true, false             | Turns debugging on or off. Default is off                                                 | global       |
| mDNS             | avahi, bonjour, ciao    | mDNS advertiser library to use. Default is ciao                                           | global       |
| HKSV             | true, false             | Turns HomeKit Secure Video on or off for doorbells and/cameras                            | global/local |
| HKSVPreBuffer    | seconds or milliseconds | Amount of time the pre-buffer for HomeKit Secure Video holds data. Default is 15 seconds  | global/local |
| H264Encoder      | copy, libx264, h264_omx | H264 encoder ffmpeg uses fior streaming and recording. Default is copy                    | global       |
| MotionCooldown   | seconds or milliseconds | Ignore motion detection for this time once triggered. Default is 1 minute                 | global/local |
| PersonCooldown   | seconds or milliseconds | Ignore person detection for this time once triggered (Non HKSV only) Default is 2 minutes | global/local |
| DoorbellCooldown | seconds or milliseconds | Ignore doorbeel button pressed for this time once triggered Default is 1 minute           | global/local |
| Exclude          | true, false             | Exclude a device. Listed by devices serial number                                         | local        |
