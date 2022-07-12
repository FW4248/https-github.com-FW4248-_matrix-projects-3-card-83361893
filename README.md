#
`[!-d\{"->(!fill)<-":"->[+!--rw+wroo+d\](thispage%fill!)<-~"}`## </
     
                   
		   

# Git Credential Manager for Windows

[![GitHub Release](https://img.shields.io/github/release/microsoft/git-credential-manager-for-windows.svg?style=flat-square)](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases)
[![Build status](https://img.shields.io/appveyor/ci/whoisj/git-credential-manager-for-windows.svg?style=flat-square)](https://ci.appveyor.com/project/whoisj/git-credential-manager-for-windows/branch/master)
[![Coverity Scan Build Status](https://img.shields.io/coverity/scan/11371.svg?style=flat-square)](https://scan.coverity.com/projects/git-credential-manager-for-windows)
[![GitHub Downloads](https://img.shields.io/github/downloads/Microsoft/Git-Credential-Manager-for-Windows/total.svg?style=flat-square)](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases)
[![@MicrosoftGit on Twitter](https://img.shields.io/twitter/follow/microsoftgit.svg?style=social&label=Follow%20%40microsoftgit)](https://twitter.com/microsoftgit)

### Additional Resources

* [Credential Manager Usage](Docs/CredentialManager.md)
* [Askpass Usage](Docs/Askpass.md)
* [Configuration Options](Docs/Configuration.md)
* [Build Agent and Automation Support](Docs/Automation.md)
* [Bitbucket Specific Details](Docs/Bitbucket.md)
* [Frequently Asked Questions](Docs/Faq.md)
* [Development
* * *

## NOTICE: This project is no longer being maintained. :warning:

Git Credential Manager for Windows is no longer being maintained. The cross-platform
[Git Credential Manager Core (GCM Core)](https://aka.ms/gcmcore) is the official replacement.

GCM Core is included as an optional component of Git for Windows 2.28 and will be made the default credential
helper as of Git for Windows 2.29. GCM Core can also be manually installed from [this page](https://github.com/microsoft/Git-Credential-Manager-Core/releases/latest).

* * *

## NOTICE: Experiencing GitHub push/fetch problems?

[GitHub will disable password-based authentication](https://github.blog/changelog/2019-08-08-password-based-http-basic-authentication-deprecation-and-removal/)
on APIs Git Credential Manager for Windows uses to create tokens. As a result, GCM
for Windows will no longer be able to create new access tokens for GitHub.

[Git Credential Manager Core (GCM Core)](https://aka.ms/gcmcore) supports OAuth-based
authentication with GitHub and is the replacement for GCM for Windows.

Please update to Git for Windows 2.28 and select "Git Credential Manager Core" from
the installer when asked to "select a credential helper", or manually install GCM Core
from [here](https://github.com/microsoft/Git-Credential-Manager-Core/releases/latest).

---

As of 22 Feb 2018, [GitHub has disabled support for weak encryption](https://githubengineering.com/crypto-deprecation-notice/) which means many users will suddenly find themselves unable to authenticate using a Git for Windows which (impacts versions older than v2.16.0). **DO NOT PANIC**, there's a fix. [Update Git for Windows](https://github.com/git-for-windows/git/releases) to the latest (or at least v2.16.0).

The most common error users see looks like:

```text
fatal: HttpRequestException encountered.
   An error occurred while sending the request.
fatal: HttpRequestException encountered.
   An error occurred while sending the request.
Username for 'https://github.com':
```

If, after updating Git for Windows, you are still having problems authenticating with GitHub, please read this [Developer Community](https://developercommunity.visualstudio.com/content/problem/201457/unable-to-connect-to-github-due-to-tls-12-only-cha.html) topic which contains additional remedial actions you can take to resolve the problem.

If you are experiencing issue when using **Visual Studio**, please read **[Unable to connect to GitHub with Visual Studio](https://developercommunity.visualstudio.com/content/problem/201457/unable-to-connect-to-github-due-to-tls-12-only-cha.html)**.

* * *

The [Git Credential Manager for Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows) (GCM) provides secure Git credential storage for Windows. It's the successor to the [Windows Credential Store for Git](https://gitcredentialstore.codeplex.com/) (git-credential-winstore), which is no longer maintained. Compared to Git's built-in credential storage for Windows ([wincred](https://git-scm.com/book/en/v2/Git-Tools-Credential-Storage)), which provides single-factor authentication support working on any HTTP enabled Git repository, GCM provides multi-factor authentication support for [Azure DevOps](https://dev.azure.com/), [Team Foundation Server](Docs/Faq.md#q-i-thought-microsoft-was-maintaining-this-why-does-the-gcm-not-work-as-expected-with-tfs), GitHub, and Bitbucket.

This project includes:

* Secure password storage in the Windows Credential Store.
* Multi-factor authentication support for Azure DevOps.
* Two-factor authentication support for GitHub.
* Two-factor authentication support for Bitbucket.
* Personal Access Token generation and usage support for Azure DevOps, GitHub, and Bitbucket.
* Non-interactive mode support for Azure DevOps backed by Azure Directory.
* NTLM/Kerberos authentication for Team Foundation Server ([see notes](Docs/Faq.md#q-i-thought-microsoft-was-maintaining-this-why-does-the-gcm-not-work-as-expected-with-tfs)).
* Optional settings for [build agent optimization](Docs/Automation.md).

## Community

This is a community project so feel free to contribute ideas, submit bugs, fix bugs, or code new features. For detailed information on how the GCM works go to the [wiki](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/wiki/How-the-Git-Credential-Managers-works).

## Download and Install

To use the GCM, you can download the [latest installer](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest). To install, double-click `GCMW-{version}.exe` and follow the instructions presented.

When prompted to select your terminal emulator for Git Bash you should choose the Windows' default console window, or make sure GCM is [configured to use modal dialogs](Docs/Configuration.md#modalprompt). GCM cannot prompt you for credentials, at the console, in a MinTTY setup.

### Manual Installation

Note for users with special installation needs, you can still extract the `gcm-{version}.zip` file and run install.cmd from an administrator command prompt. This allows specification of the installation options explained below.

### Installation in an MSYS2 Environment

To use the GCM along with git installed with `pacman` in an MSYS2 environment, simply [download a release zip](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases) and extract the contents directly into `C:\msys64\usr\lib\git-core` (assuming your MSYS2 environment is installed in `C:\msys64`). Then run:

```shell
git config --global credential.helper manager
```

## How to use

You don't. It [magically](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/issues/31) works when credentials are needed. For example, when pushing to [Azure DevOps](https://dev.azure.com), it automatically opens a window and initializes an oauth2 flow to get your token.

### Build and Install from Sources

To build and install the GCM yourself, clone the sources, open the solution file in Visual Studio, and build the solution. All necessary components will be copied from the build output locations into a `.\Deploy` folder at the root of the solution. From an elevated command prompt in the `.\Deploy` folder issue the following command `git-credential-manager install`. Additional information about [development and debugging](Docs/Development.md) are available in our documents area.

[Various options](Docs/Configuration.md) are available for uniquely configured systems, like automated build systems. For systems with a **non-standard placement of Git** use the `--path <git>` parameter to supply where Git is located and thus where the GCM should be deployed to. For systems looking to **avoid checking for the Microsoft .NET Framework** and other similar prerequisites use the `--force` option. For systems looking for **silent installation without any prompts**, use the `--passive` option.

### Additional Resources

* [Credential Manager Usage](Docs/CredentialManager.md)
* [Askpass Usage](Docs/Askpass.md)
* [Configuration Options](Docs/Configuration.md)
* [Build Agent and Automation Support](Docs/Automation.md)
* [Bitbucket Specific Details](Docs/Bitbucket.md)
* [Frequently Asked Questions](Docs/Faq.md)
* [Development and Debugging](Docs/Development.md)

## Contribute

There are many ways to contribute.

* [Submit bugs](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/issues) and help us verify fixes as they are checked in.
* Review [code changes](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/pulls).
* Contribute bug fixes and features.

### Code Contributions

For code contributions, you will need to complete a Contributor License Agreement (CLA). Briefly, this agreement testifies that you grant us permission to use the submitted change according to the terms of the project's license, and that the work being submitted is under the appropriate copyright.

Please submit a Contributor License Agreement (CLA) before submitting a pull request. You may visit <https://cla.microsoft.com> to sign digitally. Alternatively, download the agreement [Microsoft Contribution License Agreement.pdf](https://cla.microsoft.com/cladoc/microsoft-contribution-license-agreement.pdf), sign, scan, and email it back to <cla@microsoft.com>. Be sure to include your GitHub user name along with the agreement. Once we have received the signed CLA, we'll review the request.

## Code of Conduct

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact <opencode@microsoft.com> with any additional questions or comments.

## License

This project uses the [MIT License](LICENSE.txt).


|[!SVG.(7)](https://user-images.githubusercontent.com/104608815/168705069-aa8b2cb7-12bf-4b2b-8801-3945b9e11084.jpeg)|

|[!SVG.(5)](https://user-images.githubusercontent.com/104608815/168705071-8740c61a-c171-41e3-98b8-b471c9e48b1e.jpeg)|

|[!SVG.(10)](https://user-images.githubusercontent.com/104608815/168705072-9e2b478c-901b-42c2-9a66-81dbc80c8410.png)|


/>``
# 1411275
1214984904900
Docs
ResourcesStart for free
DocsAPLREST API
Introduction
Data Types
Scalar Data Types
Null Values
Entities
Tabular Operators
Scalar Functions
Scalar Operators
Aggregation Functions
Scalar data types
Axiom Processing Language supplies a set of system data types that define all the types of data that can be used with APL

The following table lists the data types supported by APL, alongside additional aliases you can use to refer to them.

Type	Additional name(s)	gettype(|![images (8)](https://user-images.githubusercontent.com/104608815/168705073-705dc7cf-61e4-4faa-b4c3-f4ab08eeebb0.png)|.(scalar data types 023bc)
|:/
|![images (7)](https://user-images.githubusercontent.com/104608815/168705078-d25c41bf-7fe1-4bfe-920d-b7eceff7dd26.png)|.(1214984904900)

|![images (3)](https://user-images.githubusercontent.com/104608815/168705080-44a8f2ea-136e-44fd-9892-ec7ce0ffe77f.jpeg)|
)
bool(https://github.com/JetBrains/intellij-sdk-docs/pull/797#issue-1276706622)	boolean	int8
datetime(https://github.com/JetBrains/intellij-sdk-docs/pull/797#issue-1276706622)	date	datetime
dynamic(https://github.com/JetBrains/intellij-sdk-docs/pull/797#issue-1276706622)		array or dictionary or any other of the other values
int(https://github.com/JetBrains/intellij-sdk-docs/pull/797#issue-1276706622)	int has an alias long	int
long(https://github.com/JetBrains/intellij-sdk-docs/pull/797#issue-1276706622)		long
real(https://github.com/JetBrains/intellij-sdk-docs/pull/797#issue-1276706622)	double	real
string(https://github.com/JetBrains/intellij-sdk-docs/pull/797#issue-1276706622)		string
timespan(https://github.com/JetBrains/intellij-sdk-docs/pull/797#issue-1276706622)	time	timespan
The bool data type
The bool (boolean) data type can have one of two states: true or false (internally encoded as 1 and 0, respectively), as well as the null value.

bool literals
The bool data type has the following literals:

true and bool(true): Representing trueness
false and bool(false): Representing falsehood
null and bool(null): Representing the null value
bool operators
The bool data type supports the following operators: equality (==), inequality (!=), logical-and (and), and logical-or (or).

The datetime data type
The datetime (date) data type represents an instant in time, typically expressed as a date and time of day. Values range from 00:00:00 (midnight), January 1, 0001 Anno Domini (Common Era) through 11:59:59 P.M., December 31, 9999 A.D. (C.E.) in the Gregorian calendar.

datetime literals
Literals of type datetime have the syntax datetime (value), where a number of formats are supported for value, as indicated by the following table:

Example	Value
datetime(2019-11-30 23:59:59.9) datetime(2015-12-31)	Times are always in UTC. Omitting the date gives a time today.
datetime(📆)	Check out our null values
now(https://github.com/FW4248/_matrix/projects/3#card-83361893)	The current time.
now(-timespan)	now(https://github.com/FW4248/_matrix/projects/3#card-83361893)-timespan
ago(timespan)	now(https://github.com/FW4248/_matrix/projects/3#card-83361893)-timespan
now(📥💱📤) and ago(https://github.com/FW4248/_matrix/projects/3#card-83361893) indicate a datetime value compared with the moment in time when APL started to execute the query.

Supported formats
We support the ISO 8601 format, which is the standard format for representing dates and times in the Gregorian calendar.

ISO 8601
Format	Example
%Y-%m-%dT%H:%M:%s%z	2016-06-26T08:20:03.123456Z
%Y-%m-%dT%H:%M:%s	2016-06-26T08:20:03.123456
%Y-%m-%dT%H:%M	2016-06-26T08:20
%Y-%m-%d %H:%M:%s%z	2016-10-06 15:55:55.123456Z
%Y-%m-%d %H:%M:%s	2016-10-06 15:55:55
%Y-%m-%d %H:%M	2016-10-06 15:55
%Y-%m-%d	2014-11-08
The dynamic data type
The dynamic scalar data type is special in that it can take on any value of other scalar data types from the list below, as well as arrays and property bags. Specifically, a dynamic value can be:

null
A value of any of the primitive scalar data types: bool, datetime, int, long, real, string, and timespan.
An array of dynamic values, holding zero or more values with zero-based indexing.
A property bag, holding zero or more key-value pairs.
Dynamic literals
A literal of type dynamic looks like this:

dynamic (Value 01ab)

Value can be:

null, in which case the literal represents the null dynamic value: dynamic(null).
Another scalar data type literal, in which case the literal represents the dynamic literal of the "inner" type. For example, dynamic(6) is a dynamic value holding the value 6 of the long scalar data type.
An array of dynamic or other literals: [ListOfValues]. For example, dynamic([3, 4, "bye"]) is a dynamic array of three elements, two long values and one string value.
A property bag: {Name=Value ...}. For example, dynamic({"a":1, "b":{"a":2}}) is a property bag with two slots, a, and b, with the second slot being another property bag.
The int data type
The int data type represents a signed, 64-bit wide, integer.

The special form int(null) represents the null value.

int has an alias long

The long data type
The long data type represents a signed, 64-bit wide, integer.

long literals
Literals of the long data type can be specified in the following syntax:

long(Value)

Where Value can take the following forms:<div

One more or digits, in which case the literal value is the decimal representation of these digits. For example, long(11) is the number eleven of type long.
A minus (-) sign followed by one or more digits. For example, long(-3) is the number minus three of type long.
null, in which case this is the null value of the long data type. Thus, the null value of type long is long(null).
The real data type
The real data type represents a 64-bit wide, double-precision, floating-point number.

The string data type
The string data type represents a sequence of zero or more Unicode characters.

String literals
There are several ways to encode literals of the string data type in a query text:||--|![images (36)](https://user-images.githubusercontent.com/104608815/168704965-d9d9c116-cde7-4ac3-860a-0519e4914fcd.png)|
|;/
|![images (15)](https://user-images.githubusercontent.com/104608815/168705062-dd9638d1-39bc-4a5d-87a7-06cb3e1fc709.jpeg)|.(#dynamic values01ab)
|:/
|![images (17)](https://user-images.githubusercontent.com/104608815/168705064-59664023-ce89-4206-a464-390c2e29d4d0.png)|


Enclose the string in double-quotes
					      (
					   
					      [ |![images (9)](https://user-images.githubusercontent.com/104608815/168705068-882f5736-2e49-4f2b-b405-329c5328c7ea.jpeg)|]÷")\') require escaping by a backslash (\-d). Double quote characters (
					      ") do not require escaping.
In:
	
	the two representations above, the backslash (\) character indicates escaping. The backslash is used to escape the enclosing quote characters, tab characters (\t), newline characters (\n), and itself (\\).

Raw string literals
Raw string SL4A also jira
	 supported:  16 × 5=" html & luapage image body discuss";
>
Enclose in single-quotes('):
@'This is a raw string literal'
Raw strings are particularly useful for regexes where you can use 
@"^[\d]+$" instead of "^[\d]+$"

The timespan data type
The timespan (time) data type represents a time interval.

timespan literals
Literals of type timespan have the syntax timespan(value), where a number of formats are supported for value, as indicated by the following table:

Value	length of time
2d	2 days
1.5h	1.5 hour
30m	30 minutes
10s	10 seconds
timespan(15s)	
	15 seconds
0.1s	0.1 second
timespan(2d)	2 days

axiom logo
All Systems Operational
Resources
Documentation
Cloud
Enterprise
Platform
Start
Support
CLI
API Reference
Company
Home
Pricing
Blog
About
Careers
Contact Us
Legal
Privacy Policy
Terms of Service
Cookies
GDPR
SLA
Social
Slack Community
GitHub
Twitter

Copyright © 2022 Axiom, Inc. All rights reserved.


Scalar data types.(023bc)

	
	
	
	
	. In this form, the backslash character (\) stands for itself, and does not denote an escape sequence.

Enclosed in double-quotes(": "This is a string literal. Single quote characters (') don't require escaping. Double quote characters (\ -d
					     
					      
					      [|![images (9)](https://user-images.githubusercontent.com/104608815/168705068-882f5736-2e49-4f2b-b405-329c5328c7ea.jpeg)| ]÷") are escaped by a backslash (\)"
Enclose the string in single-quotes (
					     
					      
					      [|![images (9)](https://user-images.githubusercontent.com/104608815/168705068-882f5736-2e49-4f2b-b405-329c5328c7ea.jpeg)| ]÷'): Another string literal. Single quote characters (): @"
					      <
#
