# droopescan

[](https://github.com/SamJoan/droopescan#droopescan)

[![Build Status](https://camo.githubusercontent.com/8eacdba20d198e15ae60ebd93c7b064ee4d3feff7fa0772d882fa2328bbdfdbe/68747470733a2f2f6170692e7472617669732d63692e6f72672f64726f6f70652f64726f6f70657363616e2e7376673f6272616e63683d6d6173746572)](https://travis-ci.org/droope/droopescan) [![PyPI version](https://camo.githubusercontent.com/0fcc8d929d997b3bb2b8fe91bf2b5c0d005640945ba6351eb02cf77abf31ba8d/68747470733a2f2f696d672e736869656c64732e696f2f707970692f762f64726f6f70657363616e2e737667)](https://pypi.python.org/pypi/droopescan) [![AGPL license](https://camo.githubusercontent.com/1c6af41362c62a454cbb6ce26d15816060de2619c359f1d0f589887cf80497ec/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f6c6963656e73652d4147504c2d626c75652e737667)](https://github.com/droope/droopescan/blob/master/LICENSE)

A plugin-based scanner that aids security researchers in identifying issues with several CMS.

Usage of droopescan for attacking targets without prior mutual consent is illegal. It is the end user's responsibility to obey all applicable local, state and federal laws. Developers assume no liability and are not responsible for any misuse or damage caused by this program. Please note that while droopescan outputs the most CMS likely version installed on the remote host, any correlation between version numbers and vulnerabilities must be done manually by the user.

Supported CMS are:

- SilverStripe
- Wordpress
- Drupal

Partial functionality for:

- Joomla (version enumeration and interesting URLs only)
- Moodle (plugin & theme very limited, watch out)

```
computer:~/droopescan$ droopescan scan drupal -u http://example.org/ -t 32
[+] No themes found.

[+] Possible interesting urls found:
    Default changelog file - https://www.example.org/CHANGELOG.txt
    Default admin - https://www.example.org/user/login

[+] Possible version(s):
    7.34

[+] Plugins found:
    views https://www.example.org/sites/all/modules/views/
        https://www.example.org/sites/all/modules/views/README.txt
        https://www.example.org/sites/all/modules/views/LICENSE.txt
    token https://www.example.org/sites/all/modules/token/
        https://www.example.org/sites/all/modules/token/README.txt
        https://www.example.org/sites/all/modules/token/LICENSE.txt
    pathauto https://www.example.org/sites/all/modules/pathauto/
        https://www.example.org/sites/all/modules/pathauto/README.txt
        https://www.example.org/sites/all/modules/pathauto/LICENSE.txt
        https://www.example.org/sites/all/modules/pathauto/API.txt
    libraries https://www.example.org/sites/all/modules/libraries/
        https://www.example.org/sites/all/modules/libraries/CHANGELOG.txt
        https://www.example.org/sites/all/modules/libraries/README.txt
        https://www.example.org/sites/all/modules/libraries/LICENSE.txt
    entity https://www.example.org/sites/all/modules/entity/
        https://www.example.org/sites/all/modules/entity/README.txt
        https://www.example.org/sites/all/modules/entity/LICENSE.txt
    google_analytics https://www.example.org/sites/all/modules/google_analytics/
        https://www.example.org/sites/all/modules/google_analytics/README.txt
        https://www.example.org/sites/all/modules/google_analytics/LICENSE.txt
    ctools https://www.example.org/sites/all/modules/ctools/
        https://www.example.org/sites/all/modules/ctools/CHANGELOG.txt
        https://www.example.org/sites/all/modules/ctools/LICENSE.txt
        https://www.example.org/sites/all/modules/ctools/API.txt
    features https://www.example.org/sites/all/modules/features/
        https://www.example.org/sites/all/modules/features/CHANGELOG.txt
        https://www.example.org/sites/all/modules/features/README.txt
        https://www.example.org/sites/all/modules/features/LICENSE.txt
        https://www.example.org/sites/all/modules/features/API.txt
    [... snip for README ...]

[+] Scan finished (0:04:59.502427 elapsed)
```

You can get a full list of options by running:

```shell
droopescan --help
droopescan scan --help
```

# Why not X?

[](https://github.com/SamJoan/droopescan#why-not-x)

Because droopescan:

- is fast
- is stable
- is up to date
- allows simultaneous scanning of multiple sites
- is 100% python

# Installation

[](https://github.com/SamJoan/droopescan#installation)

## With pip (recommended)

[](https://github.com/SamJoan/droopescan#with-pip-recommended)

Installation is easy using pip:

```shell
apt-get install python-pip
pip install droopescan
```

## From sources

[](https://github.com/SamJoan/droopescan#from-sources)

Manual installation is as follows:

```shell
git clone https://github.com/droope/droopescan.git
cd droopescan
pip install -r requirements.txt
./droopescan scan --help
```

The master branch corresponds to the latest release (what is in pypi). Development branch is unstable and all pull requests must be made against it.

## BlackArch

[](https://github.com/SamJoan/droopescan#blackarch)

BlackArch [package](https://github.com/BlackArch/blackarch/blob/master/packages/droopescan/PKGBUILD) installation (maintained by a third party):

```shell
sudo pacman -S droopescan
```

## Docker

[](https://github.com/SamJoan/droopescan#docker)

You can build a docker image and run droopescan from Docker:

```shell
git clone https://github.com/droope/droopescan.git
cd droopescan
docker build -t droope/droopescan .
# display help
docker run --rm droope/droopescan
# example scanning a drupal site
docker run --rm droope/droopescan scan drupal -u https://drupal.example.com
```

# Features

[](https://github.com/SamJoan/droopescan#features)

## Scan types

[](https://github.com/SamJoan/droopescan#scan-types)

Droopescan aims to be the most accurate by default, while not overloading the target server due to excessive concurrent requests. Due to this, by default, a large number of requests will be made with four threads; change these settings by using the `--number` and `--threads` arguments respectively.

This tool is able to perform four kinds of tests. By default all tests are ran, but you can specify one of the following with the `-e` or `--enumerate` flag:

- p -- _Plugin checks_: Performs several thousand HTTP requests and returns a listing of all plugins found to be installed in the target host.
- t -- _Theme checks_: As above, but for themes.
- v -- _Version checks_: Downloads several files and, based on the checksums of these files, returns a list of all possible versions.
- i -- _Interesting url checks_: Checks for interesting urls (admin panels, readme files, etc.)

## Target specification

[](https://github.com/SamJoan/droopescan#target-specification)

You can specify a particular host to scan by passing the `-u` or `--url` parameter:

```
    droopescan scan drupal -u example.org
```

You can also omit the `drupal` argument. This will trigger “CMS identification”, like so:

```
    droopescan scan -u example.org
```

Multiple URLs may be scanned utilising the `-U` or `--url-file` parameter. This parameter should be set to the path of a file which contains a list of URLs.

```
    droopescan scan drupal -U list_of_urls.txt
```

The `drupal` parameter may also be ommited in this example. For each site, it will make several GET requests in order to perform CMS identification, and if the site is deemed to be a supported CMS, it is scanned and added to the output list. This can be useful, for example, to run `droopescan` across all your organisation's sites.

```
    droopescan scan -U list_of_urls.txt
```

The code block below contains an example list of URLs, one per line:

```
http://localhost/drupal/6.0/
http://localhost/drupal/6.1/
http://localhost/drupal/6.10/
http://localhost/drupal/6.11/
http://localhost/drupal/6.12/
```

A file containing URLs and a value to override the default host header with separated by tabs or spaces is also OK for URL files. This can be handy when conducting a scan through a large range of hosts and you want to prevent unnecessary DNS queries. To clarify, an example below:

```
192.168.1.1	example.org
http://192.168.1.1/	example.org
http://192.168.1.2/drupal/	example.org
```

It is quite tempting to test whether the scanner works for a particular CMS by scanning the official site (e.g. `wordpress.org` for wordpress), but the official sites rarely run vainilla installations of their respective CMS or do unorthodox things. For example, `wordpress.org` runs the bleeding edge version of wordpress, which will not be identified as wordpress by `droopescan` at all because the checksums do not match any known wordpress version.

## Authentication

[](https://github.com/SamJoan/droopescan#authentication)

The application fully supports `.netrc` files and `http_proxy` environment variables.

Use a .netrc file for basic authentication. An example [netrc](https://www.gnu.org/software/inetutils/manual/html_node/The-_002enetrc-file.html) (a file named `.netrc` placed in your root home directory) file could look as follows:

```
machine secret.google.com
    login admin@google.com
    password Winter01
```

You can set the `http_proxy` and `https_proxy` variables. These allow you to set a parent HTTP proxy, in which you can handle more complex types of authentication (e.g. Fiddler, ZAP, Burp)

```
export http_proxy='user:password@localhost:8080'
export https_proxy='user:password@localhost:8080'
droopescan scan drupal --url http://localhost/drupal
```

_WARNING:_ By design, to allow intercepting proxies and the testing of applications with bad SSL, droopescan allows self-signed or otherwise invalid certificates. ˙ ͜ʟ˙

## Output

[](https://github.com/SamJoan/droopescan#output)

This application supports both "standard output", meant for human consumption, or JSON, which is more suitable for machine consumption. This output is stable between major versions.

This can be controlled with the `--output` flag. Some sample JSON output would look as follows (minus the excessive whitespace):

```
{
  "themes": {
    "is_empty": true,
    "finds": [

    ]
  },
  "interesting urls": {
    "is_empty": false,
    "finds": [
      {
        "url": "https:\/\/www.drupal.org\/CHANGELOG.txt",
        "description": "Default changelog file."
      },
      {
        "url": "https:\/\/www.drupal.org\/user\/login",
        "description": "Default admin."
      }
    ]
  },
  "version": {
    "is_empty": false,
    "finds": [
      "7.29",
      "7.30",
      "7.31"
    ]
  },
  "plugins": {
    "is_empty": false,
    "finds": [
      {
        "url": "https:\/\/www.drupal.org\/sites\/all\/modules\/views\/",
        "name": "views"
      },
      [...snip...]
    ]
  }
}
```

Some attributes might be missing from the JSON object if parts of the scan are not ran.

This is how multi-site output looks like; each line contains a valid JSON object as shown above.

```
    $ droopescan scan drupal -U six_and_above.txt -e v
    {"host": "http://localhost/drupal-7.6/", "version": {"is_empty": false, "finds": ["7.6"]}}
    {"host": "http://localhost/drupal-7.7/", "version": {"is_empty": false, "finds": ["7.7"]}}
    {"host": "http://localhost/drupal-7.8/", "version": {"is_empty": false, "finds": ["7.8"]}}
    {"host": "http://localhost/drupal-7.9/", "version": {"is_empty": false, "finds": ["7.9"]}}
    {"host": "http://localhost/drupal-7.10/", "version": {"is_empty": false, "finds": ["7.10"]}}
    {"host": "http://localhost/drupal-7.11/", "version": {"is_empty": false, "finds": ["7.11"]}}
    {"host": "http://localhost/drupal-7.12/", "version": {"is_empty": false, "finds": ["7.12"]}}
    {"host": "http://localhost/drupal-7.13/", "version": {"is_empty": false, "finds": ["7.13"]}}
    {"host": "http://localhost/drupal-7.14/", "version": {"is_empty": false, "finds": ["7.14"]}}
    {"host": "http://localhost/drupal-7.15/", "version": {"is_empty": false, "finds": ["7.15"]}}
    {"host": "http://localhost/drupal-7.16/", "version": {"is_empty": false, "finds": ["7.16"]}}
    {"host": "http://localhost/drupal-7.17/", "version": {"is_empty": false, "finds": ["7.17"]}}
    {"host": "http://localhost/drupal-7.18/", "version": {"is_empty": false, "finds": ["7.18"]}}
    {"host": "http://localhost/drupal-7.19/", "version": {"is_empty": false, "finds": ["7.19"]}}
    {"host": "http://localhost/drupal-7.20/", "version": {"is_empty": false, "finds": ["7.20"]}}
    {"host": "http://localhost/drupal-7.21/", "version": {"is_empty": false, "finds": ["7.21"]}}
    {"host": "http://localhost/drupal-7.22/", "version": {"is_empty": false, "finds": ["7.22"]}}
    {"host": "http://localhost/drupal-7.23/", "version": {"is_empty": false, "finds": ["7.23"]}}
    {"host": "http://localhost/drupal-7.24/", "version": {"is_empty": false, "finds": ["7.24"]}}
    {"host": "http://localhost/drupal-7.25/", "version": {"is_empty": false, "finds": ["7.25"]}}
    {"host": "http://localhost/drupal-7.26/", "version": {"is_empty": false, "finds": ["7.26"]}}
    {"host": "http://localhost/drupal-7.27/", "version": {"is_empty": false, "finds": ["7.27"]}}
    {"host": "http://localhost/drupal-7.28/", "version": {"is_empty": false, "finds": ["7.28"]}}
    {"host": "http://localhost/drupal-7.29/", "version": {"is_empty": false, "finds": ["7.29"]}}
    {"host": "http://localhost/drupal-7.30/", "version": {"is_empty": false, "finds": ["7.30"]}}
    {"host": "http://localhost/drupal-7.31/", "version": {"is_empty": false, "finds": ["7.31"]}}
    {"host": "http://localhost/drupal-7.32/", "version": {"is_empty": false, "finds": ["7.32"]}}
    {"host": "http://localhost/drupal-7.33/", "version": {"is_empty": false, "finds": ["7.33"]}}
    {"host": "http://localhost/drupal-7.34/", "version": {"is_empty": false, "finds": ["7.34"]}}
```

## Debug

[](https://github.com/SamJoan/droopescan#debug)

When things are not going exactly your way, you can check why by using the `--debug-requests` command.

Some output might look like this:

```
computer:~/droopescan# droopescan scan silverstripe -u http://localhost -n 10 -e p --debug-requests
[head] http://localhost/framework/... 403
[head] http://localhost/cms/css/layout.css... 404
[head] http://localhost/framework/css/UploadField.css... 200
[head] http://localhost/misc/test/error/404/ispresent.html... 404
[head] http://localhost/widgetextensions/... 404
[head] http://localhost/orbit/... 404
[head] http://localhost/sitemap/... 404
[head] http://localhost/simplestspam/... 404
[head] http://localhost/ecommerce_modifier_example/... 404
[head] http://localhost/silverstripe-hashpath/... 404
[head] http://localhost/timeline/... 404
[head] http://localhost/silverstripe-hiddenfields/... 404
[head] http://localhost/addressable/... 404
[head] http://localhost/silverstripe-description/... 404
[+] No plugins found.

[+] Scan finished (0:00:00.058422 elapsed)
```

The `--debug` paramter also exists and may be used to debug application internals.

## Stats

[](https://github.com/SamJoan/droopescan#stats)

You can get an up to date report on the capabilities of the scanner by running the following command

```
    droopescan stats
```

Some sample output might look as follows:

```
Functionality available for ‘drupal’:
- Enumerate plugins (XXXX plugins.)
- Enumerate themes (XXXX themes.)
- Enumerate interesting urls (X urls.)
- Enumerate version (up to version X.X.X-alphaXX, X.XX, X.XX.)
Functionality available for ‘joomla’:
- Enumerate interesting urls (X urls.)
- Enumerate version (up to version XX.X, X.X.X, X.X.XX.rcX.)
Functionality available for ‘wordpress’:
- Enumerate interesting urls (X urls.)
- Enumerate version (up to version X.X.X, X.X.X, X.X.X.)
Functionality available for ‘silverstripe’:
- Enumerate plugins (XXX plugins.)
- Enumerate themes (XX themes.)
- Enumerate interesting urls (X urls.)
- Enumerate version (up to version X.X.XX, X.X.XX, X.X.XX.)
```

It is important to verify that the latest version available for the CMS installation is available within `droopescan`, as otherwise results may be inaccurate.

# Contribute

[](https://github.com/SamJoan/droopescan#contribute)

## Create your own plugin

[](https://github.com/SamJoan/droopescan#create-your-own-plugin)

You can add suport for your favourite CMS. The process is actually quite simple, and a lot of information can be glimpsed by viewing the example.py file in the plugins/ folder.

This file should serve well as a base for your implementation.

You can create your own plugin for `Joomla` and enable it as follows:

```
$ cp plugins/example.py plugins/joomla.py
$ cp plugins.d/example.conf plugins.d/joomla.conf
```

You then need to go to `plugins/joomla.py` and change a few things:

- The class name needs to be Joomla.
- The plugin label (located at Meta.label) needs to be changed to joomla.
- At the end of the file, the register call needs to be modified to reflect the correct class name.
- The exposed function, 'example', needs to be renamed to joomla.

```
    @controller.expose(help='example scanner')
    def joomla(self):
        self.plugin_init()
```

We also need to change the `plugins.d/joomla.conf` file, and change it to the following:

```
[joomla]
enable_plugin = true
```

We should now be in a state which looks as follows:

```
$ droopescan scan joomla
[+] --url parameter is required.
```

Your next step would be to generate a valid plugin wordlist, a valid theme wordlist, a [versions.xml](https://github.com/droope/droopescan/blob/development/plugins/drupal/versions.xml) file, and optionally a list of interesting URLs, as well as replace all variables that are in joomla.py with values that are correct for your implementation.

The plugin needs to update automatically in order for a pull request to be accepted. Further documentation may be later made available, but for now, keep in mind that the update_version_check, update_version, update_plugins_check and update_plugins need to be implemented. For reference, please review the `drupal.py` file. This is required in order to ensure plugins are kept to date.

## Issues & Pull Requests

[](https://github.com/SamJoan/droopescan#issues--pull-requests)

Pull requests that create new plugins are welcome provided that maintenance for those plugins is done automatically.

Please remember to make your pull requests against the develoment branch rather than the master. Issues can be raised on the issue tracker here on GitHub.

To run tests, some dependencies must be installed. Running the following commands will result in them being installed and the tests being ran:

```
    apt-get install libxslt1-dev libxml2-dev zlib1g-dev python python-pip python-dev python3 python3-pip python3-dev
    pip install -r requirements.txt -r requirements_test.txt
    pip3 install -r requirements.txt -r requirements_test.txt
    ./droopescan test
```

You can run individual tests with the `-s` flag.

```
./droopescan test -s test_integration_drupal
```

# License

[](https://github.com/SamJoan/droopescan#license)

The project is licensed under the AGPL license. See LICENSE file.

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/SamJoan/droopescan). Be sure to check out the original post for more details.

# Droopescan – CMS Based Web Applications Scanner

Last Updated : 04 Jun, 2024

****Droopescan**** tool is an automated script developed in the Python language which is used in the initial reconnaissance and information gathering phases. This tool gathers the CMS information which is been used by the target domain. This can include CMS type, version, themes, plugins, etc. This tool is also available on the GitHub platform for free and is open-source to use. So you can also become a contributor in this repository.

****Note****: Make Sure You have Python Installed on your System, as this is a python-based tool. Click to check the Installation process: [Python Installation Steps on Linux](https://www.geeksforgeeks.org/how-to-install-python-on-linux)

## Installation of Droopescan  Tool on Kali Linux OS

****Step 1****: Use the following command to install the tool in your Kali Linux operating system.

git clone https://github.com/SamJoan/droopescan.git

![](https://media.geeksforgeeks.org/wp-content/uploads/20211109205437/Step1.png)

****Step 2****: Now use the following command to move into the directory of the tool. You have to move in the directory in order to run the tool.

cd droopescan

![](https://media.geeksforgeeks.org/wp-content/uploads/20211109205439/Step2.png)

****Step 3****: You are in the directory of the Droopescan . Now you have to install a dependency of the Droopescan using the following command.

sudo pip3 install -r requirements.txt

![](https://media.geeksforgeeks.org/wp-content/uploads/20211109205441/Step3min.png)

****Step 4****: All the dependencies have been installed in your Kali Linux operating system. Now use the following command to run the tool and check help section.

droopescan -h

![](https://media.geeksforgeeks.org/wp-content/uploads/20211109205443/Step4.png)

## Working with Droopescan  Tool on Kali Linux OS

****Example 1:**** Scanning Target 1 (geeksforgeeks.org)

droopescan scan joomla -u geeksforgeeks.org

![](https://media.geeksforgeeks.org/wp-content/uploads/20211109205431/Example11.png)

We have possible interesting urls that contains information about CMS.

![](https://media.geeksforgeeks.org/wp-content/uploads/20211109205432/Example12min.png)

****Example 2:**** Scanning Target 2 (example.com)

droopescan scan drupal -u example.com

In this example, we have specified the target domain as example.com.

![](https://media.geeksforgeeks.org/wp-content/uploads/20211109211339/Screenshot1060.png)

We have got the plugins list which are been used by the domain.

![Screenshot1061111zon-copy-2-(1)](https://media.geeksforgeeks.org/wp-content/uploads/20240604161823/Screenshot1061111zon-copy-2-(1).webp)

We have also got the Possible versions and interesting URLs list.

![](https://media.geeksforgeeks.org/wp-content/uploads/20211109211343/Screenshot1062211zon.png)

****Example 3:**** Displaying Stats of tool

droopescan stats

In this example, we have displayed the overall stats of tool. This stats shows the supported CMS, Version details and other information.

![](https://media.geeksforgeeks.org/wp-content/uploads/20211109205436/Example3min.png)

**Credit:** This information was adapted from an excellent guide on [GeeksForGeeks](https://www.geeksforgeeks.org/droopescan-cms-based-web-applications-scanner/). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/x3LieAkeePM?si=4KX-ymJl4aH7PL53" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=x3LieAkeePM). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/3hYRmC7ueAE?si=fH890QUygner6_4q" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=3hYRmC7ueAE). Be sure to check out the original post for more details. The video is not in English language and closed captioning is not working properly so just follow along with video muted. The tutorial is visually in English.

