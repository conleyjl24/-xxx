# -xxx
Hello-@x0x0xghj
<!-- Facebook Pixel Code -->
<script>
!function(f,b,e,v,n,t,s)
{if(f.fbq)return;n=f.fbq=function(){n.callMethod?
n.callMethod.apply(n,arguments):n.queue.push(arguments)};
if(!f._fbq)f._fbq=n;n.push=n;n.loaded=!0;n.version='2.0';
n.queue=[];t=b.createElement(e);t.async=!0;
t.src=v;s=b.getElementsByTagName(e)[0];
s.parentNode.insertBefore(t,s)}(window,document,'script',
'https://connect.facebook.net/en_US/fbevents.js');
fbq('init', '1128591863976784'); 
fbq('track', 'PageView');
</script>
<noscript>
<img height="1" width="1" 
src="https://www.facebook.com/tr?id=1128591863976784&ev=PageView
&noscript=1"/>
</noscript>
<!-- End Facebook Pixel Code -->

From 2111a836f65c05fc2320d250e633fd62a545ad38 Mon Sep 17 00:00:00 2001
From: 477447 <43150340+477447@users.noreply.github.com>
Date: Mon, 15 Oct 2018 12:58:44 +0400
Subject: [PATCH] Update README.md

---
 README.md | 143 ++++++++----------------------------------------------
 1 file changed, 19 insertions(+), 124 deletions(-)

diff --git a/README.md b/README.md
index 8bf7c2f..19e04d9 100644
--- a/README.md
+++ b/README.md
@@ -1,129 +1,24 @@
 # -xxx
 Hello-@x0x0xghj
