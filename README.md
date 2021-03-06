### LanguageTool for Sublime Text 2/3

#### Overview

This is a simple adapter to integrate
[LanguageTool](https://languagetool.org/) (an open source proof-reading
program) into Sublime Text 2/3.

From https://www.languagetool.org/:

> LanguageTool is an Open Source proof­reading program for English, French,
> German, Polish, and more than 20 other languages. It finds many errors that
> a simple spell checker cannot detect and several grammar problems.

![](https://cdn.rawgit.com/gtarawneh/languagetool-sublime/master/demo.gif)


## Installation

### By Package Control

1. Download & Install **`Sublime Text 3`** (https://www.sublimetext.com/3)
1. Go to the menu **`Tools -> Install Package Control`**, then,
    wait few seconds until the installation finishes up
1. Now,
    Go to the menu **`Preferences -> Package Control`**
1. Type **`Add Channel`** on the opened quick panel and press <kbd>Enter</kbd>
1. Then,
    input the following address and press <kbd>Enter</kbd>
    ```
    https://raw.githubusercontent.com/evandrocoan/StudioChannel/master/channel.json
    ```
1. Go to the menu **`Tools -> Command Palette...
    (Ctrl+Shift+P)`**
1. Type **`Preferences:
    Package Control Settings – User`** on the opened quick panel and press <kbd>Enter</kbd>
1. Then,
    find the following setting on your **`Package Control.sublime-settings`** file:
    ```js
    "channels":
    [
        "https://packagecontrol.io/channel_v3.json",
        "https://raw.githubusercontent.com/evandrocoan/StudioChannel/master/channel.json",
    ],
    ```
1. And,
    change it to the following, i.e.,
    put the **`https://raw.githubusercontent...`** line as first:
    ```js
    "channels":
    [
        "https://raw.githubusercontent.com/evandrocoan/StudioChannel/master/channel.json",
        "https://packagecontrol.io/channel_v3.json",
    ],
    ```
    * The **`https://raw.githubusercontent...`** line must to be added before the **`https://packagecontrol.io...`** one, otherwise,
      you will not install this forked version of the package,
      but the original available on the Package Control default channel **`https://packagecontrol.io...`**
1. Now,
    go to the menu **`Preferences -> Package Control`**
1. Type **`Install Package`** on the opened quick panel and press <kbd>Enter</kbd>
1. Then,
    search for **`LanguageTool`** and press <kbd>Enter</kbd>

See also:

1. [ITE - Integrated Toolset Environment](https://github.com/evandrocoan/ITE)
1. [Package control docs](https://packagecontrol.io/docs/usage) for details.


#### Usage

Open the file you want to proof-read then:

1. Run a language check (<kbd>ctrl+shift+c</kbd>). Any problems identified by LanguageTool will be highlighted.
2. Move between the problems using <kbd>alt+down</kbd> (next) and <kbd>alt+up</kbd> (previous).
3. A panel at the bottom will display a brief description  of the highlighted problem and suggest corrections if available.
4. Begin typing to correct the selected problem or press <kbd>alt+shift+f</kbd> to apply the suggested correction.
5. To ignore a problem, press <kbd>alt+d</kbd>.
6. Auto-correcting a problem or ignoring it will move focus to the next problem.

All commands and their keyboard shortcuts are in the command palette with the
prefix `LanguageTool:`.

#### Configuration

The settings file for the plugin can be opened from the `Preferences` menu
(`Preferences` &rarr; `Package Settings` &rarr; `LanguageTool` &rarr;
`Settings - User`). Default settings are in the corresponding submenu item
`Settings - Default`. Note that default settings are provided for reference
and should not be edited as they may be overwritten when the plugin is updated
or reinstalled. Instead, copy and modify any settings you wish to override to
`Settings - User`.

#### Local vs. Remote Checking

The adapter supports local and remote LanguageTool servers. Remote checking is
the default and works by submitting text over https to an api endpoint on
https://languagetool.org (this can be changed in plugin settings). This public
service is subject to usage constraints including:

1. Maximum text size of 50Kb
2. Access limited to 20 requests/minute per IP

(See http://wiki.languagetool.org/public-http-api for full details.)

Instead of using the public (remote) LanguageTool service, text can be checked
using a local LanguageTool Installation. A local LanguageTool server can be
started by the plugin itself using the command `LanguageTool: Start Local
Server` (this requires the settings entry `languagetool_jar` to point to the
local languagetool JAR file), or from the command line following the
instructions in http://wiki.languagetool.org/http-server.

The settings file contains remote and local server URL entries. A third option
`default_server` indicates which of these is used when the command
`LanguageTool: Check Text` is ran. As an added convenience, two more commands:

* `LanguageTool: Check Text (Local Server)`
* `LanguageTool: Check Text (Remote Server)`

are provided, which can be used to check text using the local/remote servers
regardless of `default_server`. This can be used for one-off checks when it's
desirable to use a particular server with certain pieces of text.

#### License

This plugin is freely available under
[GPLv2](https://www.gnu.org/licenses/old-licenses/gpl-2.0.html) or later.

#### Contributing

Feel free to fork and improve. All contributions are welcome.
