Modify Headers
=============

An [add-on for Firefox](https://addons.mozilla.org/en-US/firefox/addon/modify-headers/) by Gareth Hunt.
Help on using the add-on is available at http://www.garethhunt.com/modifyheaders/help/

#### Modifications

1. Support for replacement based on a regular expression match.
If the _Header value_ for a _Modify_ action is of the form
/*regex*/*replacement*/
_regex_ is a [Regular expression](https://developer.mozilla.org/en/JavaScript/Guide/Regular_Expressions)
_replacement_ is the string a matched header portion will be replaced with.
A known limitation since the above pattern must be wrapped in forward slashes, is that 
you can't use forward slashes in your regex or replacement string.

2. If a _Host_ header is being modified using the regex pattern,
the whole [request is replaced](http://stackoverflow.com/a/5207141/905908).
The replaced channel ([nsIHttpChannel](https://developer.mozilla.org/en/XPCOM_Interface_Reference/nsIHttpChannel)) has a modified URL ([nsIStandarURL](https://developer.mozilla.org/en/XPCOM_Interface_Reference/nsIStandardURL)).
This feature utilizes code from the [https-everywhere](https://www.eff.org/https-everywhere) addon (IOUtil.js).
As an example, using the Header value "/www.domain.com/192.168.254.65/"
Will make all the requests from a page to that domain go to the IP address.
So a linked CSS on the index page etc - *domain.com/css/style.css* would be requested
as *192.168.254.65/css/style.css*
