#   
[![Arjun](https://camo.githubusercontent.com/308f696ff05afb8930e2b96feef371eafcb68d2c57d12604106e24ddc3f4d8d6/68747470733a2f2f696d6167652e6962622e636f2f633631386e712f61726a756e2e706e67)](https://github.com/s0md3v/Arjun)  
Arjun  

[](https://github.com/s0md3v/Arjun#--------arjun--)

#### HTTP Parameter Discovery Suite

[](https://github.com/s0md3v/Arjun#http-parameter-discovery-suite)

 [![](https://camo.githubusercontent.com/215d97a02efd1c63f08ce64c68b666e096887fbf28d332b337def463441cfcc7/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f72656c656173652f73306d6433762f41726a756e2e737667)](https://github.com/s0md3v/Arjun/releases) [![](https://camo.githubusercontent.com/436e58a1259b4a990908f142d0992de02985e493c6d1fadf84c6c4505a74b669/68747470733a2f2f696d672e736869656c64732e696f2f707970692f762f61726a756e2e737667)](https://pypi.python.org/pypi/arjun/) [![](https://camo.githubusercontent.com/8b516afca515d0e2c53beae0e06837a93e26546a0752cf44f1e79da1c91cd661/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f6973737565732d636c6f7365642d7261772f73306d6433762f41726a756e3f636f6c6f723d6461726b2d677265656e266c6162656c3d6973737565732532306669786564)](https://github.com/s0md3v/Arjun/issues?q=is%3Aissue+is%3Aclosed)[![](https://camo.githubusercontent.com/b13c039b10611ad7c9094994b2a32f9447f39de7cb013dd374ee303bf8edcd87/68747470733a2f2f696d672e736869656c64732e696f2f7472617669732f636f6d2f73306d6433762f41726a756e2e7376673f636f6c6f723d6461726b2d677265656e266c6162656c3d7465737473)](https://travis-ci.com/s0md3v/Arjun)

[![demo](https://camo.githubusercontent.com/a11caa567b0e2b8fe70ad3c928870aa346082c8d1400edcffafd805449c7f2a5/68747470733a2f2f692e6962622e636f2f7033564b53524a2f61726a756e2d64656d6f2e706e67)](https://camo.githubusercontent.com/a11caa567b0e2b8fe70ad3c928870aa346082c8d1400edcffafd805449c7f2a5/68747470733a2f2f692e6962622e636f2f7033564b53524a2f61726a756e2d64656d6f2e706e67)

### What's Arjun?

[](https://github.com/s0md3v/Arjun#whats-arjun)

Arjun can find query parameters for URL endpoints. If you don't get what that means, it's okay, read along.

Web applications use parameters (or queries) to accept user input, take the following example into consideration

`http://api.example.com/v1/userinfo?id=751634589`

This URL seems to load user information for a specific user id, but what if there exists a parameter named `admin` which when set to `True` makes the endpoint provide more information about the user?  
This is what Arjun does, it finds valid HTTP parameters with a huge default dictionary of 25,890 parameter names.

The best part? It takes less than 10 seconds to go through this huge list while making just 50-60 requests to the target. [Here's how](https://github.com/s0md3v/Arjun/wiki/How-Arjun-works%3F).

### Why Arjun?

[](https://github.com/s0md3v/Arjun#why-arjun)

- Supports `GET/POST/POST-JSON/POST-XML` requests
- Automatically handles rate limits and timeouts
- Export results to: BurpSuite, text or JSON file
- Import targets from: BurpSuite, text file or a raw request file
- Can passively extract parameters from JS or 3 external sources

### Installing Arjun

[](https://github.com/s0md3v/Arjun#installing-arjun)

You can install `arjun` with pip as following:

```
pip3 install arjun
```

or, by downloading this repository and running

```
python3 setup.py install
```

### How to use Arjun?

[](https://github.com/s0md3v/Arjun#how-to-use-arjun)

A detailed usage guide is available on [Usage](https://github.com/s0md3v/Arjun/wiki/Usage) section of the Wiki.

Direct links to some basic options are given below:

- [Scan a single URL](https://github.com/s0md3v/Arjun/wiki/Usage#scan-a-single-url)
- [Import targets](https://github.com/s0md3v/Arjun/wiki/Usage#import-multiple-targets)
- [Export results](https://github.com/s0md3v/Arjun/wiki/Usage#save-output-to-a-file)
- [Use custom HTTP headers](https://github.com/s0md3v/Arjun/wiki/Usage#use-custom-http-headers)

Optionally, you can use the `--help` argument to explore Arjun on your own.

##### Credits

[](https://github.com/s0md3v/Arjun#credits)

The parameter names wordlist is created by extracting top parameter names from [CommonCrawl](http://commoncrawl.org/) dataset and merging best words from [SecLists](https://github.com/danielmiessler/SecLists) and [param-miner](https://github.com/PortSwigger/param-miner) wordlists into that.  
`db/special.json` wordlist is taken from [data-payloads](https://github.com/yehgdotnet/data-payloads).

**Credit:** This information was adapted from an excellent guide on [GitHub](https://github.com/s0md3v/Arjun). Be sure to check out the original post for more details.

# Hacker tools: Arjun – The parameter discovery tool

By intigriti

May 17, 2021

![](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAoHBwgHBgoICAgLCgoXDhgVDg0XFhUPFhEdFxsdHSIVFhomHysjJh0oHSEiJDUlKC0vMjIyHSI4PTcwPCsxMi8BCgsLDg0OHBANHDsmFiU7Ly8vLy8vNTU1Ly81Ly8vLy8vLzUvLy8vLy8vLy8vNTUvLy8vLy8vLy8vLy8vLy8vL//AABEIABgAGAMBIgACEQEDEQH/xAAaAAACAgMAAAAAAAAAAAAAAAAABQYHAQIE/8QAHBAAAgMBAQEBAAAAAAAAAAAAAQIAAwQRBTEh/8QAFwEBAAMAAAAAAAAAAAAAAAAAAQADBP/EABYRAQEBAAAAAAAAAAAAAAAAAAASE//aAAwDAQACEQMRAD8AqSrLou0gBT3saWeFscAhTN/P1BdYJAkoT1KwOED5N0GEAvx6stpDIwMI/wDW3o+g8UTEMzBBVY6XAg/sYpptLfYQlqOHSzteewhCQv/Z)![Hacker tools: Arjun – The parameter discovery tool](https://www.datocms-assets.com/85623/1719639661-intigriti_blog_tools_spotlight_3.png?auto=format)

_Time is money, and certainly when it comes to bug bounty! Good tools can help you find bugs before others do – but only if you know how to properly use them._  
_Today, we are reviewing a parameter discovery tool called Arjun._

Arjun is a command-line tool specifically designed to look for hidden HTTP parameters. Today’s web applications have lots of parameters to make an application dynamic. Arjun will try to discover those parameters and give you a new set of endpoints to test on.

By default, Arjun makes use of a default wordlist but this can be modified by the user. It is a multi-threaded application, can handle rate limiting, allows input of custom headers, and most importantly, supports GET, POST, XML, and JSON methods.

![](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSI0OTMiIGhlaWdodD0iMTQ3Ij48L3N2Zz4=)![](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAoHBwgHBg8ICAgLFgoODg0QCw0ZDhENFhEOFxUZGBYTFhUaHysjGh0oHRUWJDUlKC0vMjIyGSI4PTcwPCsxMi8BCgsLDg0OGg0RHDscFh0vLy8vLy87Ly8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vL//AABEIAAgAGAMBIgACEQEDEQH/xAAYAAEAAwEAAAAAAAAAAAAAAAAAAwUHAf/EABoQAAIDAQEAAAAAAAAAAAAAAAADAQIEERL/xAAWAQEBAQAAAAAAAAAAAAAAAAACAQD/xAAWEQEBAQAAAAAAAAAAAAAAAAAAAhL/2gAMAwEAAhEDEQA/AM3bl3Pr2Stfm0JnlgAtMovDZqdAKeX/2Q==)![0-2](https://www.datocms-assets.com/85623/1719571926-0-2.png?auto=format)

## The installation

**Installing python3:**

Arjun needs **python 3.4** or higher to work properly. Check if you have the correct python version installed with _python3 -V._ If this version is not installed you can install it with the following command.

```
apt-get install python3
```

![](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSI2MDIiIGhlaWdodD0iODgiPjwvc3ZnPg==)![](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAoHBwgHBgoICAgLCgoLGhgQDg0NDhEVFRUdHRUZGCITFhUaKysjGh0oHRUWJDUlKC0vMjIyGSI4PTcwPCsxMi8BCgsLDgUOFRAFEC8cFhwvLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vL//AABEIAAQAGAMBIgACEQEDEQH/xAAWAAEBAQAAAAAAAAAAAAAAAAAABQb/xAAaEAACAwEBAAAAAAAAAAAAAAAAAQIDEQRx/8QAFQEBAQAAAAAAAAAAAAAAAAAAAgD/xAAUEQEAAAAAAAAAAAAAAAAAAAAA/9oADAMBAAIRAxEAPwDJNJrCX08tUpNtPfQBElW1Rjbi0AEn/9k=)![1-1](https://www.datocms-assets.com/85623/1719571789-1-1.png?auto=format)

```
python -V
```

![](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSI2MDkiIGhlaWdodD0iNDkiPjwvc3ZnPg==)![](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAoHBwgPBgoNCAgLCg0FDhgFBQ0ODhIMDQUMFxMZGBYTFhUaHysjGh0oHRUWJDUlKC0vMjIyGSI4PTcwPCsxMi8BCgsLBQUFEAUFEC8cFhwvLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vL//AABEIAAIAGAMBIgACEQEDEQH/xAAXAAEAAwAAAAAAAAAAAAAAAAAAAgUH/8QAGhABAAEFAAAAAAAAAAAAAAAAAEIBAwUyM//EABUBAQEAAAAAAAAAAAAAAAAAAAIA/8QAFBEBAAAAAAAAAAAAAAAAAAAAAP/aAAwDAQACEQMRAD8AzvK8lNb1qBClEBJ//9k=)![2-1](https://www.datocms-assets.com/85623/1719571794-2-1.png?auto=format)

**Installing Arjun:**

Arjun is being actively developed by **s0md3v** at his Git [https://github.com/s0md3v/Arjun](https://github.com/s0md3v/Arjun). We will download and install the latest version from the git and go from there.

```
git clone https://github.com/s0md3v/Arjun
```

![](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSI2MTUiIGhlaWdodD0iMTY5Ij48L3N2Zz4=)![](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAoHBwgHBgoICAgLCgoLDhEYDg0VGCIVFhEYFxUZGBYTFhUaHysjGh0oHSEWJDUlKC0vMjIyGSI4PTcwPCsxMi8BCgsLDg0FEBAQEC8cFhwvLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vL//AABEIAAcAGAMBIgACEQEDEQH/xAAXAAEBAQEAAAAAAAAAAAAAAAAABgQB/8QAGhAAAgMBAQAAAAAAAAAAAAAAAAECAwQhEf/EABUBAQEAAAAAAAAAAAAAAAAAAAIA/8QAFBEBAAAAAAAAAAAAAAAAAAAAAP/aAAwDAQACEQMRAD8AlVngodRl11UyqacTgCSevy0qT8QAJP/Z)![3-1](https://www.datocms-assets.com/85623/1719571934-3-1.png?auto=format)

Change the directory to Arjun and run the **setup.py** with the command below. If you encounter the error: **_“ModuleNotFoundError: No module named ‘setuptools’”_** you first need to install python3-setuptools (**_apt-get install python3-setuptools_**).

```
python3 setup.py install
```

![](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSI3NDUiIGhlaWdodD0iMjEwIj48L3N2Zz4=)![](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAoHBwgHBgoICAgLDQ4LFRoQDhYMDhUNDRENFxMZGBYTFhUaHysjGh0oHRUWJDUlKC0vMjIyGSI4PTcwPCsxMi8BCgsLDg0OEBAQEi8cFhwvLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vL//AABEIAAcAGAMBIgACEQEDEQH/xAAWAAEBAQAAAAAAAAAAAAAAAAAABQb/xAAaEAADAAMBAAAAAAAAAAAAAAAAAQMCBCES/8QAFgEBAQEAAAAAAAAAAAAAAAAAAgEA/8QAFBEBAAAAAAAAAAAAAAAAAAAAAP/aAAwDAQACEQMRAD8Ax9faXGTd+lsJ8YAiRqbFsl1gAyP/2Q==)![4-1](https://www.datocms-assets.com/85623/1719571940-4-1.png?auto=format)

Now that Arjun is installed we can use it by just typing “arjun”. It should be located at **/usr/local/bin/arjun**. To check all the options we will use the (**-h**) flag.

![](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxMDQ0IiBoZWlnaHQ9IjQ4MiI+PC9zdmc+)![](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAoHBwgHBhYIEAgJDg0NDhINCQ0NDRENDRENFx8ZGBYTFhUaHysjGh0oHRUWJDUlKC0vMjIyGSI4PTcwPCsxMi8BCgsLBQUFEAUFEC8cFhwvLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vL//AABEIAAwAGAMBIgACEQEDEQH/xAAXAAEAAwAAAAAAAAAAAAAAAAAEAAEG/8QAGxAAAgIDAQAAAAAAAAAAAAAAAAECAwQTMRH/xAAVAQEBAAAAAAAAAAAAAAAAAAACAP/EABQRAQAAAAAAAAAAAAAAAAAAAAD/2gAMAwEAAhEDEQA/AMBBtWA8y1xtHVpbA2dFbOBIKeQyElBe8LJP/9k=)![5-1](https://www.datocms-assets.com/85623/1719571947-5-1.png?auto=format)

## The Basics

To understand Arjun, we need to know what HTTP parameters are. HTTP parameters are query strings that are part of a URL that accepts user input. For example:

```
http://server.com/page?id=1
```

When the server receives the request, it will process the query and return the page with “id” 1. In this example the “id” is the HTTP parameter. It’s also possible there are multiple parameters, or even hidden parameters that are not known by the user. Here is were Arjun comes into play. The tool will try to discover unknown parameters by the use of a wordlist.

Lets start with the very basic command and providing a single URL with the (**-u**) flag.

```
arjun -u http://server.com/page/
```

![](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSI1MjMiIGhlaWdodD0iMjIwIj48L3N2Zz4=)![](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAoHBwgHBgoICAgLDRYPDhIQDg8WDhEhFg0YFxMaGBYVIhUaHyslGh0oHRUWJTUlKC0vMjIyGSI4PTcwPCsxMi8BCgsLDg0OFhEQHDscHRwvLzUvLy87LzUvLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vL//AABEIAAsAGAMBIgACEQEDEQH/xAAZAAACAwEAAAAAAAAAAAAAAAAEBgEDBwD/xAAeEAACAQMFAAAAAAAAAAAAAAAAAQIFETIDBBIxM//EABUBAQEAAAAAAAAAAAAAAAAAAAEC/8QAFhEBAQEAAAAAAAAAAAAAAAAAAAEC/9oADAMBAAIRAxEAPwDO50K8OyiVB4QbbGSWAPuPFkwYhT1Ni4OyZwZrZskTX//Z)![6-1](https://www.datocms-assets.com/85623/1719571954-6-1.png?auto=format)

Arjun will analyze the page and will search for potential hidden HTTP parameters.

You can also specify the method by providing it to the Arjun with the (**-m**) parameter. Possible methods are:  GET,POST,XML,JSON. By default it will use the GET method.

```
arjun -u http://server.com/page/ -m POST
```

![](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSI1MzciIGhlaWdodD0iMjI0Ij48L3N2Zz4=)![](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAoHBwgHBhIOCAgLDw8NDg0OBwcMDhENDQgYFxMZGBYTFhUaHysjGh0oHSEWJDUlKC0vMjIyGSI4PTcwPCsxMi8BCgsLBQoNFQoQEC8cFhwvLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vL//AABEIAAsAGAMBIgACEQEDEQH/xAAZAAABBQAAAAAAAAAAAAAAAAAGAAIDBQf/xAAeEAACAgEFAQAAAAAAAAAAAAABAwACMhETMUFCBP/EABUBAQEAAAAAAAAAAAAAAAAAAAIA/8QAFBEBAAAAAAAAAAAAAAAAAAAAAP/aAAwDAQACEQMRAD8Azlq2i+Jkdw4eTCJi6bmIjHrppiIRC79w9RS0+ildeBFJP//Z)![7](https://www.datocms-assets.com/85623/1719571960-7.png?auto=format)

More powerful is using a list of URLs that we feed Arjun with the **(-i**) flag.

```
arjun -i urls
```

![](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSI1ODgiIGhlaWdodD0iNDczIj48L3N2Zz4=)![](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAoHBwgHBhYQEwgNEA0WDg0NDgYNDhEJFhENFxMZGBYTFhUaHysjGh0oHSEWJDUlKC0vMjIyGSI4PTcwPCsxMi8BCgsLDg0OEA4NEC8cFh0vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vL//AABEIABQAGAMBIgACEQEDEQH/xAAZAAEBAAMBAAAAAAAAAAAAAAAABQMEBwL/xAAcEAACAgMBAQAAAAAAAAAAAAAAAgEDBBIxURH/xAAVAQEBAAAAAAAAAAAAAAAAAAAAAv/EABQRAQAAAAAAAAAAAAAAAAAAAAD/2gAMAwEAAhEDEQA/AOePh3SpinDtVCtLWfOGG1nlOEpQnps2Bs3Q8SAK6u0x08XNOoAEvJefQAB//9k=)![8](https://www.datocms-assets.com/85623/1719571970-8.png?auto=format)

Like all other tools, the power of finding things that are not found before is using your own custom lists. You can provide your own parameter list with the (**-w**) flag.

```
arjun -u http://server.com/page/ -w parameters.txt
```

## **Other interesting flags**

**Threading**:

By default arjun will handle 2 threads, but we can increase this with the (**-t**) flag.

```
arjun -u http://server.com/page/ -t 20
```

**Delaying between requests**:

Some bounty programs require you to set a limit on your requests. With the (**-d**) flag we can set a delay on our requests. ( **this is in seconds** )

```
arjun -u http://server.com/page/ -d 2
```

**Saving to files:**

You can save your results in 2 ways. One is in JSON format (**-o or -oJ**) and the other way is in text format (**-oT**)

```
Arjun -i urls -oJ results.json
```

![](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSI4ODkiIGhlaWdodD0iMzI1Ij48L3N2Zz4=)![](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAoHBwgHBgoSCAgLEAoVDiQVDA0NDhoODRUYFxYZGBYVFhUaHysjGh0oHRUWJDUlKC0vMjIyGSI4PTcwPCsxMi8BCgsLDg0PFRAKEy8oFhwvLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vLy8vL//AABEIAAkAGAMBIgACEQEDEQH/xAAZAAACAwEAAAAAAAAAAAAAAAAEBQEDBwD/xAAfEAACAQIHAAAAAAAAAAAAAAAAAQMEIgIREhMxNEH/xAAVAQEBAAAAAAAAAAAAAAAAAAABAP/EABURAQEAAAAAAAAAAAAAAAAAAAAR/9oADAMBAAIRAxEAPwDPYJKdUzzYvmdG8TuK8PXYvfLEjZNjRayAPw4lX//Z)![9](https://www.datocms-assets.com/85623/1719571977-9.png?auto=format)

**Including data:**

Arjun can detect parameters in a specified location when using JSON or XML method parameters by default by adding **$arjun$.** If you want to send specific data with every request you can do this with the **(–include**) flag.

```
Arjun -u http://server.com/page/ --include ‘{“api_key”:”xxxxx”}’
OR
Arjun -u http://server.com -m XML --include='<?xml><root>$arjun$</root>'
```

**Adding headers:**

When we want to add specific headers, or test on a authenticated endpoint, we can make use of the **(–headers**) flag. If we don’t provide a string after the headers flag, the default text editor will open where we can past our headers.

```
Arjun -u http://server.com/page/ --headers ‘Cookie: PHPSESSID=xxxx’
```

## Conclusion

Arjun is a tool that can expose hidden parameters, what will lead to a greater attack surface. You can easily chain this tool in your automation by providing it a list of URLs and send the output to a json file to be used by another tool. This was a short article describing the most useful flags of Arjun. I hope you enjoyed it and see you next time.

**Credit:** This information was adapted from an excellent guide on [Intigriti](https://blog.intigriti.com/hacking-tools/hacker-tools-arjun-the-parameter-discovery-tool). Be sure to check out the original post for more details.

# Arjun – Hidden HTTP Parameter Discovery Suite in Kali Linux

Last Updated : 30 Jun, 2021

When a security researcher tries to hack a web application to test the security of a web application, sometimes it becomes a challenging task due to the sheer amount of moving parts they possess. The web applications use HTTP requests and parameters for GET and POST methods. But sometimes developers of web applications conceal these details from the user due to internal security reasons for the web applications. However, Arjun is a tool that can help security researchers in such situations. This tool helps security researchers to discover hidden HTTP parameters in web applications. HTTP parameters are also called query strings, which you see in the URL bar. The following is an example of an HTTP parameter.

http://site.com/name?id=1

**Arjun** is an Indian bug bounty tool. The Arjun tool is famous for finding query parameters for URL endpoints on the links of websites and web apps. This tool is a lightweight tool and can find parameters in 10 seconds by just making 20-40 requests to the target domain. This tool has an in-built default dictionary of 10,985 parameter names, which makes it more powerful to find query parameters in URL. This tool provides a command-line interface that you can run on Kali Linux. This tool can be used to get information about our target(domain), which can be a website or an IP address. The interactive console provides a number of helpful features, such as command completion and contextual help.

![](https://media.geeksforgeeks.org/wp-content/uploads/20210612164802/9.PNG)

### Installation 

**Step 1:** Open your kali Linux operating system and use the following command to install the tool. After installing the tool, you have to move into the directory of the tool using the second command. To list out the contents of the directory, use the third command that is given below.

git clone https://github.com/s0md3v/Arjun.git
cd Arjun
ls -l

![](https://media.geeksforgeeks.org/wp-content/uploads/20210612164018/6.PNG)

**Step 2:** The tool has been downloaded successfully. Now use the following command to install the tool.

python3 setup.py install

![](https://media.geeksforgeeks.org/wp-content/uploads/20210612164421/7.PNG)

**Step 3:** The tool has been installed successfully. Now use the following command to run the tool.

arjun -h

![](https://media.geeksforgeeks.org/wp-content/uploads/20210612164533/8.PNG)

The help menu of the tool is opened. The tool is running successfully. Now let’s see some examples which will show usages of the tool.

### Usage

**Example 1:** Use the arjun tool to find the endpoints of a URL.

arjun -u http://testphp.vulnweb.com/listproducts.php

![](https://media.geeksforgeeks.org/wp-content/uploads/20210612164802/9.PNG)

The tool giving all the information above can be useful for a security researcher.

**Example 2:** Use the arjun tool to find the endpoints of a URL with the -u flag.

arjun -u http://testphp.vulnweb.com/listproducts.php -o new.json

And to search for JSON parameters, use the –json option or new.json option with -o flag

![](https://media.geeksforgeeks.org/wp-content/uploads/20210612165627/10.PNG)![](https://media.geeksforgeeks.org/wp-content/uploads/20210612165846/11.PNG)

**Example 3:** Use the arjun tool to find the endpoints of a URL with -u flag with the heuristic scanner.

arjun -u http://google.com

The -u flag is the simple way to run the tool. You have to apply the -u URL to the tool with the valid URL.

![](https://media.geeksforgeeks.org/wp-content/uploads/20210618140724/13.PNG)

**Example 4:** Use the arjun tool to find endpoints of a URL with -u flag and thread drag.

arjun -u http://google.com -t 5

![](https://media.geeksforgeeks.org/wp-content/uploads/20210618141253/14.PNG)


**Credit:** This information was adapted from an excellent guide on [GeeksForGeeks](https://www.geeksforgeeks.org/arjun-hidden-http-parameter-discovery-suite-in-kali-linux/). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/jm7QFm12naE?si=MiemHvgi9BP4_1U0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=jm7QFm12naE). Be sure to check out the original post for more details.

<iframe width="560" height="315" src="https://www.youtube.com/embed/TtzKrTKkTgs?si=LH4K2itcU2ZjpWLa" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**Credit:** This information was adapted from an excellent guide on [YouTube](https://www.youtube.com/watch?v=TtzKrTKkTgs). Be sure to check out the original post for more details.


