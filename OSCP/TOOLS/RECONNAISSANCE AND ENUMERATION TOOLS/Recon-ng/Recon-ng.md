# The Recon-ng Framework

[](https://github.com/lanmaster53/recon-ng#the-recon-ng-framework)

[Recon-ng content now available on Pluralsight!](https://app.pluralsight.com/library/courses/technical-information-gathering-recon-ng)

Recon-ng is a full-featured reconnaissance framework designed with the goal of providing a powerful environment to conduct open source web-based reconnaissance quickly and thoroughly.

Recon-ng has a look and feel similar to the Metasploit Framework, reducing the learning curve for leveraging the framework. However, it is quite different. Recon-ng is not intended to compete with existing frameworks, as it is designed exclusively for web-based open source reconnaissance. If you want to exploit, use the Metasploit Framework. If you want to social engineer, use the Social-Engineer Toolkit. If you want to conduct reconnaissance, use Recon-ng! See the [Wiki](https://github.com/lanmaster53/recon-ng/wiki) to get started.

Recon-ng is a completely modular framework and makes it easy for even the newest of Python developers to contribute. See the [Development Guide](https://github.com/lanmaster53/recon-ng/wiki/Development-Guide) for more information on building and maintaining modules.

## Sponsors

[](https://github.com/lanmaster53/recon-ng#sponsors)

[![Black Hills Information Security](https://camo.githubusercontent.com/136832cc8ea4e8bd6735277567e1b0776c58c8e00657b22b1a328b4cc03d4214/68747470733a2f2f7777772e626c61636b68696c6c73696e666f7365632e636f6d2f77702d636f6e74656e742f75706c6f6164732f323031362f30332f424849532d6c6f676f2d7765622e706e67)](http://www.blackhillsinfosec.com/)

  

[![Practical Security Services](https://camo.githubusercontent.com/c1b45192f19df5df6cc11743a69ac97970b6272260a26680a699a5ff64c79d67/68747470733a2f2f7777772e7072616374697365632e636f6d2f7374617469632f696d616765732f696d67732f737469636b792d6c6f676f2e706e67)](http://www.practisec.com/)

## Donations

[](https://github.com/lanmaster53/recon-ng#donations)

Recon-ng is free software. However, large amounts of time and effort go into its continued development. If you are interested in financially supporting the project, you can view and assist in marketing the [Pluralsight content](https://app.pluralsight.com/library/courses/technical-information-gathering-recon-ng), or send a donation to tjt1980[at]gmail.com via PayPal. Thank you.

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/lanmaster53/recon-ng). Be sure to check out the original post for more details.

# Recon-NG Tutorial

In this recon-ng tutorial, discover open source intelligence and easily **pivot** to new results. Using a modular approach, collect and dig deeper into extracted data.

## What is Recon-ng?

[Recon-ng](https://github.com/lanmaster53/recon-ng) is a reconnaissance / OSINT tool with an interface similar to Metasploit. Running recon-ng from the command line speeds up the recon process as it automates gathering information from open sources.

Recon-ng has a variety of options to configure, perform recon, and output results to different report types.

The interactive console provides a number of helpful features such as command completion and contextual help.

Recon-NG Tutorial & Tips

- [What is Recon-NG](https://hackertarget.com/recon-ng-tutorial/#what)
- [Install Recon-NG](https://hackertarget.com/recon-ng-tutorial/#install)
- [Using Recon-NG](https://hackertarget.com/recon-ng-tutorial/#use)
- [How to create a workspace](https://hackertarget.com/recon-ng-tutorial/#workspace)
- [Recon-ng Marketplace and Modules](https://hackertarget.com/recon-ng-tutorial/#marketplace)
- [Recon-ng Modules](https://hackertarget.com/recon-ng-tutorial/#modules)
- [Recon-ng Examples](https://hackertarget.com/recon-ng-tutorial/#examples)
- [Add API keys to Recon-ng](https://hackertarget.com/recon-ng-tutorial/#API)
- [Recon-ng configuration files](https://hackertarget.com/recon-ng-tutorial/#configuration)

## Recon-ng Installation

Installing Recon-ng is very simple and there are a few common ways. Below are a few examples;

### Kali:

At the time of this article version 5.1.2 comes pre-installed with Kali Linux. Having said that, its good to run `apt-get update && apt-get install recon-ng` to ensure latest dependencies installed.

![OSINT with our Recon-NG Tutorial](https://hackertarget.com/images/osint-recon.png)

### Ubuntu:

Requires `git` and `pip` installed.

test@ubuntu:~/$ git clone https://github.com/lanmaster53/recon-ng.git
test@ubuntu:~/$ cd recon-ng
test@ubuntu:~/recon-ng/$ pip install -r REQUIREMENTS

Next to run recon-ng;

test@ubuntu:~/recon-ng/$ ./recon-ng

The Recon-NG console is now loaded.

    _/_/_/    _/_/_/_/    _/_/_/    _/_/_/    _/      _/            _/      _/    _/_/_/
   _/    _/  _/        _/        _/      _/  _/_/    _/            _/_/    _/  _/       
  _/_/_/    _/_/_/    _/        _/      _/  _/  _/  _/  _/_/_/_/  _/  _/  _/  _/  _/_/_/
 _/    _/  _/        _/        _/      _/  _/    _/_/            _/    _/_/  _/      _/ 
_/    _/  _/_/_/_/    _/_/_/    _/_/_/    _/      _/            _/      _/    _/_/_/    
                                                                                        

                                          /\
                                         / \\ /\
    Sponsored by...               /\  /\/  \\V  \/\
                                 / \\/ // \\\\\ \\ \/\
                                // // BLACK HILLS \/ \\
                               www.blackhillsinfosec.com

                  ____   ____   ____   ____ _____ _  ____   ____  ____
                 |____] | ___/ |____| |       |   | |____  |____ |
                 |      |   \_ |    | |____   |   |  ____| |____ |____
                                   www.practisec.com

                      [recon-ng v5.1.2, Tim Tomes (@lanmaster53)]                       

[*] No modules enabled/installed.

[recon-ng][default] > 

## Using recon-ng

From the console it is easy to get `help` and get started with your recon.

[recon-ng][default] > help

Commands (type [help|?] ):
---------------------------------
back            Exits the current context
dashboard       Displays a summary of activity
db              Interfaces with the workspace's database
exit            Exits the framework
help            Displays this menu
index           Creates a module index (dev only)
keys            Manages third party resource credentials
marketplace     Interfaces with the module marketplace
modules         Interfaces with installed modules
options         Manages the current context options
pdb             Starts a Python Debugger session (dev only)
script          Records and executes command scripts
shell           Executes shell commands
show            Shows various framework items
snapshots       Manages workspace snapshots
spool           Spools output to a file
workspaces      Manages workspaces

Recon-ng begins with an empty framework. No modules enabled or installed.

[*] No modules enabled/installed.

## How to use Recon-ng:

### Create a Workspace

There is a lot of options when using this OSINT tool. Maintaining collected information and notes organised is a necessary part of any OSINT investigation. Creating a `workspaces` keeps things orderly and easy to find. When using Recon-ng `workspaces`, all data located and collected is saved within a database in that workspace.

[recon-ng][default] > workspaces create example_name 

[recon-ng][default] > workspaces create example_name
[recon-ng][example_name] > 

The command r`econ-ng -w example_name` opens or returns directly to that workspace.

test@ubuntu:~/$ recon-ng -w example_name 

[recon-ng][example_name] > 

## Recon-ng Marketplace and Modules

Here again the help comes in handy `marketplace help` shows commands for removing modules, how to find more info, search, refresh and install.

[recon-ng][default] > marketplace help
Interfaces with the module marketplace

Usage: marketplace info|install|refresh|remove|search [...] 

Typing `marketplace search` displays a list of all the modules. From which you can start following the white rabbit exploring and getting deeper into recon and [open source intelligence](https://hackertarget.com/quietly-mapping-the-network-attack-surface/).

### Recon-ng modules

Modules are grouped together under various categories and can be found searching on `marketplace`

`- discovery   - exploitation   - import   - recon   - reporting`

Each of the above have sub categories as shown in the table below. Use `marketplace search` for a full table providing information on version, status (installed or not-installed), date updated, dependencies or require keys.

[recon-ng][example_name] > marketplace search

  +---------------------------------------------------------------------------------------------------+
  |                        Path                        | Version |     Status    |  Updated   | D | K |
  +---------------------------------------------------------------------------------------------------+
  | discovery/info_disclosure/cache_snoop              | 1.1     | not installed | 2020-10-13 |   |   |
  | discovery/info_disclosure/interesting_files        | 1.2     | not installed | 2021-10-04 |   |   |
  | exploitation/injection/command_injector            | 1.0     | not installed | 2019-06-24 |   |   |
  | exploitation/injection/xpath_bruter                | 1.2     | not installed | 2019-10-08 |   |   |
  | import/csv_file                                    | 1.1     | not installed | 2019-08-09 |   |   |
  | import/list                                        | 1.1     | not installed | 2019-06-24 |   |   |
  | import/masscan                                     | 1.0     | not installed | 2020-04-07 |   |   |
  | import/nmap                                        | 1.1     | not installed | 2020-10-06 |   |   |
  | recon/companies-contacts/bing_linkedin_cache       | 1.0     | not installed | 2019-06-24 |   | * |
  | recon/companies-contacts/censys_email_address      | 2.0     | not installed | 2021-05-11 | * | * |
  | recon/companies-contacts/pen                       | 1.1     | not installed | 2019-10-15 |   |   |
  | recon/companies-domains/censys_subdomains          | 2.0     | not installed | 2021-05-10 | * | * |
  | recon/companies-domains/pen                        | 1.1     | not installed | 2019-10-15 |   |   |
  | recon/companies-domains/viewdns_reverse_whois      | 1.1     | not installed | 2021-08-24 |   |   |
  | recon/companies-domains/whoxy_dns                  | 1.1     | not installed | 2020-06-17 |   | * |
  | recon/companies-hosts/censys_org                   | 2.0     | not installed | 2021-05-11 | * | * |
  | recon/companies-hosts/censys_tls_subjects          | 2.0     | not installed | 2021-05-11 | * | * |
  | recon/companies-multi/github_miner                 | 1.1     | not installed | 2020-05-15 |   | * |
  | recon/companies-multi/shodan_org                   | 1.1     | not installed | 2020-07-01 | * | * |
  | recon/companies-multi/whois_miner                  | 1.1     | not installed | 2019-10-15 |   |   |
  | recon/contacts-contacts/abc                        | 1.0     | not installed | 2019-10-11 | * |   |
  | recon/contacts-contacts/mailtester                 | 1.0     | not installed | 2019-06-24 |   |   |
  | recon/contacts-contacts/mangle                     | 1.0     | not installed | 2019-06-24 |   |   |
  | recon/contacts-contacts/unmangle                   | 1.1     | not installed | 2019-10-27 |   |   |
  | recon/contacts-credentials/hibp_breach             | 1.2     | not installed | 2019-09-10 |   | * |
  | recon/contacts-credentials/hibp_paste              | 1.1     | not installed | 2019-09-10 |   | * |
  | recon/contacts-domains/migrate_contacts            | 1.1     | not installed | 2020-05-17 |   |   |
  | recon/contacts-profiles/fullcontact                | 1.1     | not installed | 2019-07-24 |   | * |
  | recon/credentials-credentials/adobe                | 1.0     | not installed | 2019-06-24 |   |   |
  | recon/credentials-credentials/bozocrack            | 1.0     | not installed | 2019-06-24 |   |   |
  | recon/credentials-credentials/hashes_org           | 1.0     | not installed | 2019-06-24 |   | * |
  | recon/domains-companies/censys_companies           | 2.0     | not installed | 2021-05-10 | * | * |
  | recon/domains-companies/pen                        | 1.1     | not installed | 2019-10-15 |   |   |
  | recon/domains-companies/whoxy_whois                | 1.1     | not installed | 2020-06-24 |   | * |
  | recon/domains-contacts/hunter_io                   | 1.3     | not installed | 2020-04-14 |   | * |
  | recon/domains-contacts/metacrawler                 | 1.1     | not installed | 2019-06-24 | * |   |
  | recon/domains-contacts/pen                         | 1.1     | not installed | 2019-10-15 |   |   |
  | recon/domains-contacts/pgp_search                  | 1.4     | not installed | 2019-10-16 |   |   |
  | recon/domains-contacts/whois_pocs                  | 1.0     | not installed | 2019-06-24 |   |   |
  | recon/domains-contacts/wikileaker                  | 1.0     | not installed | 2020-04-08 |   |   |
  | recon/domains-credentials/pwnedlist/account_creds  | 1.0     | not installed | 2019-06-24 | * | * |
  | recon/domains-credentials/pwnedlist/api_usage      | 1.0     | not installed | 2019-06-24 |   | * |
  | recon/domains-credentials/pwnedlist/domain_creds   | 1.0     | not installed | 2019-06-24 | * | * |
  | recon/domains-credentials/pwnedlist/domain_ispwned | 1.0     | not installed | 2019-06-24 |   | * |
  | recon/domains-credentials/pwnedlist/leak_lookup    | 1.0     | not installed | 2019-06-24 |   |   |
  | recon/domains-credentials/pwnedlist/leaks_dump     | 1.0     | not installed | 2019-06-24 |   | * |
  | recon/domains-domains/brute_suffix                 | 1.1     | not installed | 2020-05-17 |   |   |
  | recon/domains-hosts/binaryedge                     | 1.2     | not installed | 2020-06-18 |   | * |
  | recon/domains-hosts/bing_domain_api                | 1.0     | not installed | 2019-06-24 |   | * |
  | recon/domains-hosts/bing_domain_web                | 1.1     | not installed | 2019-07-04 |   |   |
  | recon/domains-hosts/brute_hosts                    | 1.0     | not installed | 2019-06-24 |   |   |
  | recon/domains-hosts/builtwith                      | 1.1     | not installed | 2021-08-24 |   | * |
  | recon/domains-hosts/censys_domain                  | 2.0     | not installed | 2021-05-10 | * | * |
  | recon/domains-hosts/certificate_transparency       | 1.2     | not installed | 2019-09-16 |   |   |
  | recon/domains-hosts/google_site_web                | 1.0     | not installed | 2019-06-24 |   |   |
  | recon/domains-hosts/hackertarget                   | 1.1     | not installed | 2020-05-17 |   |   |
  | recon/domains-hosts/mx_spf_ip                      | 1.0     | not installed | 2019-06-24 |   |   |
  | recon/domains-hosts/netcraft                       | 1.1     | not installed | 2020-02-05 |   |   |
  | recon/domains-hosts/shodan_hostname                | 1.1     | not installed | 2020-07-01 | * | * |
  | recon/domains-hosts/spyse_subdomains               | 1.1     | not installed | 2021-08-24 |   | * |
  | recon/domains-hosts/ssl_san                        | 1.0     | not installed | 2019-06-24 |   |   |
  | recon/domains-hosts/threatcrowd                    | 1.0     | not installed | 2019-06-24 |   |   |
  | recon/domains-hosts/threatminer                    | 1.0     | not installed | 2019-06-24 |   |   |
  | recon/domains-vulnerabilities/ghdb                 | 1.1     | not installed | 2019-06-26 |   |   |
  | recon/domains-vulnerabilities/xssed                | 1.1     | not installed | 2020-10-18 |   |   |
  | recon/hosts-domains/migrate_hosts                  | 1.1     | not installed | 2020-05-17 |   |   |
  | recon/hosts-hosts/bing_ip                          | 1.0     | not installed | 2019-06-24 |   | * |
  | recon/hosts-hosts/censys_hostname                  | 2.0     | not installed | 2021-05-10 | * | * |
  | recon/hosts-hosts/censys_ip                        | 2.0     | not installed | 2021-05-10 | * | * |
  | recon/hosts-hosts/censys_query                     | 2.0     | not installed | 2021-05-10 | * | * |
  | recon/hosts-hosts/ipinfodb                         | 1.2     | not installed | 2021-08-24 |   | * |
  | recon/hosts-hosts/ipstack                          | 1.0     | not installed | 2019-06-24 |   | * |
  | recon/hosts-hosts/resolve                          | 1.0     | not installed | 2019-06-24 |   |   |
  | recon/hosts-hosts/reverse_resolve                  | 1.0     | not installed | 2019-06-24 |   |   |
  | recon/hosts-hosts/ssltools                         | 1.0     | not installed | 2019-06-24 |   |   |
  | recon/hosts-hosts/virustotal                       | 1.0     | not installed | 2019-06-24 |   | * |
  | recon/hosts-locations/migrate_hosts                | 1.0     | not installed | 2019-06-24 |   |   |
  | recon/hosts-ports/binaryedge                       | 1.0     | not installed | 2019-06-24 |   | * |
  | recon/hosts-ports/shodan_ip                        | 1.2     | not installed | 2020-07-01 | * | * |
  | recon/locations-locations/geocode                  | 1.0     | not installed | 2019-06-24 |   | * |
  | recon/locations-locations/reverse_geocode          | 1.0     | not installed | 2019-06-24 |   | * |
  | recon/locations-pushpins/flickr                    | 1.0     | not installed | 2019-06-24 |   | * |
  | recon/locations-pushpins/shodan                    | 1.1     | not installed | 2020-07-07 | * | * |
  | recon/locations-pushpins/twitter                   | 1.1     | not installed | 2019-10-17 |   | * |
  | recon/locations-pushpins/youtube                   | 1.2     | not installed | 2020-09-02 |   | * |
  | recon/netblocks-companies/censys_netblock_company  | 2.0     | not installed | 2021-05-11 | * | * |
  | recon/netblocks-companies/whois_orgs               | 1.0     | not installed | 2019-06-24 |   |   |
  | recon/netblocks-hosts/censys_netblock              | 2.0     | not installed | 2021-05-10 | * | * |
  | recon/netblocks-hosts/reverse_resolve              | 1.0     | not installed | 2019-06-24 |   |   |
  | recon/netblocks-hosts/shodan_net                   | 1.2     | not installed | 2020-07-21 | * | * |
  | recon/netblocks-hosts/virustotal                   | 1.0     | not installed | 2019-06-24 |   | * |
  | recon/netblocks-ports/census_2012                  | 1.0     | not installed | 2019-06-24 |   |   |
  | recon/netblocks-ports/censysio                     | 1.0     | not installed | 2019-06-24 |   | * |
  | recon/ports-hosts/migrate_ports                    | 1.0     | not installed | 2019-06-24 |   |   |
  | recon/ports-hosts/ssl_scan                         | 1.1     | not installed | 2021-08-24 |   |   |
  | recon/profiles-contacts/bing_linkedin_contacts     | 1.2     | not installed | 2021-08-24 |   | * |
  | recon/profiles-contacts/dev_diver                  | 1.1     | not installed | 2020-05-15 |   |   |
  | recon/profiles-contacts/github_users               | 1.0     | not installed | 2019-06-24 |   | * |
  | recon/profiles-profiles/namechk                    | 1.0     | not installed | 2019-06-24 |   | * |
  | recon/profiles-profiles/profiler                   | 1.0     | not installed | 2019-06-24 |   |   |
  | recon/profiles-profiles/twitter_mentioned          | 1.0     | not installed | 2019-06-24 |   | * |
  | recon/profiles-profiles/twitter_mentions           | 1.0     | not installed | 2019-06-24 |   | * |
  | recon/profiles-repositories/github_repos           | 1.1     | not installed | 2020-05-15 |   | * |
  | recon/repositories-profiles/github_commits         | 1.0     | not installed | 2019-06-24 |   | * |
  | recon/repositories-vulnerabilities/gists_search    | 1.0     | not installed | 2019-06-24 |   |   |
  | recon/repositories-vulnerabilities/github_dorks    | 1.0     | not installed | 2019-06-24 |   | * |
  | reporting/csv                                      | 1.0     | not installed | 2019-06-24 |   |   |
  | reporting/html                                     | 1.0     | not installed | 2019-06-24 |   |   |
  | reporting/json                                     | 1.0     | not installed | 2019-06-24 |   |   |
  | reporting/list                                     | 1.0     | not installed | 2019-06-24 |   |   |
  | reporting/proxifier                                | 1.0     | not installed | 2019-06-24 |   |   |
  | reporting/pushpin                                  | 1.0     | not installed | 2019-06-24 |   | * |
  | reporting/xlsx                                     | 1.0     | not installed | 2019-06-24 |   |   |
  | reporting/xml                                      | 1.1     | not installed | 2019-06-24 |   |   |
  +---------------------------------------------------------------------------------------------------+

  D = Has dependencies. See info for details.
  K = Requires keys. See info for details.

Marketplace search brings up the full table, however you can be more specific in your search, a couple of examples

recon-ng][default] >marketplace search ssl
[*] Searching module index for 'ssl'...

  +----------------------------------------------------------------------------+
  |             Path            | Version |     Status    |  Updated   | D | K |
  +----------------------------------------------------------------------------+
  | recon/domains-hosts/ssl_san | 1.0     | not installed | 2019-06-24 |   |   |
  | recon/hosts-hosts/ssltools  | 1.0     | not installed | 2019-06-24 |   |   |
  | recon/ports-hosts/ssl_scan  | 1.1     | not installed | 2021-08-24 |   |   |
  +----------------------------------------------------------------------------+

  D = Has dependencies. See info for details.
  K = Requires keys. See info for details.

[recon-ng][default] > 

To find out more info on a specific module

[recon-ng][default] > marketplace info ssltools 

  +---------------------------------------------------------------------------------------+
  | path          | recon/hosts-hosts/ssltools                                                                                                                                                                                 |
  | name          | SSLTools.com Host Name Lookups                                                                                                                                                                             |
  | author        | Tim Maletic (borrowing from the ssl_san module by Zach Graces)                                                                                                                                             |
  | version       | 1.0                                                                                                                                                                                                        |
  | last_updated  | 2019-06-24                                                                                                                                                                                                 |
  | description   | Uses the ssltools.com site to obtain host names from a site's SSL certificate metadata to update the 'hosts' table.  Security issues with the certificate trust are pushed to the 'vulnerabilities' table. |
  | required_keys | []                                                                                                                                                                                                         |
  | dependencies  | []                                                                                                                                                                                                         |
  | files         | []                                                                                                                                                                                                         |
  | status        | not installed                                                                                                                                                                                              |
  +------------------------------------------------------------------------------------+

[recon-ng][default] > 

As noted above Hackertarget has a module. This will be used as an example on how to use recon-ng.

### Recon-ng example

As an example on how to use Recon-ng, `hackertarget` has a module to gather subdomains `recon/domains-hosts/hackertarget`. This module uses the Hackertarget API and [hostname search](https://hackertarget.com/find-dns-host-records/).

#### Install module

To install this module use the following:

[recon-ng][default] > marketplace install hackertarget
[*] Module installed: recon/domains-hosts/hackertarget
[*] Reloading modules...
[recon-ng][default] > 

#### Load module

[recon-ng][default] > modules load hackertarget
[recon-ng][default][hackertarget] > 

#### Module Help

The help command from within a loaded module has different options to the global 'help'.  
When you are ready to explore more modules use 'back'.

[recon-ng][default][hackertarget] > help

Commands (type [help|?] ):
---------------------------------
back            Exits the current context
dashboard       Displays a summary of activity
db              Interfaces with the workspace's database
exit            Exits the framework
goptions        Manages the global context options
help            Displays this menu
info            Shows details about the loaded module
input           Shows inputs based on the source option
keys            Manages third party resource credentials
modules         Interfaces with installed modules
options         Manages the current context options
pdb             Starts a Python Debugger session (dev only)
reload          Reloads the loaded module
run             Runs the loaded module
script          Records and executes command scripts
shell           Executes shell commands
show            Shows various framework items
spool           Spools output to a file

[recon-ng][default][hackertarget] > 

#### Set source

Using `show options`, brings a table showing the source `current value` set at `default`.

[recon-ng][default][hackertarget] > show options

  Name    Current Value  Required  Description
  ------  -------------  --------  -----------
  SOURCE  `default`        yes       source of input (see 'show info' for details)

Now, set the source to the name of the domain investigating. This example uses tesla.com as they have a published big bounty.

Use command `options set SOURCE tesla.com`

[recon-ng][default][hackertarget] > options set SOURCE tesla.com
SOURCE => tesla.com

Use command `info`. This shows `current value` has changed to tesla.com

[recon-ng][default][hackertarget] > info

Options:
  Name    Current Value  Required  Description
  ------  -------------  --------  -----------
  SOURCE  **tesla.com**      yes       source of input (see 'info' for details)

Source Options:
  default      SELECT DISTINCT domain FROM domains WHERE domain IS NOT NULL
  string       string representing a single input
  path         path to a file containing a list of inputs
  query sql    database query returning one column of inputs

Use `input` to see

[recon-ng][default][hackertarget] > input

  +---------------+
  | Module Inputs |
  +---------------+
  | tesla.com     |
  +---------------+

#### Run the module

Type `run` to execute the module.

[recon-ng][default][hackertarget] > run

---------
TESLA.COM
---------
[*] Host: tesla.com
[*] Ip_Address: 104.119.104.74
[*] --------------------------------------------------
[*] Host: o7.ptr6980.tesla.com
[*] Ip_Address: 149.72.144.42
[*] --------------------------------------------------
[*] Host: vpn1.tesla.com
[*] Ip_Address: 8.45.124.215
[*] --------------------------------------------------
[*] Host: apacvpn1.tesla.com
[*] Ip_Address: 8.244.131.215
[*] --------------------------------------------------
[*] Host: cnvpn1.tesla.com
[*] Ip_Address: 114.141.176.215
[*] --------------------------------------------------
[*] Host: vpn2.tesla.com
[*] Ip_Address: 8.47.24.215
[*] --------------------------------------------------
[*] Host: model3.tesla.com
[*] Ip_Address: 205.234.27.221
[*] --------------------------------------------------
[*] Host: o3.ptr1444.tesla.com
[*] Ip_Address: 149.72.152.236
[*] --------------------------------------------------
[*] Host: o2.ptr556.tesla.com
[*] Ip_Address: 149.72.134.64
[*] --------------------------------------------------
[*] Host: o5.ptr8466.tesla.com
[*] Ip_Address: 149.72.172.170
[*] --------------------------------------------------
[*] Host: o6.ptr9437.tesla.com
[*] Ip_Address: 168.245.123.10
[*] --------------------------------------------------
[*] Host: o4.ptr1867.tesla.com
[*] Ip_Address: 149.72.163.58
[*] --------------------------------------------------
[*] Host: marketing.tesla.com
[*] Ip_Address: 13.111.47.196
[*] --------------------------------------------------
[*] Host: o1.ptr2410.link.tesla.com
[*] Ip_Address: 149.72.247.52
[*] --------------------------------------------------
[*] Host: referral.tesla.com
[*] Ip_Address: 72.10.32.90
[*] --------------------------------------------------
[*] Host: mta2.email.tesla.com
[*] Ip_Address: 13.111.4.231
[*] --------------------------------------------------
[*] Host: mta.email.tesla.com
[*] Ip_Address: 13.111.14.190
[*] --------------------------------------------------
[*] Host: xmail.tesla.com
[*] Ip_Address: 204.74.99.100
[*] --------------------------------------------------
[*] Host: comparison.tesla.com
[*] Ip_Address: 64.125.183.133
[*] --------------------------------------------------
[*] Host: apacvpn.tesla.com
[*] Ip_Address: 8.244.67.215
[*] --------------------------------------------------
[*] Host: cnvpn.tesla.com
[*] Ip_Address: 103.222.41.215
[*] --------------------------------------------------
[*] Host: emails.tesla.com
[*] Ip_Address: 13.111.18.27
[*] --------------------------------------------------
[*] Host: mta2.emails.tesla.com
[*] Ip_Address: 13.111.88.1
[*] --------------------------------------------------
[*] Host: mta3.emails.tesla.com
[*] Ip_Address: 13.111.88.2
[*] --------------------------------------------------
[*] Host: mta4.emails.tesla.com
[*] Ip_Address: 13.111.88.52
[*] --------------------------------------------------
[*] Host: mta5.emails.tesla.com
[*] Ip_Address: 13.111.88.53
[*] --------------------------------------------------
[*] Host: mta.emails.tesla.com
[*] Ip_Address: 13.111.62.118
[*] --------------------------------------------------
[*] Host: click.emails.tesla.com
[*] Ip_Address: 13.111.48.179
[*] --------------------------------------------------
[*] Host: view.emails.tesla.com
[*] Ip_Address: 13.111.49.179
[*] --------------------------------------------------
[*] Host: itanswers.tesla.com
[*] Ip_Address: 204.74.99.100
[*] --------------------------------------------------
[*] Host: events.tesla.com
[*] Ip_Address: 13.111.47.195
[*] --------------------------------------------------
[*] Host: www-uat.tesla.com
[*] Ip_Address: 199.66.9.47
[*] --------------------------------------------------
[*] Host: shop.eu.tesla.com
[*] Ip_Address: 205.234.27.221
[*] --------------------------------------------------
[*] Host: mfamobile-dev.tesla.com
[*] Ip_Address: 205.234.27.209
[*] --------------------------------------------------
[*] Host: mfauser-dev.tesla.com
[*] Ip_Address: 205.234.27.209
[*] --------------------------------------------------


-------
SUMMARY
-------
[*] 35 total (35 new) hosts found.

#### Show hosts

Now we have begun to populate our hosts. Typing `show hosts` will give you a summary of the resources discovered.

[recon-ng][default][hackertarget] > show hosts
 +----------------------------------------------------------------------------------------------------------------------+
  | rowid |            host         |    ip_address   | region | country | latitude | longitude | notes |    module    |
  +----------------------------------------------------------------------------------------------------------------------+
  | 1   | tesla.com                 | 104.119.104.74  |        |         |          |           |       | hackertarget |
  | 2   | o7.ptr6980.tesla.com      | 149.72.144.42   |        |         |          |           |       | hackertarget |
  | 3   | vpn1.tesla.com            | 8.45.124.215    |        |         |          |           |       | hackertarget |
  | 4   | apacvpn1.tesla.com        | 8.244.131.215   |        |         |          |           |       | hackertarget |
  | 5   | cnvpn1.tesla.com          | 114.141.176.215 |        |         |          |           |       | hackertarget |
  | 6   | vpn2.tesla.com            | 8.47.24.215     |        |         |          |           |       | hackertarget |
  | 7   | model3.tesla.com          | 205.234.27.221  |        |         |          |           |       | hackertarget |
  | 8   | o3.ptr1444.tesla.com      | 149.72.152.236  |        |         |          |           |       | hackertarget |
  | 9   | o2.ptr556.tesla.com       | 149.72.134.64   |        |         |          |           |       | hackertarget |
  | 10  | o5.ptr8466.tesla.com      | 149.72.172.170  |        |         |          |           |       | hackertarget |
  | 11  | o6.ptr9437.tesla.com      | 168.245.123.10  |        |         |          |           |       | hackertarget |
  | 12  | o4.ptr1867.tesla.com      | 149.72.163.58   |        |         |          |           |       | hackertarget |
  | 13  | marketing.tesla.com       | 13.111.47.196   |        |         |          |           |       | hackertarget |
  | 14  | o1.ptr2410.link.tesla.com | 149.72.247.52   |        |         |          |           |       | hackertarget |
  | 15  | referral.tesla.com        | 72.10.32.90     |        |         |          |           |       | hackertarget |
  | 16  | mta2.email.tesla.com      | 13.111.4.231    |        |         |          |           |       | hackertarget |
  | 17  | mta.email.tesla.com       | 13.111.14.190   |        |         |          |           |       | hackertarget |
  | 18  | xmail.tesla.com           | 204.74.99.100   |        |         |          |           |       | hackertarget |
  | 19  | comparison.tesla.com      | 64.125.183.133  |        |         |          |           |       | hackertarget |
  | 20  | apacvpn.tesla.com         | 8.244.67.215    |        |         |          |           |       | hackertarget |
  | 21  | cnvpn.tesla.com           | 103.222.41.215  |        |         |          |           |       | hackertarget |
  | 22  | emails.tesla.com          | 13.111.18.27    |        |         |          |           |       | hackertarget |
  | 23  | mta2.emails.tesla.com     | 13.111.88.1     |        |         |          |           |       | hackertarget |
  | 24  | mta3.emails.tesla.com     | 13.111.88.2     |        |         |          |           |       | hackertarget |
  | 25  | mta4.emails.tesla.com     | 13.111.88.52    |        |         |          |           |       | hackertarget |
  | 26  | mta5.emails.tesla.com     | 13.111.88.53    |        |         |          |           |       | hackertarget |
  | 27  | mta.emails.tesla.com      | 13.111.62.118   |        |         |          |           |       | hackertarget |
  | 28  | click.emails.tesla.com    | 13.111.48.179   |        |         |          |           |       | hackertarget |
  | 29  | view.emails.tesla.com     | 13.111.49.179   |        |         |          |           |       | hackertarget |
  | 30  | itanswers.tesla.com       | 204.74.99.100   |        |         |          |           |       | hackertarget |
  | 31  | events.tesla.com          | 13.111.47.195   |        |         |          |           |       | hackertarget |
  | 32  | www-uat.tesla.com         | 199.66.9.47     |        |         |          |           |       | hackertarget |
  | 33  | shop.eu.tesla.com         | 205.234.27.221  |        |         |          |           |       | hackertarget |
  | 34  | mfamobile-dev.tesla.com   | 205.234.27.209  |        |         |          |           |       | hackertarget |
  | 35  | mfauser-dev.tesla.com     | 205.234.27.209  |        |         |          |           |       | hackertarget |
  +----------------------------------------------------------------------------------------------------------------------+

[*] 35 rows returned     

[recon-ng][default][hackertarget] > 

--------------------------------------------------------------

## Add API keys to Recon-ng

It is a simple matter to add API keys to recon-ng. [Shodan](https://www.shodan.io/) with a PRO account is a highly recommended option. This will enable queries to open ports on your discovered hosts without sending any packets to the target systems.

### How to add shodan API key

Create or login to your Shodan account, Go to 'Account" in top right corner. The API Key is listed here on the Account Overview page.

Recon-ng shows the syntax to add an API key is below

[recon-ng][default] > keys add 
Adds/Updates a third party resource credential

Usage: keys add name value

[recon-ng][default] keys add shodan_api bbexampleapikey33 

## .recon-ng configuration files

When you install recon-ng on your machine, it creates a folder in your home directory called .recon-ng. Contained in this folder is `keys.db`. If you are upgrading from one version to another or changed computers, and have previous modules that require keys to work, copy this file from the old version on your system and move it on the new one. You do not have to start all over again.

test@test-desktop:~/.recon-ng$ ls

keys.db  
modules  
modules.yml  
workspaces

test@test-desktop:~/.recon-ng$ 

## Conclusion

Recon-ng is a powerful tool that can be further explored by viewing the list of modules. The `help` within the console is clear, and with a bit of playing around it won't take long to become an expert.

The rise of bug bounties allows you to play with new tools and explore Organizations' every expanding attack surface footprint. Have fun. Don't break the rules.

For a great overview on version 5 check out the [you tube](https://www.youtube.com/watch?v=WVEv7peHerw) video by Tim Tomes.

**article revised and updated Nov 2022

**Credit:** This information was adapted from an excellent guide on [HackerTarget](https://hackertarget.com/recon-ng-tutorial/). Be sure to check out the original post for more details.

# Crack Open the Secrets: Mastering Information Gathering with Recon-ng

Hello, guess what? I’ve got just the thing to help you get started on your cybersecurity journey! If you’re looking to up your information gathering game, you’ve come to the right place. I recently made a post on how to use Recon-ng, a powerful tool for gathering information and reconnaissance in cybersecurity.

But let’s be real, being a cybersecurity detective sounds pretty cool, right? It’s like you’re living in a spy movie! And with the right tools and knowledge, you can become a master of information gathering and protect yourself and your digital assets like a pro. So why not give it a shot and see what you can uncover? Who knows, you might just uncover some juicy secrets!

[**Information gathering**](https://www.tutorialspoint.com/ethical_hacking/ethical_hacking_reconnaissance.htm) (reconnaissance ) is the process of collecting and analyzing data from various sources on a target. It’s crucial for making informed decisions and avoiding assumptions or biases. Effective information gathering involves a systematic approach, clear goals, identifying reliable sources, evaluating information quality, and analyzing data to extract meaningful insights. It requires critical thinking, research skills, and the ability to ask appropriate questions and find answers to them using the right tools. In this post i will reveal to you how to use recon-ng as a pro to do a very effective _reconnaissance._Let’s get started!

> **Recon-ng** is a powerful open-source tool used for reconnaissance and information gathering in cybersecurity. It automates the process of collecting data from various sources, including search engines, social media platforms, and other online resources.Recon-ng has a wide range of capabilities, including subdomain enumeration, email harvesting, and OSINT (Open-Source Intelligence) gathering. It also supports various modules and plugins that can be customized to meet the user’s specific needs.

Recon-ng is a popular choice among cybersecurity professionals due to its user-friendly interface, ease of customization, and ability to automate the information gathering process. It can help identify potential vulnerabilities and threats, and aid in the development of effective security measures to protect against cyber attacks.

# Getting Started with Recon-ng

![](https://miro.medium.com/v2/resize:fit:700/1*u-YLidpAAeFURLJDxVGb5A.jpeg)

_A. Installation and setup_

This command installs Recon-ng on a Debian-based Linux system.

sudo apt-get install recon-ng

![](https://miro.medium.com/v2/resize:fit:700/1*r5NifKvDf8X91HdfXLdCpw.png)

I had it installed so you can see nothing no new installations were made

This command starts Recon-ng

recon-ng

![](https://miro.medium.com/v2/resize:fit:700/1*Be-Q6ZpcpWfGg-6C6NGQsA.png)

Recon-ng interface

_B. Basic commands and syntax_

1. **creating and interacting with workspaces**

Let’s create a workspace just like your office to work within , the command is

workspaces create workspace_name

replace workspace_name with your preferred name . The default workspace name is ‘default’

Let’s list the created workspaces , to list enter this command 👇🏽

workspaces list

![](https://miro.medium.com/v2/resize:fit:700/1*mCTwn89cXRLcHjXoVctiTw.png)

these are the workspace I created for my projects , you can create different workspace for different project.

Let’s load the demo workspace to work within it , to load any workspace enter 👇🏽

workspaces load workspace_name

Instead of **workspace_name** add the workspace name you wanna load, in my case ‘demo’ **Example: workspaces load demo**

To delete workspace just enter 👇🏽

workspaces remove workspace_name

you know what to do to the ‘workspace_name’ in the command right? good! let’s continue

**2. creating and interacting with snapshots**

> In Recon-ng, snapshots are used to save the current state of a workspace, which includes all modules, workspaces, and associated data. Snapshots allow you to save your progress and return to it later, or even share it with others

to do a snapshot enter this command 👇🏽

snapshots take workspace_name

Let’s list the snapshots

snapshots list

![](https://miro.medium.com/v2/resize:fit:700/1*koSSYFudgWSdcDxnmJ2a7g.jpeg)

screenshot for the snapshot I made on CEH workspace

Let’s load the snapshot

To load snapshots enter this command 👇🏽 using the name of the snapshot you made

snapshots snapshot_20230614022243.db

To remove snapshots enter this command

snapshots remove snapshot_20230614022243.db

**3. Dashboards**

Dashboard is used to see the summary of your activities on recon-ng

Here is the command to check for your work activity 👇🏽

dashboard

![](https://miro.medium.com/v2/resize:fit:700/1*OuIate4oU0F9PuYTlPWkJA.png)

summary of my activities on recon-ng

4. Shell

> In Recon-ng, the shell is used to execute various commands and modules to perform reconnaissance on a target. The shell provides a command-line interface where you can enter commands to interact with the framework and perform various operations such as scanning, fingerprinting, and information gathering. You can use the shell to load and run modules, configure options, and view the results of your reconnaissance. The shell is an essential part of Recon-ng, and it allows you to perform reconnaissance tasks efficiently and effectively.

To execute a shell enter

shell sh

i**nstead** of sh, enter the name your preferred

![](https://miro.medium.com/v2/resize:fit:700/1*ArCiYY4dRHWeV-LVJj9WNA.jpeg)

recon-ng shell

5. pdb

> Pdb stands for Python Debugger, and it is a built-in debugging module in Python that can be used in Recon-ng to debug code and modules. Pdb allows you to pause the execution of your Python code at any point and interactively inspect the state of the program, including the values of variables, the call stack, and the execution flow.
> 
> To use Pdb in Recon-ng, you can add the — pdb option to the run command when running a module. For example, if you want to run the google_site_web module with Pdb enabled, you would type run — pdb google_site_web.

6. db

> In Recon-ng, db is a command used to interact with the framework’s built-in database. The db command allows you to manipulate the data stored in the database, including adding, modifying, and deleting records.

Here are some examples of how you can use the db command in Recon-ng:

![](https://miro.medium.com/v2/resize:fit:700/1*c3U16dg-c4VQka-Eep1W6g.png)

you can perform a query on with db on recon-ng just as how you do for any database

Once you do db schema you see all this information in a database format

Now let’s add an insert port,

To insert something in db just enter

db insert ports  

Instead of port you could enter whatever you want.

Here is a list you can choose from

companies|contacts|credentials|domains|hosts|leaks|locations|netblocks|ports|profiles|pushpins|repositories|vulnerabilities

To delete any rows enter

db delete hosts

Instead of host enter what you want to delete

Let’s add notes in db

Do this 👇🏽 specify the tables and then enter the rows and the enter the change

db notes ports  

7. Index

Here is where we could know the information of the module.

## Example1:

Gathering information on all installed modules

index all  

Now, let’s index a specific module here it will be

index brute_hosts

![](https://miro.medium.com/v2/resize:fit:700/1*_B0-7h39GKW3sKj0tS4HXQ.png)

8.Marketplace

In the marketplace, we are going to install, remove, search, info and refresh modules

In the marketplace, we can install all recon tools. Most of the recon tools are available in the marketplace

Let’s search for a tool, to search just enter

marketplace search

![](https://miro.medium.com/v2/resize:fit:700/1*VpKLNmpq-m7QT9M5hvq9vg.png)

some modules available in the marketplace

Let’s search for a specific tool, to search a specific tool enter this command 👇🏽

marketplace search dns  
  

![](https://miro.medium.com/v2/resize:fit:700/1*QoBXCno_R-2NidRnkSPgMA.png)

Instead of DNS you enter whatever you want, you could enter nmap, or any other tool you

Okay, now let’s install the searched tool, to install any tool enter this command 👇🏽

marketplace install recon/companies-domains/whoxy_dns

![](https://miro.medium.com/v2/resize:fit:700/1*sJIueTIZwWY5DaEhSxkrJA.png)

the module has been installed , however it needs an API key to operate. we will cover this in the later part of the post

Instead of **recon/companies-domains/whoxy_dns** enter the tool you wanna install

To remove any installed tool enter

marketplace remove  recon/companies-domains/whoxy_dns 

9. Modules

> In Recon-ng, modules are the building blocks that perform specific tasks or operations related to reconnaissance. Modules are designed to automate common reconnaissance tasks, such as information gathering, footprinting, and vulnerability scanning, and can be used to gather information about targets, identify potential attack vectors, and assess the security posture of a system or network.

Now, let’s check for the installed tool in the marketplace, the tool will be saved in modules and to look for it enter this command

Modules search 

To load the module just enter 👇🏽

modules load recon/domains-contacts/whois_pocs

Instead of **recon/domains-contacts/whois_pocs** enter the tool you wanna load

Now let’s do info and look at the loaded module,

info  

Changing target

options unset SOURCE 

**Now we have unset the target, check your SOURCE there is nothing**

To add the target simply enter 👇🏽

options set SOURCE certifiedethicalhacker.com  

![](https://miro.medium.com/v2/resize:fit:700/1*OTZ7xqKz8D8ovUBDAd4awQ.jpeg)

the red highlight shows the commands to load a module and find its info and the green shows how to set and unset a domain for the module

**Now the new target is set (caution: do not use a domain you are not permitted to use , THIS POST IS FOR ACADEMIC PURPOSES ONLY)**

To run the set target just enter

run

![](https://miro.medium.com/v2/resize:fit:700/1*_K5laFpw7ImB983YFhTCNw.png)

the url doesnt have much info , its probably for demonstration purposes

10. keys

You should have noticed at the marketplace some tools asking for API keys.

So, to add the API key follow these step

> API keys are unique identifiers that grant access to an API (Application Programming Interface) service. To get an API key for a module, you typically need to follow these steps:
> 
> 1. Visit the website or documentation of the module’s API service.  
> 2. Look for the section on API keys or authentication.  
> 3. Follow the instructions to create an account or sign in to an existing account.  
> 4. Generate an API key, which may involve providing additional information or verifying your identity.  
> 5. Copy the API key and use it in your code to authenticate your requests to the API service.
> 
> Note that the exact process for obtaining API keys may vary depending on the module and API service you’re using. Additionally, some API services may charge fees for API access or have limits on the number of requests you can make with your API key.

Firstly you should install a module that has API key dependency and once installed , do this command and see what all tools require keys

keys list  

![](https://miro.medium.com/v2/resize:fit:700/1*oNo5wKheVznJFC4YVLYDxg.jpeg)

I created an account with shodan.org and thats how i got the API key for shodan_api

**I have installed these tools 👆 which requires API and one tool has API key.**

To add an API key just follow my steps 👇🏽

keys add whoxy_api 1234567890abcdefgh  

![](https://miro.medium.com/v2/resize:fit:700/1*umUQEJ2yRF_30FTbSv0Lkw.jpeg)

**Instead of whoxy_api add the module you want**

To remove an API key do it 👇🏽

keys remove builtwith_api 0000000000000000000000000000000  

11. Show

> In Recon-ng, the “show” command is used to display information about the available modules, workspaces, and other aspects of the framework.

Now to see any framework (eg. hosts) just enter 👇🏽

show hosts

12. **Hosting on local host with python**

Aside the show command you can also view your framwork on the web by hosting it on your localhost with python

cd /usr/share/recon-ng

![](https://miro.medium.com/v2/resize:fit:700/1*ZEW6IJcYeCln-mj0RFOD4g.png)

now use python to host it on your localhost

python3 recon-web

![](https://miro.medium.com/v2/resize:fit:700/1*AtGrNfaHh6oziWghjpF0Mw.png)

you can now copy the url (that’s [http://127.0.0.1:5000/](http://127.0.0.1:5000/) ) and paste it in your browser

![](https://miro.medium.com/v2/resize:fit:1920/1*4LK-1KG96eRqEaH47bN_SQ.png)

![](https://miro.medium.com/v2/resize:fit:1920/1*myzoq1annjsAXRCN7OIofA.png)

you can navigate through the web interface

🎉 Congratulations, fellow information gatherers! I just wanted to give a big shoutout to [EDUC8AFRICA Ghana](https://www.linkedin.com/company/educ8africaghana/) for helping me obtain the skills I need to succeed in my career! Their Ethical Hacker certification class was top-notch, and I learned so much from my facilitator, [Rahul Sharma](https://www.linkedin.com/in/rahulsharma07/), and coordinators [Newman Mortey](https://www.linkedin.com/in/newman-mortey/) and [Kennedy Sarpong](https://www.linkedin.com/in/kennsarp/). Thank you for the amazing opportunity to learn and grow!

🔍 In my latest post, I shared my top tips and tricks for using Recon-ng to gather information about a target. From setting up the framework to running scans and gathering valuable insights, I covered everything you need to know to become a pro at information gathering.

👨‍💻 With the power of Recon-ng at your fingertips, you’re now equipped with the tools and techniques to uncover valuable insights and gain a deeper understanding of your target. Whether you’re a security researcher, a penetration tester, or just someone curious about the world around you, Recon-ng is a powerful tool for gathering information and uncovering hidden gems.

👍 So, what are you waiting for? Dive in and start exploring the world of information gathering today! With the right tools and techniques, anyone can become a pro at gathering information and uncovering valuable insights.

**Credit:** This information was adapted from an excellent guide on [Medium](https://medium.com/@philapp25/crack-open-the-secrets-mastering-information-gathering-with-recon-ng-9fe2ad09db1e). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/pyDIppIJsgA?si=y93-La2ca2ClUsr1" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=pyDIppIJsgA). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/i99v8lIOvFc?si=52ZDsPLLr1KXGD2S" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=i99v8lIOvFc). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/2No7NRP2taY?si=kFQDWnHdSt6RrXq5" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=2No7NRP2taY). Be sure to check out the original post for more details.

