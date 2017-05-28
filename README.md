# roon-extension-repository

Repository of (community developed) Roon Extensions

------------

## Introduction

Community developed Roon Extensions can be added to this repository to allow extension distribution via a generic extension installer.

## Format of a repository entry

The backbone behind the distribution is GitHub. An extension gets an entry in the global extension repository in json format. An entry contains the fields that are shown in the below example:

    {
      "author": "The Appgineer",
      "display_name": "Alarm Clock",
      "description": "Roon Extension to start or stop playback on a specific zone at a specific time",
      "repository": {
        "type": "git",
        "url": "https://github.com/TheAppgineer/roon-extension-alarm-clock.git"
      }
    }

The first three fields are shown to the user by an extension installer, the last one is used to access the git repository of the extension. When the repository is cloned the current version can be read from the 'package.json' file that should be in the root of the repository. Updates can be automatic and do not require an update of the above information.