-Artificial inte intelligence
-can you give me reply
-https://github.com/huandu/facebook.git
-https://github.com/facebook/facebook-android-sdk.git
-https://github.com/facebook/facebook-objc-sdk.git
-https://github.com/opauth/facebook.git
-diff --git a/README.md b/README.md
-index 2e5e471..7e61c23 100644
---- a/README.md
-+++ b/README.md
-@@ -2,6 +2,14 @@
- Hello-@x0x0xghj
- Artificial inte intelligence
- can you give me reply
-+https://github.com/huandu/facebook.git
-+https://github.com/facebook/facebook-android-sdk.git
-+https://github.com/facebook/facebook-objc-sdk.git
-+https://github.com/opauth/facebook.git
-+
-+
-+
-+
-git-clone
-https://github.com/AdmitHub/meteor-buildpack-horse.git
-git-clone
-Merge pull request #118 from 477447/readme-edits  …
-
-[![Build Status](https://travis-ci.org/huandu/facebook.png?branch=master)](https://travis-ci.org/huandu/facebook)
- This is a Go library fully supports Facebook Graph API with file upload, batch request and FQL. It's simple yet powerful.
-This is a Go library fully supports Facebook Graph API with file upload, batch request and FQL. It also supports Graph API 2.0 using the same methods.
- It can be used in Google App Engine. See [document](http://godoc.org/github.com/huandu/facebook) for details.
-
-Change Log
-v2.3.2
-[FIX] #114 Correctly parse query string in the path which doesn't start with '/', e.g. fb.Get("me?fields=name,email", nil).
-v2.3.1
-[FIX] #114 Query string in the path, e.g. fb.Get("/me?fields=name,email", nil), works as expected now. Thanks, @AsifArko.
-v2.3.0
-[FIX] #110 Use HTTP GET to send request in which the method is GET. Thank @nayakravi for raising this issue, and Thank @AlphaB and @robbiet480 for your valuable inputs.
-v2.2.0
-[NEW] #103 Add RFC3339Timestamps flag to set date_format on every API request. If this flag is set, all date value returned by facebook will be encoded with a format supported by json.Unmarshal. Thanks, @robbiet480.
-[NEW] #105 Added ability to override Session base URL. It's designed for unit testing. All session requests can be redirected to a test server by setting Session#BaseURL to a test URL. Thanks, @vania-pooh.
-v2.1.2
-[FIX] #87 Fix a crash in Session#addUsageInfo. Thanks, @flemeur.
-v2.1.1
-[NEW] #86 Parse X-App-Usage and X-Page-Usage in response header and store the usage information in Result. Use Result#UsageInfo() to read it. Thanks, @robbiet480.
-v2.1.0
-[NEW] #81 Compatible with the struct field's tag used by json.Unmarshal. The "json" key works as expected now. If both the "facebook" key and the "json" key exist, use "facebook".
-v2.0.0
-[NEW] #80 #71 All Session API, which sends requests to Facebook, support Context now. Thanks, @sebnow for your thoughts and reminder.
-[NEW] #79 Add some number types which can be decoded from a string implicitly.
-[NEW] #78 #57 Deprecate FQL and remove all related code.
-[FIX] #73 Fix regular expression for video post. Thanks, @acochrane.
-[FIX] #62 Use base64.RawURLEncoding to decode signed request data. Thanks,@zonr.
-[FIX] Fix some typos in README and test cases. Thank @nick3399, @J-P-77, @smasher164, @enm10k and many others.
-[FIX] Clean up code for readability.
-v1.8.1
-[FIX] #60 Handle string errors in Decode(). Thanks, @sebnow.
-v1.8.0
-[FIX] #59 Guess content type for binary params by filename extension or an arbitrary value. Thanks,@panki.
-v1.7.1
-[FIX] Fix a tiny bug which slightly affects performance when decoding anonymous field.
-v1.7.0
-[NEW] #50 Result can decode embedded struct field now.
-[NEW] Add a new field tag facebook:"-" to omit the field when decoding. It can improve decoding performance slightly.
-v1.6.0
-[NEW] #42 Support custom JSON unmarshaling and json.Unmarshaler interface in decoding.
-v1.5.6
-[NEW] #40 Session works with http client created by package golang.org/x/oauth2. README is updated with a sample.
-v1.5.5
-[FIX] #39 When /oauth/access_token returns a query string, this package can parse expires or expires_in field correctly.
-v1.5.4
-[FIX] #37 Add missing client_secret in query string when parsing client code.
-v1.5.3
-[FIX] #34 Use expires instead of expires_in if possible when exchanging token or parsing code.
-v1.5.2
-[FIX] #32 BatchApi/Batch returns facebook error when access token is not valid.
-v1.5.1
-[FIX] #31 When /oauth/access_token returns a query string instead of json, this package can correctly handle it.
-v1.5.0
-[NEW] #28 Support debug mode introduced by facebook graph API v2.3.
-[FIX] Removed all test cases depending on facebook graph API v1.0.
-v1.4.1
-[NEW] #27 Timestamp value in Graph API response can be decoded as a time.Time value now. Thanks, @Lazyshot.
-v1.4.0
-[FIX] #23 Algorithm change: Camel case string to underscore string supports abbreviation
-Fix for #23 could be a breaking change. Camel case string HTTPServer will be converted to http_server instead of h_t_t_p_server. See issue description for detail.
-
-v1.3.0
-[NEW] #22 Add a new helper struct BatchResult to hold batch request responses.
-v1.2.0
-[NEW] #20 Add Decode functionality for paging results. Thanks, @cbroglie.
-[FIX] #21 Session#Inspect cannot return error if access token is invalid.
-Fix for #21 will result a possible breaking change in Session#Inspect. It was return whole result returned by facebook inspect api. Now it only return its "data" sub-tree. As facebook puts everything including error message in "data" sub-tree, I believe it's reasonable to make this change.
-
-v1.1.0
-[FIX] #19 Any valid int64 number larger than 2^53 or smaller than -2^53 can be correctly decoded without precision lost.
-Fix for #19 will result a possible breaking change in Result#Get and Result#GetField. If a JSON field is a number, these two functions will return json.Number instead of float64.
-
-The fix also introduces a side effect in Result#Decode and Result#DecodeField. A number field (int* and float*) can be decoded to a string. It was not allowed in previous version.
-
-v1.0.0
-Initial tag. Library is stable enough for all features mentioned in README.md.
-https://github.com/phonegap/phonegap-start.git
-v1.0.0
-Initial tag. Library is stable enough for all features mentioned in README.md
-
-
-Colorado @x0x0xghj on Facebook
-urgently need 10,000 subscribers
-100,000 subscribers
-too many scams and
-malefactors should be destroyed
-malware that
-apply to my Account.
-Initial tag. Library is stable enough for all features mentioned in README.md
-Initial tag. Library is stable enough for all features mentioned in README.md
-
-
-
-
-
- 
- 
+<!-- Facebook Pixel Code -->
+<script>
+!function(f,b,e,v,n,t,s)
+{if(f.fbq)return;n=f.fbq=function(){n.callMethod?
+n.callMethod.apply(n,arguments):n.queue.push(arguments)};
+if(!f._fbq)f._fbq=n;n.push=n;n.loaded=!0;n.version='2.0';
+n.queue=[];t=b.createElement(e);t.async=!0;
+t.src=v;s=b.getElementsByTagName(e)[0];
+s.parentNode.insertBefore(t,s)}(window,document,'script',
+'https://connect.facebook.net/en_US/fbevents.js');
+fbq('init', '1128591863976784'); 
+fbq('track', 'PageView');
+</script>
+<noscript>
+<img height="1" width="1" 
+src="https://www.facebook.com/tr?id=1128591863976784&ev=PageView
+&noscript=1"/>
+</noscript>
+<!-- End Facebook Pixel Code -->

{
   "editor.renderWhitespace": "all",
  
  "html.format.wrapLinength": 0,
  
  "editor.fontFamily": "Consolas, 'Courier New', monospace",
  
  "jshint,options": {
  
    "esversion":6
    
    }
    
}
 $1000
 Development of a web portal for interaction with Clients and business partners.
•	Integration of existing web portals to the process/ workflow solutions.
•	Enhancements and upgrades of existing SCM solutions.

#!/bin/bash
echo "Generating an SSL private key to sign your certificate..."
openssl genrsa -des3 -out myssl.key 1024
Hello-World-Hello-Facebook-Hello-kolorado-Hello-@x0x0xghj

I have a cell phone with a valid number, but I have one.
there is a suspicion that against my number are malicious programs
my number is registered on Facebook I think that for your employees will not be
it's hard to get my phone number. I have to destroy these.
malware managed Facebook page
called kolorado @x0x0xghj not a managed page
called Robert Bondikyan I'll send you a lot of letters, symbols and numbers
so you can dial a normal program to solve
this problem think that this you will help,
 
 
 hgjwefweoioiewiyqioqoiyqoiyeoifgygopipg[gpug][guoighgdhzzbzmbcvmbcv.//bn;lsdhjgiysdigysdilhysdfkh.newioiewoygrweqpou
 iewyuitghjkbvhgdrwtrwuitoiyp[[pkl;knmghfcvbxwqegfqeii327832897ghlkjgvlkgewopwegulwekgjnm,nm,nsdnvd.,ndsv.,ndv.,nvd
 
 %!@#$!#@~#@~$@$@%@%$@&^$&^$%^#&*%*&%(*&(++)_)+_+)*&*^IOTYOPIPOU"":":?>?>><><><?>??<?<?<"L"L{O{}}}P}||||\\\\'''"""
 
 
 
#$@$#!!$#7568757647436536537859871981698641982641097401974-9386938673r5375r75r3312
21231316464697979//*****

Hello-main()

Hello-main():4
you can destroy all malware programs that operate against my phone number


