# roon-extension-repository

Repository of (community developed) Roon Extensions

------------

## Introduction

Community developed Roon Extensions can be added to this repository to allow extension distribution via a generic extension installer.

## Format of a repository entry

The backbone behind the distribution is npm. An extension gets an entry in the global extension repository in json format. An entry contains the fields that are shown in the below example:

    {
      "author": "The Appgineer",
      "display_name": "Alarm Clock",
      "description": "Roon Extension to start or stop playback on a specific zone at a specific time",
      "repository": {
        "type": "git",
        "url": "https://github.com/TheAppgineer/roon-extension-alarm-clock.git"
      }
    }

The first three fields are shown to the user by an extension installer, the last one is used to install the extension. Updates can be automatic and do not require an update of the above information.

## Format of a repository category

Version 0.2.0 of the repository layout introduces the concept of categories. A category groups repository entries that have a similar function.

A category is shown in the below example:

    "display_name": "Device Control",
    "extensions": [{
            <entry 1>
        },
        {
            <entry 2>
        }
    }

The display_name specifies the name of the category and the extensions array countains the entries of the category.

### backwards compatibility
To be backwards compatible with the old (0.1.0) layout a category should have an empty repository field:

    "repository": { "url": "" }
