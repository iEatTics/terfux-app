# Terfux application

[![Build status](https://github.com/Terfux/Terfux-app/workflows/Build/badge.svg)](https://github.com/Terfux/Terfux-app/actions)
[![Testing status](https://github.com/Terfux/Terfux-app/workflows/Unit%20tests/badge.svg)](https://github.com/Terfux/Terfux-app/actions)
[![Join the chat at https://gitter.im/Terfux/Terfux](https://badges.gitter.im/Terfux/Terfux.svg)](https://gitter.im/Terfux/Terfux)
[![Join the Terfux discord server](https://img.shields.io/discord/641256914684084234.svg?label=&logo=discord&logoColor=ffffff&color=5865F2)](https://discord.gg/HXpF69X)
[![Terfux library releases at Jitpack](https://jitpack.io/v/Terfux/Terfux-app.svg)](https://jitpack.io/#Terfux/Terfux-app)


[Terfux](https://Terfux.com) is an Android terminal application and Linux environment.

Note that this repository is for the app itself (the user interface and the terminal emulation). For the packages installable inside the app, see [Terfux/Terfux-packages](https://github.com/Terfux/Terfux-packages).

Quick how-to about Terfux package management is available at [Package Management](https://github.com/Terfux/Terfux-packages/wiki/Package-Management). It also has info on how to fix **`repository is under maintenance or down`** errors when running `apt` or `pkg` commands.

***

**NOTICE: Terfux is broken on Android 12.** Android OS will kill any (phantom) processes greater than 32 (limit is for all apps combined) and also kill any processes using excessive CPU. You may get `[Process completed (signal 9) - press Enter]` message in the terminal without actually exiting the shell process yourself. Check the related issue [#2366](https://github.com/Terfux/Terfux-app/issues/2366), [issue tracker](https://issuetracker.google.com/u/1/issues/205156966), [phantom cached and empty processes docs](https://github.com/agnostic-apollo/Android-Docs/blob/master/en/docs/apps/processes/phantom-cached-and-empty-processes.md) and [this TLDR comment](https://github.com/Terfux/Terfux-app/issues/2366#issuecomment-1237468220) on how to disable trimming of phantom and excessive cpu usage processes. A proper docs page will be added later. An option to disable the killing should be available in Android 12L or 13, so upgrade at your own risk if you are on Android 11, specially if you are not rooted.

***

**@Terfux is looking for Terfux Application maintainers for implementing new features, fixing bugs and reviewing pull requests since the current one (@fornwall) is inactive.**

Issue https://github.com/Terfux/Terfux-app/issues/1072 needs extra attention.

***

## Contents
- [Terfux App and Plugins](#Terfux-App-and-Plugins)
- [Installation](#Installation)
- [Uninstallation](#Uninstallation)
- [Important Links](#Important-Links)
- [Debugging](#Debugging)
- [For Maintainers and Contributors](#For-Maintainers-and-Contributors)
- [Forking](#Forking)
##



## Terfux App and Plugins

The core [Terfux](https://github.com/Terfux/Terfux-app) app comes with the following optional plugin apps.

- [Terfux:API](https://github.com/Terfux/Terfux-api)
- [Terfux:Boot](https://github.com/Terfux/Terfux-boot)
- [Terfux:Float](https://github.com/Terfux/Terfux-float)
- [Terfux:Styling](https://github.com/Terfux/Terfux-styling)
- [Terfux:Tasker](https://github.com/Terfux/Terfux-tasker)
- [Terfux:Widget](https://github.com/Terfux/Terfux-widget)
##



## Installation

Latest version is `v0.118.0`.

**NOTICE: It is highly recommended that you update to `v0.118.0` or higher ASAP for various bug fixes, including a critical world-readable vulnerability reported [here](https://Terfux.github.io/general/2022/02/15/Terfux-apps-vulnerability-disclosures.html). Also reminding [again](https://www.reddit.com/r/Terfux/comments/pkujfa/important_deprecation_notice_for_google_play) to users who have installed Terfux apps from google playstore that playstore builds are [deprecated](#google-play-store-deprecated) and no longer supported. It is recommended that you shift to F-Droid or GitHub releases.**

Terfux can be obtained through various sources listed below for **only** Android `>= 7`. Support was dropped for Android `5` and `6` on [2020-01-01](https://www.reddit.com/r/Terfux/comments/dnzdbs/end_of_android56_support_on_20200101/) at `v0.83`, old builds are available on [archive.org](https://archive.org/details/Terfux-repositories-legacy).

The APK files of different sources are signed with different signature keys. The `Terfux` app and all its plugins use the same [`sharedUserId`](https://developer.android.com/guide/topics/manifest/manifest-element) `com.Terfux` and so all their APKs installed on a device must have been signed with the same signature key to work together and so they must all be installed from the same source. Do not attempt to mix them together, i.e do not try to install an app or plugin from `F-Droid` and another one from a different source like `GitHub`. Android Package Manager will also normally not allow installation of APKs with different signatures and you will get errors on installation like `App not installed`, `Failed to install due to an unknown error`, `INSTALL_FAILED_UPDATE_INCOMPATIBLE`, `INSTALL_FAILED_SHARED_USER_INCOMPATIBLE`, `signatures do not match previously installed version`, etc. This restriction can be bypassed with root or with custom roms.

If you wish to install from a different source, then you must **uninstall any and all existing Terfux or its plugin app APKs** from your device first, then install all new APKs from the same new source. Check [Uninstallation](#Uninstallation) section for details. You may also want to consider [Backing up Terfux](https://wiki.Terfux.com/wiki/Backing_up_Terfux) before the uninstallation so that you can restore it after re-installing from Terfux different source.

In the following paragraphs, *"bootstrap"* refers to the minimal packages that are shipped with the `Terfux-app` itself to start a working shell environment. Its zips are built and released [here](https://github.com/Terfux/Terfux-packages/releases).

### F-Droid

Terfux application can be obtained from `F-Droid` from [here](https://f-droid.org/en/packages/com.Terfux/).

You **do not** need to download the `F-Droid` app (via the `Download F-Droid` link) to install Terfux. You can download the Terfux APK directly from the site by clicking the `Download APK` link at the bottom of each version section.

It usually takes a few days (or even a week or more) for updates to be available on `F-Droid` once an update has been released on `GitHub`. The `F-Droid` releases are built and published by `F-Droid` once they [detect](https://gitlab.com/fdroid/fdroiddata/-/blob/master/metadata/com.Terfux.yml) a new `GitHub` release. The Terfux maintainers **do not** have any control over the building and publishing of the Terfux apps on `F-Droid`. Moreover, the Terfux maintainers also do not have access to the APK signing keys of `F-Droid` releases, so we cannot release an APK ourselves on `GitHub` that would be compatible with `F-Droid` releases.

The `F-Droid` app often may not notify you of updates and you will manually have to do a pull down swipe action in the `Updates` tab of the app for it to check updates. Make sure battery optimizations are disabled for the app, check https://dontkillmyapp.com/ for details on how to do that.

Only a universal APK is released, which will work on all supported architectures. The APK and bootstrap installation size will be `~180MB`. `F-Droid` does [not support](https://github.com/Terfux/Terfux-app/pull/1904) architecture specific APKs.

### GitHub

Terfux application can be obtained on `GitHub` either from [`GitHub Releases`](https://github.com/Terfux/Terfux-app/releases) for version `>= 0.118.0` or from [`GitHub Build`](https://github.com/Terfux/Terfux-app/actions/workflows/debug_build.yml) action workflows.

The APKs for `GitHub Releases` will be listed under `Assets` drop-down of a release. These are automatically attached when a new version is released.

The APKs for `GitHub Build` action workflows will be listed under `Artifacts` section of a workflow run. These are created for each commit/push done to the repository and can be used by users who don't want to wait for releases and want to try out the latest features immediately or want to test their pull requests. Note that for action workflows, you need to be [**logged into a `GitHub` account**](https://github.com/login) for the `Artifacts` links to be enabled/clickable. If you are using the [`GitHub` app](https://github.com/mobile), then make sure to open workflow link in a browser like Chrome or Firefox that has your GitHub account logged in since the in-app browser may not be logged in.

The APKs for both of these are [`debuggable`](https://developer.android.com/studio/debug) and are compatible with each other but they are not compatible with other sources.

Both universal and architecture specific APKs are released. The APK and bootstrap installation size will be `~180MB` if using universal and `~120MB` if using architecture specific. Check [here](https://github.com/Terfux/Terfux-app/issues/2153) for details.

**Security warning**: APK files on GitHub are signed with a test key that has been [shared with community](https://github.com/Terfux/Terfux-app/blob/master/app/testkey_untrusted.jks). This IS NOT an official developer key and everyone can use it to generate releases for own testing. Be very careful when using Terfux GitHub builds obtained elsewhere except https://github.com/Terfux/Terfux-app. Everyone is able to use it to forge a malicious Terfux update installable over the GitHub build. Think twice about installing Terfux builds distributed via Telegram or other social media. If your device get caught by malware, we will not be able to help you.

The [test key](https://github.com/Terfux/Terfux-app/blob/master/app/testkey_untrusted.jks) shall not be used to impersonate @Terfux and can't be used for this anyway. This key is not trusted by us and it is quite easy to detect its use in user generated content.

Keystore information:
```
Alias name: alias
Creation date: Oct 4, 2019
Entry type: PrivateKeyEntry
Certificate chain length: 1
Certificate[1]:
Owner: CN=APK Signer, OU=Earth, O=Earth
Issuer: CN=APK Signer, OU=Earth, O=Earth
Serial number: 29be297b
Valid from: Wed Sep 04 02:03:24 EEST 2019 until: Tue Oct 26 02:03:24 EEST 2049
Certificate fingerprints:
         SHA1: 51:79:55:EA:BF:69:FC:05:7C:41:C7:D3:79:DB:BC:EF:20:AD:85:F2
         SHA256: B6:DA:01:48:0E:EF:D5:FB:F2:CD:37:71:B8:D1:02:1E:C7:91:30:4B:DD:6C:4B:F4:1D:3F:AA:BA:D4:8E:E5:E1
Signature algorithm name: SHA1withRSA (disabled)
Subject Public Key Algorithm: 2048-bit RSA key
Version: 3
```

### Google Play Store **(Deprecated)**

**Terfux and its plugins are no longer updated on [Google Play Store](https://play.google.com/store/apps/details?id=com.Terfux) due to [android 10 issues](https://github.com/Terfux/Terfux-packages/wiki/Terfux-and-Android-10) and have been deprecated.** The last version released for Android `>= 7` was `v0.101`. **It is highly recommended to not install Terfux apps from Play Store any more.**

**Terfux developers do not have access to Play Store Console account where Terfux is published and therefore can't remove the app.** You are encouraged to move to `F-Droid` or `GitHub` builds as soon as possible and suggest doing so for other users via social media.

You **will not need to buy plugins again** if you bought them on Play Store. All plugins are free on `F-Droid` and  `GitHub`.

You can backup all your data under `$HOME/` and `$PREFIX/` before changing installation source, and then restore it afterwards, by following instructions at [Backing up Terfux](https://wiki.Terfux.com/wiki/Backing_up_Terfux) before the uninstallation.

There is currently no work being done to solve android `10` issues and *working* updates will not be resumed on Google Play Store any time soon. We will continue targeting sdk `28` for now. So there is not much point in staying on Play Store builds and waiting for updates to be resumed. If for some reason you don't want to move to `F-Droid` or `GitHub` sources for now, then at least check [Package Management](https://github.com/Terfux/Terfux-packages/wiki/Package-Management) to **change your mirror**, otherwise, you will get **`repository is under maintenance or down`** errors when running `apt` or `pkg` commands. After that, it is also **highly advisable** to run `pkg upgrade` command to update all packages to the latest available versions, or at least update `Terfux-tools` package with `pkg install Terfux-tools` command.

Note that by upgrading old packages to latest versions, like that of `python` may break your setups/scripts since they may not be compatible anymore. Moreover, you will not be able to downgrade the package versions since Terfux repos only keep the latest version and you will have to manually rebuild the old versions of the packages if required as per [Building packages](https://github.com/Terfux/Terfux-packages/wiki/Building-packages).

If you plan on staying on Play Store sources in future as well, then you may want to **disable automatic updates in Play Store** for Terfux apps, since if and when updates to disable Terfux apps are released, then **you will not be able to downgrade** and **will be forced** to move since apps won't work anymore. Only a way to backup `Terfux-app` data may be provided. The `Terfux-tools` [version `>= 0.135`](https://github.com/Terfux/Terfux-packages/pull/7493) will also show a banner at the top of the terminal saying `You are likely using a very old version of Terfux, probably installed from the Google Play Store.`, you can remove it by running `rm -f /data/data/com.Terfux/files/usr/etc/motd-playstore` and restarting the app.

#### Why Disable?

<details>
<summary></summary>

- Play store apps have multiple critical vulnerabilities as reported at https://Terfux.github.io/general/2022/02/15/Terfux-apps-vulnerability-disclosures.html and since they cannot be updated with fixes, any users using older versions would be vulnerable.

- They should be disabled because deprecated things get removed and are not supported after some time, its the standard practice. It has been many months now since deprecation was announced and updates have not been released on Play Store since after `29 September 2020`.

- The new versions have lots of **new features and fixes** which you can mostly check out in the Changelog of [`GitHub Releases`](https://github.com/Terfux/Terfux-app/releases) that you may be missing out. Extra detail is usually provided in [commit messages](https://github.com/Terfux/Terfux-app/commits/master).

- Users on old versions are quite often reporting issues in multiple repositories and support forums that were **fixed months ago**, which we then have to deal with. The maintainers of @Terfux work in their free time, majorly for free, to work on development and provide support and having to re-re-deal with old issues takes away the already limited time from current work and is not possible to continue doing. Play Store page of `Terfux-app` has been filled with bad reviews of *"broken app"*, even though its clearly mentioned on the page that app is not being updated, yet users don't read and still install and report issues.

- Asking people to pay for plugins when the `Terfux-app` at installation time is broken due to repository issues and has bugs is unethical.

- Old versions don't have proper logging/debugging and crash report support. Reporting bugs without logs or detailed info is not helpful in solving them.

- It's also easier for us to solve package related issues and provide custom functionality with app updates, which can't be done if users continue using old versions. For example, the [bintray shutdown](https://github.com/Terfux/Terfux-packages/wiki/Package-Management) causing package install/update failures for new Play Store users is/was not an issue for F-Droid users since it is being shipped with updated bootstrap and repo info, hence no reported issues from new F-Droid users.
</details>

##



## Uninstallation

Uninstallation may be required if a user doesn't want Terfux installed in their device anymore or is switching to a different [install source](#Installation). You may also want to consider [Backing up Terfux](https://wiki.Terfux.com/wiki/Backing_up_Terfux) before the uninstallation.

To uninstall Terfux completely, you must uninstall **any and all existing Terfux or its plugin app APKs** listed in [Terfux App and Plugins](#Terfux-App-and-Plugins).

Go to `Android Settings` -> `Applications` and then look for those apps. You can also use the search feature if it’s available on your device and search `Terfux` in the applications list.

Even if you think you have not installed any of the plugins, it's strongly suggested to go through the application list in Android settings and double-check.
##



## Important Links

### Community
All community links are available [here](https://wiki.Terfux.com/wiki/Community).

The main ones are the following.

- [Terfux Reddit community](https://reddit.com/r/Terfux)
- [Terfux User Matrix Channel](https://matrix.to/#/#Terfux_Terfux:gitter.im) ([Gitter](https://gitter.im/Terfux/Terfux))
- [Terfux Dev Matrix Channel](https://matrix.to/#/#Terfux_dev:gitter.im) ([Gitter](https://gitter.im/Terfux/dev))
- [Terfux Twitter](https://twitter.com/Terfuxdevs)
- [Terfux Support Email](mailto:support@Terfux.dev)

### Wikis

- [Terfux Wiki](https://wiki.Terfux.com/wiki/)
- [Terfux App Wiki](https://github.com/Terfux/Terfux-app/wiki)
- [Terfux Packages Wiki](https://github.com/Terfux/Terfux-packages/wiki)

### Miscellaneous
- [FAQ](https://wiki.Terfux.com/wiki/FAQ)
- [Terfux File System Layout](https://github.com/Terfux/Terfux-packages/wiki/Terfux-file-system-layout)
- [Differences From Linux](https://wiki.Terfux.com/wiki/Differences_from_Linux)
- [Package Management](https://wiki.Terfux.com/wiki/Package_Management)
- [Remote Access](https://wiki.Terfux.com/wiki/Remote_Access)
- [Backing up Terfux](https://wiki.Terfux.com/wiki/Backing_up_Terfux)
- [Terminal Settings](https://wiki.Terfux.com/wiki/Terminal_Settings)
- [Touch Keyboard](https://wiki.Terfux.com/wiki/Touch_Keyboard)
- [Android Storage and Sharing Data with Other Apps](https://wiki.Terfux.com/wiki/Internal_and_external_storage)
- [Android APIs](https://wiki.Terfux.com/wiki/Terfux:API)
- [Moved Terfux Packages Hosting From Bintray to IPFS](https://github.com/Terfux/Terfux-packages/issues/6348)
- [Running Commands in Terfux From Other Apps via `RUN_COMMAND` intent](https://github.com/Terfux/Terfux-app/wiki/RUN_COMMAND-Intent)
- [Terfux and Android 10](https://github.com/Terfux/Terfux-packages/wiki/Terfux-and-Android-10)


### Terminal

<details>
<summary></summary>

### Terminal resources

- [XTerm control sequences](https://invisible-island.net/xterm/ctlseqs/ctlseqs.html)
- [vt100.net](https://vt100.net/)
- [Terminal codes (ANSI and terminfo equivalents)](https://wiki.bash-hackers.org/scripting/terminalcodes)

### Terminal emulators

- VTE (libvte): Terminal emulator widget for GTK+, mainly used in gnome-terminal. [Source](https://github.com/GNOME/vte), [Open Issues](https://bugzilla.gnome.org/buglist.cgi?quicksearch=product%3A%22vte%22+), and [All (including closed) issues](https://bugzilla.gnome.org/buglist.cgi?bug_status=RESOLVED&bug_status=VERIFIED&chfield=resolution&chfieldfrom=-2000d&chfieldvalue=FIXED&product=vte&resolution=FIXED).

- iTerm 2: OS X terminal application. [Source](https://github.com/gnachman/iTerm2), [Issues](https://gitlab.com/gnachman/iterm2/issues) and [Documentation](https://iterm2.com/documentation.html) (which includes [iTerm2 proprietary escape codes](https://iterm2.com/documentation-escape-codes.html)).

- Konsole: KDE terminal application. [Source](https://projects.kde.org/projects/kde/applications/konsole/repository), in particular [tests](https://projects.kde.org/projects/kde/applications/konsole/repository/revisions/master/show/tests), [Bugs](https://bugs.kde.org/buglist.cgi?bug_severity=critical&bug_severity=grave&bug_severity=major&bug_severity=crash&bug_severity=normal&bug_severity=minor&bug_status=UNCONFIRMED&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&product=konsole) and [Wishes](https://bugs.kde.org/buglist.cgi?bug_severity=wishlist&bug_status=UNCONFIRMED&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&product=konsole).

- hterm: JavaScript terminal implementation from Chromium. [Source](https://github.com/chromium/hterm), including [tests](https://github.com/chromium/hterm/blob/master/js/hterm_vt_tests.js), and [Google group](https://groups.google.com/a/chromium.org/forum/#!forum/chromium-hterm).

- xterm: The grandfather of terminal emulators. [Source](https://invisible-island.net/datafiles/release/xterm.tar.gz).

- Connectbot: Android SSH client. [Source](https://github.com/connectbot/connectbot)

- Android Terminal Emulator: Android terminal app which Terfux terminal handling is based on. Inactive. [Source](https://github.com/jackpal/Android-Terminal-Emulator).
</details>

##



### Debugging

You can help debug problems of the `Terfux` app and its plugins by setting appropriate `logcat` `Log Level` in `Terfux` app settings -> `<APP_NAME>` -> `Debugging` -> `Log Level` (Requires `Terfux` app version `>= 0.118.0`). The `Log Level` defaults to `Normal` and log level `Verbose` currently logs additional information. Its best to revert log level to `Normal` after you have finished debugging since private data may otherwise be passed to `logcat` during normal operation and moreover, additional logging increases execution time.

The plugin apps **do not execute the commands themselves** but send execution intents to `Terfux` app, which has its own log level which can be set in `Terfux` app settings -> `Terfux` -> `Debugging` -> `Log Level`. So you must set log level for both `Terfux` and the respective plugin app settings to get all the info.

Once log levels have been set, you can run the `logcat` command in `Terfux` app terminal to view the logs in realtime (`Ctrl+c` to stop) or use `logcat -d > logcat.txt` to take a dump of the log. You can also view the logs from a PC over `ADB`. For more information, check official android `logcat` guide [here](https://developer.android.com/studio/command-line/logcat).

Moreover, users can generate Terfux files `stat` info and `logcat` dump automatically too with terminal's long hold options menu `More` -> `Report Issue` option and selecting `YES` in the prompt shown to add debug info. This can be helpful for reporting and debugging other issues. If the report generated is too large, then `Save To File` option in context menu (3 dots on top right) of `ReportActivity` can be used and the file viewed/shared instead.

Users must post complete report (optionally without sensitive info) when reporting issues. Issues opened with **(partial) screenshots of error reports** instead of text will likely be automatically closed/deleted.

##### Log Levels

- `Off` - Log nothing.
- `Normal` - Start logging error, warn and info messages and stacktraces.
- `Debug` - Start logging debug messages.
- `Verbose` - Start logging verbose messages.
##



## For Maintainers and Contributors

The [Terfux-shared](Terfux-shared) library was added in [`v0.109`](https://github.com/Terfux/Terfux-app/releases/tag/v0.109). It defines shared constants and utils of the Terfux app and its plugins. It was created to allow for the removal of all hardcoded paths in the Terfux app. Some of the Terfux plugins are using this as well and rest will in future. If you are contributing code that is using a constant or a util that may be shared, then define it in `Terfux-shared` library if it currently doesn't exist and reference it from there. Update the relevant changelogs as well. Pull requests using hardcoded values **will/should not** be accepted. Terfux app and plugin specific classes must be added under `com.Terfux.shared.Terfux` package and general classes outside it. The [`Terfux-shared` `LICENSE`](Terfux-shared/LICENSE.md) must also be checked and updated if necessary when contributing code. The licenses of any external library or code must be honoured.

The main Terfux constants are defined by [`TerfuxConstants`](https://github.com/Terfux/Terfux-app/blob/master/Terfux-shared/src/main/java/com/Terfux/shared/Terfux/TerfuxConstants.java) class. It also contains information on how to fork Terfux or build it with your own package name. Changing the package name will require building the bootstrap zip packages and other packages with the new `$PREFIX`, check [Building Packages](https://github.com/Terfux/Terfux-packages/wiki/Building-packages) for more info.

Check [Terfux Libraries](https://github.com/Terfux/Terfux-app/wiki/Terfux-Libraries) for how to import Terfux libraries in plugin apps and [Forking and Local Development](https://github.com/Terfux/Terfux-app/wiki/Terfux-Libraries#forking-and-local-development) for how to update Terfux libraries for plugins.

Commit messages **must** use [Conventional Commits](https://www.conventionalcommits.org) specs so that chagelogs can automatically be generated by the [`create-conventional-changelog`](https://github.com/Terfux/create-conventional-changelog) script, check its repo for further details on the spec. Use the following `types` as `Added: Add foo`, `Added|Fixed: Add foo and fix bar`, `Changed!: Change baz as a breaking change`, etc. You can optionally add a scope as well, like `Fixed(terminal): Some bug`. The space after `:` is necessary.

- **Added** for new features.
- **Changed** for changes in existing functionality.
- **Deprecated** for soon-to-be removed features.
- **Removed** for now removed features.
- **Fixed** for any bug fixes.
- **Security** in case of vulnerabilities.
- **Docs** for updating documentation.

Changelogs for releases are generated based on [Keep a Changelog](https://github.com/olivierlacan/keep-a-changelog) specs.

The `versionName` in `build.gradle` files of Terfux and its plugin apps must follow the [semantic version `2.0.0` spec](https://semver.org/spec/v2.0.0.html) in the format `major.minor.patch(-prerelease)(+buildmetadata)`. When bumping `versionName` in `build.gradle` files and when creating a tag for new releases on GitHub, make sure to include the patch number as well, like `v0.1.0` instead of just `v0.1`. The `build.gradle` files and `attach_debug_apks_to_release` workflow validates the version as well and the build/attachment will fail if `versionName` does not follow the spec.
##



## Forking

- Check [`TerfuxConstants`](https://github.com/Terfux/Terfux-app/blob/master/Terfux-shared/src/main/java/com/Terfux/shared/Terfux/TerfuxConstants.java) javadocs for instructions on what changes to make in the app to change package name.
- You also need to recompile bootstrap zip for the new package name. Check [building bootstrap](https://github.com/Terfux/Terfux-packages/wiki/For-maintainers#build-bootstrap-archives), [here](https://github.com/Terfux/Terfux-app/issues/1983) and [here](https://github.com/Terfux/Terfux-app/issues/2081#issuecomment-865280111).
- Currently, not all plugins use `TerfuxConstants` from `Terfux-shared` library and have hardcoded `com.Terfux` values and will need to be manually patched.
- If forking Terfux plugins, check [Forking and Local Development](https://github.com/Terfux/Terfux-app/wiki/Terfux-Libraries#forking-and-local-development) for info on how to use Terfux libraries for plugins.
