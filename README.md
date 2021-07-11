# roon-extension-repository

Repository of (community developed) Roon Extensions

------------

## Introduction

Community developed Roon Extensions can be added to this repository to allow extension distribution via a generic extension installer.

## Format of a repository entry

The backbone behind the distribution is Docker. An extension gets an entry in the global Extension Repository in json format. An entry contains the fields that are shown in the below example:

    {
      "author": "The Appgineer",
      "display_name": "Alarm Clock",
      "description": "Roon Extension to start or stop playback on a specific zone at a specific time",
      "image": {
        ...
      }
    }

The first three fields are shown to the user by an extension installer, the last one is used to install the extension. Updates can be automatic and do not require an update of the above information.

### The "image" entry

The Docker image and the options for container creation are described in the `image` field of the repository entry:

    "image": {
        "repo": "theappgineer/roon-extension-alarm-clock",
        "tags": {
            "amd64": "latest",
            "arm": "latest"
        },
        "binds": [
            "/usr/src/app/config.json"
        ],
        "options": {
            "env": {
                "TZ": "Time Zone"
            },
            "devices": [
                "Device Path"
            ]
        },
        "config": {
            ...
        }
    }

The usage of the subfields is described in the following table:

|Subfield|Description|
|---|---|
|repo|The repository name on Docker Hub, including user name|
|tags|The tag names for the supported architectures|
|binds|File paths within the container that should be created as a bind mount, to keep content in case of image update|
|options.env|Environment variables that should be set by the user at install (container creation) time|
|options.devices|Device paths that should be set by the user at install (container creation) time|
|config|Configuration options directly passed through to Docker for creating the container, see [Docker API documentation](https://docs.docker.com/engine/api/v1.39/#operation/ContainerCreate) for details|

## Format of a repository category

The repository layout uses the concept of categories. A category groups repository entries that have a similar function.

A category is shown in the below example:

    "display_name": "Device Control",
    "extensions": [{
            <entry 1>
        },
        {
            <entry 2>
        }]

The display_name specifies the name of the category and the extensions array contains the entries of the category.
