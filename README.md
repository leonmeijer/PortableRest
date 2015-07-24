[PortableRest 3.0](https://github.com/leonmeijer/PortableRest)
=================

The different between this fork and the original one is that this supports doing HttpRequests with raw body content. And the NuGet dependencies are updated.

PortableRest is a Portable Class Library for implementing REST API clients in other Portable Class Libraries. It leverages JSON.NET for rapid, customizable serialization, as well as the Microsoft.Bcl.Async library for awaitable execution on any platform. It is designed to be largely drop-in compatible with RestSharp, though you will need to make some changes and recompile if you are upgrading from that solution.
This is a fork of http://github.com/AdvancedREI/PortableRest because the original project couldn't send a HttpRequest with a raw body.

Works on .NET 4.5, Silverlight 5, Windows Phone 8.x, and Windows 8.x, as well as iOS and Android through Xamarin.

Design Goals
----------
+ Be able to write one REST client wrapper that can be used on all current-generation Microsoft platforms (without the techniques we have to use for [XamlEssentials](http://github.com/AdvancedREI/XamlEssentials)).
+ Have more control over serialization of property names (so you're not limited to the "remove all dashes" convention of RestSharp).
+ Be able to have objects be easily serializable to local storage using standard techniques, without jumping through a lot of hoops.

What's New?
-----------
### Version 3.0
+ Added constructor overload that accepts a custom HttpMessageHandler for all requests the HttpClient makes.
+ Added support for using the AsyncOAuth NuGet package for leveraging OAuth in your requests.
+ Added support for specifying the JsonSerializerSettings on a client-wide or per-request basis, with request-specific settings taking precedence.
+ Enhanced the SendAsync method to pass exceptions thrown by the serializer into the RestResponse.
+ BREAKING: The regular package is no longer being signed. If you need the signed version, install `PortableRest.Signed` instead.

### Version 2.5
+ Ability to control parameter encoding. Example: `RestRequest.AddParameter("test", someStream, ParameterEncoding.Base64);`.
+ Ability to add request-specific headers. This is useful in situations where the value might change between requests, for example with expiring OAuth tokens. Example: `RestRequest.AddHeader("X-Authorization", yourTokenHere);`
+ The RestClient will now set the UserAgent for you if you do not set the property yourself. The format will be `"YourAssemblyTitleAttributeValue Major.Minor.Revision (PortableRest Major.Minor.Revision)"`
+ In addition, you can call `RestClient.SetUserAgent<SomeTypeFromYourRestLibrary>(someString)`, which in the above example would replace `YourAssemblyTitleAttributeValue` with the contents of `someString`.

### Version 2.4
+ Ability to control parameter encoding. Example: `RestRequest.AddParameter("test", someStream, ParameterEncoding.Base64);`.
+ Ability to add request-specific headers. This is useful in situations where the value might change between requests, for example with expiring OAuth tokens. Example: `RestRequest.AddHeader("X-Authorization", yourTokenHere);`
+ The RestClient will now set the UserAgent for you if you do not set the property yourself. The format will be `"YourAssemblyTitleAttributeValue Major.Minor.Revision (PortableRest Major.Minor.Revision)"`
+ In addition, you can call `RestClient.SetUserAgent<SomeTypeFromYourRestLibrary>(someString)`, which in the above example would replace `YourAssemblyTitleAttributeValue` with the contents of `someString`.

More Info
-----------
NOTE: Will have an updated post for v3 soon!
[Read more about PortableRest on our blog](http://advancedrei.com/blogs/development/introducing-portablerest-v2-cross-platform-rest-client-for-dotnet-apps)


Quick start
-----------

Install the NuGet package: `Install-Package PortableRest`, clone the repo, `git clone git://github.com/advancedrei/portablerest.git`, or [download the latest release](https://github.com/advancedrei/portablerest/zipball/master).

If you are planning on redistributing your own PortableRest-based client, such as our http://gaug.es Client, you need to make sure your Portable profile does not use .NET 4.0, Silverlight 4.0, or Windows Phone 7.X. Having those platforms available will cause this package to fail to install. If you need support for those platforms, create an issue and we'll investigate the possibility of adding support.

Please see the unit tests project, [Bing.RestClient](https://github.com/advancedrei/bing.restclient), or [Xbox.Music](https://github.com/advancedrei/xbox.music) for examples of how to leverage PortableRest in your REST client.

Bug tracker
-----------

Have a bug? Please create an issue here on GitHub that conforms with [necolas's guidelines](https://github.com/necolas/issue-guidelines).

https://github.com/AdvancedREI/PortableRest/issues



Twitter account
---------------

Keep up to date on announcements and more by following AdvancedREI on Twitter, [@AdvancedREI](http://twitter.com/AdvancedREI).



Blog
----

Read more detailed announcements, discussions, and more on [The AdvancedREI Dev Blog](http://advancedrei.com/blogs/development).


Author
-------

**Robert McLaws**

+ http://twitter.com/robertmclaws
+ http://github.com/advancedrei


Copyright and license
---------------------

Copyright 2013 AdvancedREI, LLC.

The MIT License (MIT)

Copyright (c) 2013 AdvancedREI, LLC. and Robert McLaws

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of
the Software, and to permit persons to whom the Software is furnished to do so,
subject to the following conditions:

- The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

- You may not use this software to sell apps in the [Windows Phone Store](http://www.windowsphone.com/en-US/store/publishers?publisherId=AdvancedREI%252c%2BLLC.&appId=42268b66-a8ed-46ea-9355-1287522a7cf9) or Windows Store that replicate functionality from apps distributed by AdvancedREI.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS
FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR
COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER
IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN
CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
