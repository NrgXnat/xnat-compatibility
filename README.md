# XNAT Compatibility Matrix

The purpose of this repo is to create a maintable compatibility matrix for versions of XNAT to correspond to versions of XNAT Plugins. This would allow for plugins to live in any repository, as long as we can provide a filepath to download a tagged version of the plugin. 

## Usage

The revised XNAT Downloads page populates its list of plugins from a master JSON file located within the [xnat-org repo](https://github.com/xnatworks/xnat-org). This file (`/_js/packages-os-plugins.json`) contains a set of plugin identifiers, which match the GitHub repo identifiers for each plugin repo. It also contains descriptive text and links. 

The Downloads page then reaches out to this repository to match plugin versions with a selected XNAT version. A query for all plugins that are supported by XNAT 1.10.0, for example, is listed in this repository in the `xnat-1.10.0-os-plugins.json` file. That listing simply contains a key-value pair matching the plugin identifier with the *latest supported version* of that plugin for that version of XNAT. For example:

```declarative
{
  "versions": {
    "batch-launch-plugin": "0.9.0",
    "container-service": "3.8.1",
    "dicom-query-retrieve": "3.0.0",
    "dist-events": "2.0.0",
    "ldap-auth-plugin": "1.3.0",
    "mfa-plugin": "1.5.0",
    "openid-auth-plugin": "1.5.0",
    "ohif-viewer-xnat-plugin": "3.8.0",
    "pipeline-engine-plugin": "1.2.0",
    "pixi-plugin": "v1.5.0",
    "xnat-jupyterhub-plugin": "v1.3.4",
    "xsync": "1.8.1"
  }
}
```

**Important**: Each plugin version specified in these JSON files should correspond EXACTLY with a GitHub release tagged with that version number in the plugin's repository. This includes differences in naming conventions as necessary (i.e. "v1.5.0" for the PIXI plugin rather than "1.5.0"). 

## Updating

Any new XNAT version release or plugin release should also trigger an update to this repository, updating existing lists and adding new files. Also, XNAT open source developers can add backdated support for older versions of XNAT, making the Downloads page that much more usable. 