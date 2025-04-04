# Salesforce CLI v51 Release Notes

Here are the new and changed features in recent updates of Salesforce CLI and the `salesforcedx` plug-in.

We publish the `latest` plug-in and CLI on Thursdays. At the same time we also publish the `latest-rc` release candidate plug-in and CLI. The release candidates contain changes that will likely be in the final official version.

Run `sfdx version` to display the version of Salesforce CLI installed on your computer. Run `sfdx plugins --core` to display the version of the installed `salesforcedx` plug-in.

Run `sfdx update` to update both the CLI and the `salesforcedx` plug-in to the latest available version.

If you use [autocomplete](https://developer.salesforce.com/docs/atlas.en-us.sfdx_setup.meta/sfdx_setup/sfdx_dev_cli_autocomplete.htm), run `sfdx autocomplete --refresh-cache` after you update the `salesforcedx` plug-in to ensure that autocomplete works correctly on any new commands.

[Click here for the v50 release notes.](./v50.md)

## April 29, 2021

These changes are in the release candidate plug-in (`salesforcedx@latest-rc`). We plan to include these changes in next week's official release. This list isn't final and is subject to change.

* FIX: The `force:org:list` command no longer returns the error `MissingMessageError - Missing message list:noResultsFound for locale en_US` when it doesn't find non-scratch orgs in certain use cases. 

* CHANGE: We [deprecated](https://developer.salesforce.com/docs/atlas.en-us.sfdx_setup.meta/sfdx_setup/sfdx_dev_cli_deprecation.htm) the `force:lightning:lint` command and plan to remove it in v53.0. Use the [esling-plugin-aura](https://github.com/forcedotcom/eslint-plugin-aura) npm package instead. 

## 51.9.1 (April 22, 2021) - CLI 7.98.0

* FIX: Running a Quick Deploy on a package with recently validated components no longer fails. Previously, running the command `force:source:deploy` with the `-q | --validateddeployrequestid` parameter returned the error `Unexpected element {http://soap.sforce.com/2006/04/metadata}id during simple type deserialization`. (GitHub issues [#877](https://github.com/forcedotcom/cli/issues/877) and [#876](https://github.com/forcedotcom/cli/issues/876))

## 51.8.0 (April 15, 2021) - CLI 7.97.0

* FIX: We fixed some under-the-hood bugs.

## 51.7.1 (April 8, 2021) - CLI 7.96.1

Before we describe the changes in this week's release, here's a quick update on open-sourcing Salesforce CLI since we published [this blog post](https://developer.salesforce.com/blogs/2021/02/open-sourcing-salesforce-cli-update-feb-2021.html) in February 2021.

* We've created two new public GitHub repositories and broken out the [force:data](https://github.com/salesforcecli/data) and some of the [force:org](https://github.com/salesforcecli/plugin-org) commands into their own plug-ins.
* At the same time we open-sourced these plug-ins, we also fixed a bunch of GitHub issues. For example, [these issues](https://github.com/forcedotcom/cli/issues?q=is%3Aissue+is%3Aclosed+%22I+think+this+is+fixed+in+the+new+data+plugin%22) were fixed in the new data repository. 

  Check out the [status page](https://github.com/salesforcecli/status) to get a bird’s eye view of the project. 

---
 
* NEW: Get more granular information about the code coverage results of your Apex test runs with the new `--detailedcoverage` parameter of the `force:apex:test:run` command. We've also greatly improved the code coverage results and output of the `force:apex:test:run` and `force:apex:test:report` commands. 
 
    Check out the [Clearer Apex Commands](https://developer.salesforce.com/blogs/2021/04/clearer-apex-commands.html) blog post for more information and a preview of more exciting changes coming soon. Note that the upcoming improvements to the command output might break your existing scripts. 

* CHANGE: We changed the URLs we use to distribute the TAR files for installing Salesforce CLI. Don't worry, the URLs listed in this [manifest](https://developer.salesforce.com/media/salesforce-cli/manifest.json) still work, but starting this week we'll no longer update them to point to the latest releases. If you use these URLs in your CI/CD jobs, update your scripts with the new URLs to ensure you install the latest Salesforce CLI release. 

    This table lists the new unversioned URLs for the TAR files (`.tar.gz` or `.tar.xz`) for each operating system. When we release a new version of Salesforce CLI every week, we also update these URLs so they point to the most up-to-date version. 
    
    | Operating System | TAR Files                |
    |------------------|--------------------------|
    |Linux| [sfdx-linux-x64.tar.gz](https://developer.salesforce.com/media/salesforce-cli/sfdx/channels/stable/sfdx-linux-x64.tar.gz)|
    ||[sfdx-linux-x64.tar.xz](https://developer.salesforce.com/media/salesforce-cli/sfdx/channels/stable/sfdx-linux-x64.tar.xz)|
    ||[sfdx-linux-arm.tar.gz](https://developer.salesforce.com/media/salesforce-cli/sfdx/channels/stable/sfdx-linux-arm.tar.gz)|
    ||[sfdx-linux-arm.tar.xz](https://developer.salesforce.com/media/salesforce-cli/sfdx/channels/stable/sfdx-linux-arm.tar.xz)|
    |macOS|[sfdx-darwin-x64.tar.gz](https://developer.salesforce.com/media/salesforce-cli/sfdx/channels/stable/sfdx-darwin-x64.tar.gz)|
    ||[sfdx-darwin-x64.tar.xz](https://developer.salesforce.com/media/salesforce-cli/sfdx/channels/stable/sfdx-darwin-x64.tar.xz)|
    |Windows*|[sfdx-win32-x64.tar.gz](https://developer.salesforce.com/media/salesforce-cli/sfdx/channels/stable/sfdx-win32-x64.tar.gz)|
    | |[sfdx-win32-x64.tar.xz](https://developer.salesforce.com/media/salesforce-cli/sfdx/channels/stable/sfdx-win32-x64.tar.xz)|
    | |[sfdx-win32-x86.tar.gz](https://developer.salesforce.com/media/salesforce-cli/sfdx/channels/stable/sfdx-win32-x86.tar.gz)|
    ||[sfdx-win32-x86.tar.xz](https://developer.salesforce.com/media/salesforce-cli/sfdx/channels/stable/sfdx-win32-x86.tar.xz)|

    * WINDOWS NOTE: Installing Salesforce CLI with a TAR file on Windows requires a separate program, such as 7Zip, to extract the contents. We highly recommend you use the [Windows installers](https://developer.salesforce.com/tools/sfdxcli).

    We also removed the `install` script from the new TAR files. The existing TAR files listed in this [manifest](https://developer.salesforce.com/media/salesforce-cli/manifest.json) still contain the `install` script. You had to have administrator privileges to run the script, and it wasn’t necessary to install Salesforce CLI anyway. We now recommend that you simply unpack the TAR file into a directory of your choice and update your PATH environment variable appropriately. 

    We’ll update the [documentation](https://developer.salesforce.com/docs/atlas.en-us.sfdx_setup.meta/sfdx_setup/sfdx_setup_install_cli.htm#sfdx_setup_install_cli_linux) soon. 

* CHANGE: We've rolled back the change we announced on [February 22, 2021](./README.md#new-parameters) where some commands (`force:org:create`, `force:source:*`, and `force:mdapi:*`) use REST API by default when deploying source. These commands use SOAP API by default again. 

    If you want to use REST for deployment, set the `restDeploy` config value or `SFDX_REST_DEPLOY` environment variable to `true`. For example, to set it globally with the config variable:

	`$ sfdx config:set restDeploy=true --global`

    To set it for just your project, don’t use the `--global` flag. We’ll update the [documentation](https://developer.salesforce.com/docs/atlas.en-us.sfdx_setup.meta/sfdx_setup/sfdx_dev_cli_config_values.htm) soon.

## 51.6.0 (April 1, 2021) - CLI 7.94.3

* NEW: Get a list of files in your project that the `force:source:*` commands ignore with the new `force:source:ignored:list` command. The command refers to the `.forceignore` file to determine the list of ignored files. Run the command without any parameters to get a list of all the files in all package directories that are ignored. Use the `--sourcepath` parameter to limit the check to a specific file or directory. If you specify a directory, the command checks all subdirectories recursively. For example, run this command to check if a particular file is ignored:

    `sfdx force:source:ignored:list --sourcepath=package.xml`

    Run this command to get a list of all ignored files in a specific directory:
	
    `sfdx force:source:ignored:list --sourcepath=force-app/main/default`
    
* NEW: Here at Salesforce, we love metadata! We're always looking for ways to improve moving it between orgs. And we feel like we haven't provided you with enough ways to deploy and retrieve it. So we're excited to introduce these new commands that provide true flexibility and power to your workflows:
  * `force:tooling:deploy|retrieve`
  * `force:source:transfer`
  * `force:mdapi:stash:push|pop`
  * `force:code:shove|wrest`

  Enjoy! 

## 51.5.0 (March 25, 2021) - CLI 7.93.1

* FIX: The `auth:sfdxurl:store` command executes correctly when you specify a `.json` file to the `---sfdxurlfile` parameter. We also improved the command so that you can pass it the `.json` output of the `force:org:display` command. For example:

	```bash
    sfdx force:org:display -u <DevHub> --verbose --json > authFile.json
	sfdx auth:sfdxurl:store --sfdxurlfile authFile.json
    ```
* CHANGE: We've removed the `force:project:upgrade` command after deprecating it in v50. 

## 51.4.0 (March 18, 2021) - CLI 7.92.0

* NEW:  Use the `--setuniqueusername` flag of `force:user:create` to force the newly created username, if specified in the definition file or at the command line, to be unique by appending the org ID. This feature is particularly useful in CI scripts that run multiple times.

    For example, let’s say your user definition file contains a `Username` attribute:

    ```bash
    {
        "Username": "tester@sfdx.org",
        "LastName": "Hobbs",
        ...
    }
    ```

    The username `tester@sfdx.org` must be unique across the entire Salesforce ecosystem; otherwise, the `force:user:create` command fails. But if you use the same user definition file for each CI run, the command definitely fails on the second run. To ensure success, specify the `--setuniqueusername` parameter so that the resulting username looks something like `tester@sfdx.org.00D123456123456123`. Because org IDs are always unique, the username is also always unique.  

    Thank you, Fabien Taillon, for submitting this [new feature request](https://github.com/salesforcecli/plugin-user/pull/50) and then writing most of the code. You're our first community member to contribute a feature that we then merged into our code and released. We're thrilled with your elegant solution to a real-world problem and hope to see many more contributions from you and the community. 

As part of [open-sourcing Salesforce CLI](https://developer.salesforce.com/blogs/2021/02/open-sourcing-salesforce-cli-update-feb-2021.html), we've broken out the source for some of the org commands (`force:org:open|list|display`) into their own [GitHub repo](https://github.com/salesforcecli/plugin-org). These commands are still in the `force` namespace and bundled in the `salesforcedx` plug-in, and they work the same as before.  

We don't normally announce when we open-source commands that remain in the `force` namespace. But because we made so many exciting changes this release, we thought we'd give you a few details. 

  * NEW: The `force:org:display` command displays the scratch org’s namespace. Many thanks to Todd Halfpenny for requesting this new feature. (GitHub issue [#422](https://github.com/forcedotcom/cli/issues/422))

  * CHANGE: Starting in version 52.0 of Salesforce CLI, the `--json` output of the `force:org:list` command no longer returns the property `connectedStatus` for scratch orgs. The `force:org:list` command displays a warning about this upcoming change, but be sure to update your CI/CD scripts now if they currently use this property.

  * FIX: GitHub issues [#361](https://github.com/forcedotcom/cli/issues/361), [#456](https://github.com/forcedotcom/cli/issues/456), [#482](https://github.com/forcedotcom/cli/issues/482), [#637](https://github.com/forcedotcom/cli/issues/637), [#666](https://github.com/forcedotcom/cli/issues/666), [#719](https://github.com/forcedotcom/cli/issues/719), [#724](https://github.com/forcedotcom/cli/issues/724) 


## 51.3.0 (March 11, 2021) - CLI 7.91.0

* FIX: The `force:mdapi:deploy --runtests` command now runs the specified tests.
* FIX: When you run the `force:mdapi:deploy` command with the `--json` parameter and the command fails, it returns the exit code 1. Previously it returned 0.


## 51.2.2 (March 4, 2021) - CLI 7.90.2

* CHANGE: As of v51, all `force:source` and `force:mdapi` commands use REST API by default to deploy. Previously they used SOAP API by default. Set the `restDeploy` config value or `SFDX_REST_DEPLOY` environment variable to false to switch back to SOAP. (GitHub Issues [#860](https://github.com/forcedotcom/cli/issues/860), [#870](https://github.com/forcedotcom/cli/issues/870), [#872](https://github.com/forcedotcom/cli/issues/872), [#884](https://github.com/forcedotcom/cli/issues/884))
* FIX: You no longer get the error FILE HAS NO CONTENT when you run any command after authenticating to an org with the `auth:jwt:grant` command. (GitHub Issue [#867](https://github.com/forcedotcom/cli/issues/867))
* FIX: The force:user:password:generate and force:user:create commands generate valid passwords. (GitHub Issue [#858](https://github.com/forcedotcom/cli/issues/858))
* FIX: The force:project:create command now generates a scratch org definition file with EnableSetPasswordInApi as a scratch org feature rather than a security setting. This change is a result of the field [Settings.securitySettings.passwordPolicies.enableSetPasswordInApi](https://help.salesforce.com/articleView?id=release-notes.rn_api_meta.htm&type=5&release=230) being removed in version 51.0 of the Metadata API.
* FIX: When authorizing an org with `auth:web:login`, the browser no longer hangs after allowing access. (GitHub Issue [#890](https://github.com/forcedotcom/cli/issues/890))

## 51.1.1 (February 25, 2021) - CLI 7.89.2

* FIX: The command `force:user:create` properly authenticates to a connected app authenticated with Web Flow login.

## 51.0.4 (February 22, 2021) - CLI 7.88.4

Welcome to the first release of version 51 of the `salesforcedx` CLI plug-in in Spring '21.

### Installation Notes

Update Salesforce CLI to v51 by running `sfdx update`.

```bash
$ sfdx update
```

If you are installing Salesforce CLI for the first time, see [Install Salesforce CLI](https://developer.salesforce.com/docs/atlas.en-us.sfdx_setup.meta/sfdx_setup/sfdx_setup_install_cli.htm#sfdx_setup_install_cli) to install the CLI for your operating system, then run `sfdx update`.

Run `sfdx plugins --core` to display the version of Salesforce CLI and the installed `salesforcedx` plug-in.

```bash
$ sfdx plugins --core

@oclif/plugin-autocomplete 0.3.0 (core)
@oclif/plugin-commands 1.3.0 (core)
@oclif/plugin-help 3.2.2 (core)
@oclif/plugin-not-found 1.2.4 (core)
@oclif/plugin-plugins 1.9.5 (core)
@oclif/plugin-update 1.4.0-2 (core)
@oclif/plugin-warn-if-update-available 1.7.0 (core)
@oclif/plugin-which 1.0.3 (core)
@salesforce/sfdx-trust 3.6.0 (core)
alias 1.1.5 (core)
auth 1.4.8 (core)
config 1.2.4 (core)
generator 1.1.5 (core)
salesforcedx 51.0.2 (core)                    // salesforcedx plug-in version
├─ limits 1.0.3 (core)
├─ user 1.1.0 (core)
├─ schema 1.0.3 (core)
├─ apex 0.1.4 (core)
├─ templates 51.1.0 (core)
├─ custom-metadata 1.0.11 (core)
├─ @salesforce/sfdx-plugin-lwc-test 0.1.7 (core)
└─ salesforce-alm 51.0.1 (core)
sfdx-cli 7.88.3 (core)                        // Salesforce CLI version
telemetry 1.1.1 (core)
```

### Uninstall the Pre-Release Version of the salesforcedx CLI Plug-In

If you installed the pre-release version of the `salesforcedx` plug-in, uninstall it and update the CLI. We’re no longer updating the pre-release and will be removing the tag.

```bash
$ sfdx plugins:uninstall salesforcedx
$ sfdx update
```

### The Salesforce CLI platform installers now install nodejs v14 LTS
The platform installers for Salesforce CLI (Windows, Linux and Mac OS X) now install nodejs v14 LTS.

### Salesforce CLI has dropped support for nodejs v8
Nodejs v8 has reached end-of-life and is no longer maintained. Salesforce CLI supports nodejs engine v10 or greater.

### New Commands

No new commands have been added in release v51.

### Removed Commands

These commands were removed in v51. The ISV Hammer test closed pilot program has been terminated.

* `force:package:hammertest:list`
* `force:package:hammertest:report`
* `force:package:hammertest:run`

### New Parameters

* `force:mdapi:deploy --soapdeploy`

  The `--soapdeploy` parameter causes the metadata deploy to use the SOAP API. Starting in v51, the `force:mdapi:deploy` command uses REST by default; previously it used SOAP. All other commands continue to use SOAP by default.

* `force:package:create --orgdependent`

  For unlocked packages only, allows the package to depend on unpackaged metadata in the installation org. This parameter is now GA; it was Beta in v50.

### Removed Parameters

* `force:org:shape:create --definitionfile`

  The `definitionfile` parameter has been removed from this command. This parameter is part of the org shape feature which is currently in beta. We removed the parameter based on feedback from users that they preferred storing the org shape in the shape source org rather than in a scratch definition file.

### Second-Generation Managed Packaging

* The `force:pacakge:version:report --verbose` command displays the release version stamped on a package version.

* We've enhanced the package version CLI commands to support component deletion.
  * If `force:package:version:create` completes successfully, and metadata has been removed from the package version as compared to its ancestor, the command displays a generic warning message about the removed metadata.
  * The command `force:package:version:list --verbose` displays whether metadata was removed.
  * The command `force:package:version:report` displays whether metadata was removed.
  * The command `force:package:version:promote` displays a warning if components have been removed from the version being promoted and `--noprompt` isn't specified.
  * The `--orgdependent` parameter of `force:package:create` is GA. The parameter was beta in v50."

### Other Changes

* FIX: We've improved the error message returned when you run `force:user:password:generate` using API version 51.0 and EnableSetPasswordInApi is configured as a security setting in your scratch org definition file. EnableSetPasswordInApi is now a scratch org feature instead of a Metadata API setting. Here's an example of configuring it as a feature in your scratch org definition file:

  `"features": ["EnableSetPasswordInApi","MultiCurrency"],`

  This change is a result of the field `Settings.securitySettings.passwordPolicies.enableSetPasswordInApi` being [removed in version 51.0 of the Metadata API](https://help.salesforce.com/articleView?id=release-notes.rn_api_meta.htm&type=5&release=230).  (GitHub issue [#798](https://github.com/forcedotcom/cli/issues/798))

* FIX: The command `force:user:password:generate` no longer fails when generating a password for a user that doesn't have access to the Profile standard object.

* FIX: The output of `force:user:create --json` now matches the output from previous versions.

* FIX: The command `force:source:deploy` no longer fails with "The org cannot be found" after a successful login.

* FIX: The command `force:user:password:generate` no longer fails when generating a password for a user that doesn't have access to the Profile standard object.
