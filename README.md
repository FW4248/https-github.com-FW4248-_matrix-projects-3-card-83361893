
## </
     
                   
		   



|![images (7)](https://user-images.githubusercontent.com/104608815/168705069-aa8b2cb7-12bf-4b2b-8801-3945b9e11084.jpeg)|

|![images (5)](https://user-images.githubusercontent.com/104608815/168705071-8740c61a-c171-41e3-98b8-b471c9e48b1e.jpeg)|

|![images (10)](https://user-images.githubusercontent.com/104608815/168705072-9e2b478c-901b-42c2-9a66-81dbc80c8410.png)|


/>
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
bool()	boolean	int8
datetime()	date	datetime
dynamic()		array or dictionary or any other of the other values
int()	int has an alias long	int
long()		long
real()	double	real
string()		string
timespan()	time	timespan
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
datetime(null)	Check out our null values
now()	The current time.
now(-timespan)	now()-timespan
ago(timespan)	now()-timespan
now() and ago() indicate a datetime value compared with the moment in time when APL started to execute the query.

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
