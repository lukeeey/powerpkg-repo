# Power Package Manager (Repository)
![Status](https://img.shields.io/badge/Status-In_Progress-blue)

This repo serves as the package repository for Power Package Manager (PPKG), a package manager for PowerToys Run plugins.

#### Repo Url
https://repo.powerpkg.dev/repo.json

### Package vs plugin
Throughout the repo you'll see references to both packages and plugins. Here's the difference:
- **Plugin:** A PowerToys Run plugin 
- **Package:** A definition in this repository that defines information about a plugin to be displayed in the Power Package Manager desktop app

### Adding a new package
1. Create a directory `packages/PACKAGEID` where `PACKAGEID` is a sensible alphanumeric name based off your plugin name. The rest of the steps take place in this directory.
2. Create a file `info.json`. Below is a schema for the file:

```json
{
    // This is the same ID that you use in the `plugin.json` for your PowerToys Run Plugin
    "ID": "BX1Z634F30489859A3671B4FQ7Y07193", 
    // Plugin name to be displayed in the PPKG UI
    "Name": "Spotify", 
    // A short summary of your package
    "Description": "Allows you to search Spotify and control its player.", 
    // Your name or username
    "Author": "waaverecords", 
     // The source code URL
    "SourceUrl": "https://github.com/waaverecords/PowerToys-Run-Spotify",
    // OPTIONAL: License information. Don't include if you don't have a license
    "License": { 
        // License type (MIT, GPL, etc). Can be any string value as long as it's the license name.
        "Type": "MIT", 
        // The url to the license file
        "Url": "https://github.com/waaverecords/PowerToys-Run-Spotify/blob/main/LICENSE" 
    },
    // Define versions of your package. Versions MUST be in descending order with the latest version being at the top
    "Versions": { 
        // The keys are supported architectures and values are the download for that architecture. 
        // You must include at least one. 
        // Supported architectures: x64, arm64
        // Supported file types: zip
        "0.82.0": { 
            "x64": "https://github.com/waaverecords/PowerToys-Run-Spotify/releases/download/v0.83.0/PowerToys-Run-Spotify.zip"
        }
    },
    // OPTIONAL: Scripts to be run during install. Allowed values: Install, PostInstall
    "Scripts": {
        // OPTIONAL: Run before install
        "Install": "https://example.com/install.bat",
        // OPTIONA: Run after install
        "PostInstall": "https://example.com/post-install.bat"
    }
}
```
3. Create a `README.md` file. This will be the long description of the package in PPKG desktop app. If you are using the same README from your plugins GitHub repo, a few changes may be required.
  - Don't include content that is not relevant to the average user. For example, you can provide a link to developer documentation or contributing guides, but don't go in depth.
  - Images must reside in a directory called `assets` inside your package directory.
  - Images must be referred to in markdown relatively, so for example `./assets/preview.png`. **This is a MUST as image paths are parsed later on**


### TODO
* Add more packages
* Add older versions (currently only track the current version of a plugin)