python 2.7.14
10.3. stat — Interpreting stat() results
Source code: Lib/stat.py
________________________________________
The stat module defines constants and functions for interpreting the results of os.stat(), os.fstat() and os.lstat() (if they exist). For complete details about the stat(), fstat() and lstat() calls, consult the documentation for your system.
The stat module defines the following functions to test for specific file types:
stat.S_ISDIR(mode) 
Return non-zero if the mode is from a directory.
stat.S_ISCHR(mode) 
Return non-zero if the mode is from a character special device file.
stat.S_ISBLK(mode) 
Return non-zero if the mode is from a block special device file.
stat.S_ISREG(mode) 
Return non-zero if the mode is from a regular file.
stat.S_ISFIFO(mode) 
Return non-zero if the mode is from a FIFO (named pipe).
stat.S_ISLNK(mode) 
Return non-zero if the mode is from a symbolic link.
stat.S_ISSOCK(mode) 
Return non-zero if the mode is from a socket.
Two additional functions are defined for more general manipulation of the file’s mode:
stat.S_IMODE(mode) 
Return the portion of the file’s mode that can be set by os.chmod()—that is, the file’s permission bits, plus the sticky bit, set-group-id, and set-user-id bits (on systems that support them).
stat.S_IFMT(mode) 
Return the portion of the file’s mode that describes the file type (used by the S_IS*() functions above).
Normally, you would use the os.path.is*() functions for testing the type of a file; the functions here are useful when you are doing multiple tests of the same file and wish to avoid the overhead of the stat() system call for each test. These are also useful when checking for information about a file that isn’t handled by os.path, like the tests for block and character devices.
Example:
import os, sys
from stat import *

def walktree(top, callback):
    '''recursively descend the directory tree rooted at top,
       calling the callback function for each regular file'''

    for f in os.listdir(top):
        pathname = os.path.join(top, f)
        mode = os.stat(pathname).st_mode
        if S_ISDIR(mode):
            # It's a directory, recurse into it
            walktree(pathname, callback)
        elif S_ISREG(mode):
            # It's a file, call the callback function
            callback(pathname)
        else:
            # Unknown file type, print a message
            print 'Skipping %s' % pathname

def visitfile(file):
    print 'visiting', file

if __name__ == '__main__':
    walktree(sys.argv[1], visitfile)
All the variables below are simply symbolic indexes into the 10-tuple returned by os.stat(), os.fstat() or os.lstat().
stat.ST_MODE 
Inode protection mode.
stat.ST_INO 
Inode number.
stat.ST_DEV 
Device inode resides on.
stat.ST_NLINK 
Number of links to the inode.
stat.ST_UID 
User id of the owner.
stat.ST_GID 
Group id of the owner.
stat.ST_SIZE 
Size in bytes of a plain file; amount of data waiting on some special files.
stat.ST_ATIME 
Time of last access.
stat.ST_MTIME 
Time of last modification.
stat.ST_CTIME 
The “ctime” as reported by the operating system. On some systems (like Unix) is the time of the last metadata change, and, on others (like Windows), is the creation time (see platform documentation for details).
The interpretation of “file size” changes according to the file type. For plain files this is the size of the file in bytes. For FIFOs and sockets under most flavors of Unix (including Linux in particular), the “size” is the number of bytes waiting to be read at the time of the call to os.stat(), os.fstat(), or os.lstat(); this can sometimes be useful, especially for polling one of these special files after a non-blocking open. The meaning of the size field for other character and block devices varies more, depending on the implementation of the underlying system call.
The variables below define the flags used in the ST_MODE field.
Use of the functions above is more portable than use of the first set of flags:
stat.S_IFSOCK 
Socket.
stat.S_IFLNK 
Symbolic link.
stat.S_IFREG 
Regular file.
stat.S_IFBLK 
Block device.
stat.S_IFDIR 
Directory.
stat.S_IFCHR 
Character device.
stat.S_IFIFO 
FIFO.
The following flags can also be used in the mode argument of os.chmod():
stat.S_ISUID 
Set UID bit.
stat.S_ISGID 
Set-group-ID bit. This bit has several special uses. For a directory it indicates that BSD semantics is to be used for that directory: files created there inherit their group ID from the directory, not from the effective group ID of the creating process, and directories created there will also get the S_ISGID bit set. For a file that does not have the group execution bit (S_IXGRP) set, the set-group-ID bit indicates mandatory file/record locking (see also S_ENFMT).
stat.S_ISVTX 
Sticky bit. When this bit is set on a directory it means that a file in that directory can be renamed or deleted only by the owner of the file, by the owner of the directory, or by a privileged process.
stat.S_IRWXU 
Mask for file owner permissions.
stat.S_IRUSR 
Owner has read permission.
stat.S_IWUSR 
Owner has write permission.
stat.S_IXUSR 
Owner has execute permission.
stat.S_IRWXG 
Mask for group permissions.
stat.S_IRGRP 
Group has read permission.
stat.S_IWGRP 
Group has write permission.
stat.S_IXGRP 
Group has execute permission.
stat.S_IRWXO 
Mask for permissions for others (not in group).
stat.S_IROTH 
Others have read permission.
stat.S_IWOTH 
Others have write permission.
stat.S_IXOTH 
Others have execute permission.
stat.S_ENFMT 
System V file locking enforcement. This flag is shared with S_ISGID: file/record locking is enforced on files that do not have the group execution bit (S_IXGRP) set.
stat.S_IREAD 
Unix V7 synonym for S_IRUSR.
stat.S_IWRITE 
Unix V7 synonym for S_IWUSR.
stat.S_IEXEC 
Unix V7 synonym for S_IXUSR.
The following flags can be used in the flags argument of os.chflags():
stat.UF_NODUMP 
Do not dump the file.
stat.UF_IMMUTABLE 
The file may not be changed.
stat.UF_APPEND 
The file may only be appended to.
stat.UF_OPAQUE 
The directory is opaque when viewed through a union stack.
stat.UF_NOUNLINK 
The file may not be renamed or deleted.
stat.UF_COMPRESSED 
The file is stored compressed (Mac OS X 10.6+).
stat.UF_HIDDEN 
The file should not be displayed in a GUI (Mac OS X 10.5+).
stat.SF_ARCHIVED 
The file may be archived.
stat.SF_IMMUTABLE 
The file may not be changed.
stat.SF_APPEND 
The file may only be appended to.
stat.SF_NOUNLINK 
The file may not be renamed or deleted.
stat.SF_SNAPSHOT 
The file is a snapshot file.
See the *BSD or Mac OS systems man page chflags(2) for more information.

Gemfile
Current version
By default, all requests to https://api.github.com receive the v3 version of the REST API. We encourage you to explicitly request this version via the Accept header.
Accept: application/vnd.github.v3+json
For information about GitHub's GraphQL API v4, see the v4 documentation. For information about migrating to GraphQL, see "Migrating from REST."
Schema
All API access is over HTTPS, and accessed from https://api.github.com. All data is sent and received as JSON.
curl -i https://api.github.com/users/octocat/orgs
HTTP/1.1 200 OK
Server: nginx
Date: Fri, 12 Oct 2012 23:33:14 GMT
Content-Type: application/json; charset=utf-8
Connection: keep-alive
Status: 200 OK
ETag: "a00049ba79152d03380c34652f2cb612"
X-GitHub-Media-Type: github.v3
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4987
X-RateLimit-Reset: 1350085394
Content-Length: 5
Cache-Control: max-age=0, private, must-revalidate
X-Content-Type-Options: nosniff
Blank fields are included as null instead of being omitted.
All timestamps return in ISO 8601 format:
YYYY-MM-DDTHH:MM:SSZ
For more information about timezones in timestamps, see this section.
Summary representations
When you fetch a list of resources, the response includes a subset of the attributes for that resource. This is the "summary" representation of the resource. (Some attributes are computationally expensive for the API to provide. For performance reasons, the summary representation excludes those attributes. To obtain those attributes, fetch the "detailed" representation.)
Example: When you get a list of repositories, you get the summary representation of each repository. Here, we fetch the list of repositories owned by the octokit organization:
GET /orgs/octokit/repos
Detailed representations
When you fetch an individual resource, the response typically includes all attributes for that resource. This is the "detailed" representation of the resource. (Note that authorization sometimes influences the amount of detail included in the representation.)
Example: When you get an individual repository, you get the detailed representation of the repository. Here, we fetch the octokit/octokit.rb repository:
GET /repos/octokit/octokit.rb
The documentation provides an example response for each API method. The example response illustrates all attributes that are returned by that method.
Authentication
There are two ways to authenticate through GitHub API v3. Requests that require authentication will return 404 Not Found, instead of 403 Forbidden, in some places. This is to prevent the accidental leakage of private repositories to unauthorized users.
Basic authentication
curl -u "username" https://api.github.com
OAuth2 token (sent in a header)
curl -H "Authorization: token OAUTH-TOKEN" https://api.github.com
Note: GitHub recommends sending OAuth tokens using the Authorization header. GitHub accepts sending OAuth tokens as a query parameter, but it is less secure because URLs can be logged by any system along the request path.
Read more about OAuth2. Note that OAuth2 tokens can be acquired programmatically, for applications that are not websites.
OAuth2 key/secret
curl 'https://api.github.com/users/whatever?client_id=xxxx&client_secret=yyyy'
Using your client_id and client_secret does not authenticate as a user, it will only identify your OAuth application to increase your rate limit. Permissions are only granted to users, not applications, and you will only get back data that an unauthenticated user would see. For this reason, you should only use the OAuth2 key/secret in server-to-server scenarios. Don't leak your OAuth application's client secret to your users.
Read more about unauthenticated rate limiting.
Failed login limit
Authenticating with invalid credentials will return 401 Unauthorized:
curl -i https://api.github.com -u foo:bar
HTTP/1.1 401 Unauthorized
{
  "message": "Bad credentials",
  "documentation_url": "https://developer.github.com/v3"
}
After detecting several requests with invalid credentials within a short period, the API will temporarily reject all authentication attempts for that user (including ones with valid credentials) with 403 Forbidden:
curl -i https://api.github.com -u valid_username:valid_password
HTTP/1.1 403 Forbidden
{
  "message": "Maximum number of login attempts exceeded. Please try again later.",
  "documentation_url": "https://developer.github.com/v3"
}
Parameters
Many API methods take optional parameters. For GET requests, any parameters not specified as a segment in the path can be passed as an HTTP query string parameter:
curl -i "https://api.github.com/repos/vmg/redcarpet/issues?state=closed"
In this example, the 'vmg' and 'redcarpet' values are provided for the :owner and :repo parameters in the path while :state is passed in the query string.
For POST, PATCH, PUT, and DELETE requests, parameters not included in the URL should be encoded as JSON with a Content-Type of 'application/json':
curl -i -u username -d '{"scopes":["public_repo"]}' https://api.github.com/authorizations
Root endpoint
You can issue a GET request to the root endpoint to get all the endpoint categories that the REST API v3 supports:
curl https://api.github.com
GraphQL global node IDs
See the guide on "Using Global Node IDs" for detailed information about how to find node_ids via the REST API v3 and use them in GraphQL operations.
Client errors
There are three possible types of client errors on API calls that receive request bodies:
1.	Sending invalid JSON will result in a 400 Bad Request response.
2.	HTTP/1.1 400 Bad Request
3.	Content-Length: 35
4.	
5.	{"message":"Problems parsing JSON"}
6.	Sending the wrong type of JSON values will result in a 400 Bad Request response.
7.	HTTP/1.1 400 Bad Request
8.	Content-Length: 40
9.	
10.	{"message":"Body should be a JSON object"}
11.	Sending invalid fields will result in a 422 Unprocessable Entity response.
12.	HTTP/1.1 422 Unprocessable Entity
13.	Content-Length: 149
14.	
15.	{
16.	  "message": "Validation Failed",
17.	  "errors": [
18.	    {
19.	      "resource": "Issue",
20.	      "field": "title",
21.	      "code": "missing_field"
22.	    }
23.	  ]
24.	}
All error objects have resource and field properties so that your client can tell what the problem is. There's also an error code to let you know what is wrong with the field. These are the possible validation error codes:
Error Name	Description
missing	This means a resource does not exist.
missing_field	This means a required field on a resource has not been set.
invalid	This means the formatting of a field is invalid. The documentation for that resource should be able to give you more specific information.
already_exists	This means another resource has the same value as this field. This can happen in resources that must have some unique key (such as Label names).
Resources may also send custom validation errors (where code is custom). Custom errors will always have a message field describing the error, and most errors will also include a documentation_url field pointing to some content that might help you resolve the error.
HTTP redirects
API v3 uses HTTP redirection where appropriate. Clients should assume that any request may result in a redirection. Receiving an HTTP redirection is not an error and clients should follow that redirect. Redirect responses will have a Location header field which contains the URI of the resource to which the client should repeat the requests.
Status Code	Description
301	Permanent redirection. The URI you used to make the request has been superseded by the one specified in the Location header field. This and all future requests to this resource should be directed to the new URI.
302, 307	Temporary redirection. The request should be repeated verbatim to the URI specified in the Location header field but clients should continue to use the original URI for future requests.
Other redirection status codes may be used in accordance with the HTTP 1.1 spec.
HTTP verbs
Where possible, API v3 strives to use appropriate HTTP verbs for each action.
Verb	Description
HEAD	Can be issued against any resource to get just the HTTP header info.
GET	Used for retrieving resources.
POST	Used for creating resources.
PATCH	Used for updating resources with partial JSON data. For instance, an Issue resource has title and body attributes. A PATCH request may accept one or more of the attributes to update the resource. PATCH is a relatively new and uncommon HTTP verb, so resource endpoints also accept POST requests.
PUT	Used for replacing resources or collections. For PUT requests with no body attribute, be sure to set the Content-Length header to zero.
DELETE	Used for deleting resources.
Hypermedia
All resources may have one or more *_url properties linking to other resources. These are meant to provide explicit URLs so that proper API clients don't need to construct URLs on their own. It is highly recommended that API clients use these. Doing so will make future upgrades of the API easier for developers. All URLs are expected to be proper RFC 6570 URI templates.
You can then expand these templates using something like the uri_template gem:
>> tmpl = URITemplate.new('/notifications{?since,all,participating}')
>> tmpl.expand
=> "/notifications"

>> tmpl.expand :all => 1
=> "/notifications?all=1"

>> tmpl.expand :all => 1, :participating => 1
=> "/notifications?all=1&participating=1"
Pagination
Requests that return multiple items will be paginated to 30 items by default. You can specify further pages with the ?page parameter. For some resources, you can also set a custom page size up to 100 with the ?per_page parameter. Note that for technical reasons not all endpoints respect the ?per_pageparameter, see events for example.
curl 'https://api.github.com/user/repos?page=2&per_page=100'
Note that page numbering is 1-based and that omitting the ?page parameter will return the first page.
For more information on pagination, check out our guide on Traversing with Pagination.
Link header
Note: It's important to form calls with Link header values instead of constructing your own URLs.
The Link header includes pagination information:
Link: <https://api.github.com/user/repos?page=3&per_page=100>; rel="next",
  <https://api.github.com/user/repos?page=50&per_page=100>; rel="last"
The example includes a line break for readability.
This Link response header contains one or more Hypermedia link relations, some of which may require expansion as URI templates.
The possible rel values are:
Name	Description
next	The link relation for the immediate next page of results.
last	The link relation for the last page of results.
first	The link relation for the first page of results.
prev	The link relation for the immediate previous page of results.
Rate limiting
For API requests using Basic Authentication or OAuth, you can make up to 5000 requests per hour. Authenticated requests are associated with the authenticated user, regardless of whether Basic Authentication or an OAuth token was used. This means that all OAuth applications authorized by a user share the same quota of 5000 requests per hour when they authenticate with different tokens owned by the same user.
For unauthenticated requests, the rate limit allows for up to 60 requests per hour. Unauthenticated requests are associated with the originating IP address, and not the user making requests.
Note that the Search API has custom rate limit rules.
The returned HTTP headers of any API request show your current rate limit status:
curl -i https://api.github.com/users/octocat
HTTP/1.1 200 OK
Date: Mon, 01 Jul 2013 17:27:06 GMT
Status: 200 OK
X-RateLimit-Limit: 60
X-RateLimit-Remaining: 56
X-RateLimit-Reset: 1372700873
Header Name	Description
X-RateLimit-Limit	The maximum number of requests you're permitted to make per hour.
X-RateLimit-Remaining	The number of requests remaining in the current rate limit window.
X-RateLimit-Reset	The time at which the current rate limit window resets in UTC epoch seconds.

If you need the time in a different format, any modern programming language can get the job done. For example, if you open up the console on your web browser, you can easily get the reset time as a JavaScript Date object.
new Date(1372700873 * 1000)
// => Mon Jul 01 2013 13:47:53 GMT-0400 (EDT)
If you exceed the rate limit, an error response returns:
HTTP/1.1 403 Forbidden
Date: Tue, 20 Aug 2013 14:50:41 GMT
Status: 403 Forbidden
X-RateLimit-Limit: 60
X-RateLimit-Remaining: 0
X-RateLimit-Reset: 1377013266
{
   "message": "API rate limit exceeded for xxx.xxx.xxx.xxx. (But here's the good news: Authenticated requests get a higher rate limit. Check out the documentation for more details.)",
   "documentation_url": "https://developer.github.com/v3/#rate-limiting"
}
You can check your rate limit status without incurring an API hit.
Increasing the unauthenticated rate limit for OAuth applications
If your OAuth application needs to make unauthenticated calls with a higher rate limit, you can pass your app's client ID and secret as part of the query string.
curl -i 'https://api.github.com/users/whatever?client_id=xxxx&client_secret=yyyy'
HTTP/1.1 200 OK
Date: Mon, 01 Jul 2013 17:27:06 GMT
Status: 200 OK
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4966
X-RateLimit-Reset: 1372700873
Note: Never share your client secret with anyone or include it in client-side browser code. Use the method shown here only for server-to-server calls.
Staying within the rate limit
If you exceed your rate limit using Basic Authentication or OAuth, you can likely fix the issue by caching API responses and using conditional requests.
Abuse rate limits
In order to provide quality service on GitHub, additional rate limits may apply to some actions when using the API. For example, using the API to rapidly create content, poll aggressively instead of using webhooks, make multiple concurrent requests, or repeatedly request data that is computationally expensive may result in abuse rate limiting.
Abuse rate limits are not intended to interfere with legitimate use of the API. Your normal rate limitsshould be the only limit you target. To ensure you're acting as a good API citizen, check out our Best Practices guidelines.
If your application triggers this rate limit, you'll receive an informative response:
HTTP/1.1 403 Forbidden
Content-Type: application/json; charset=utf-8
Connection: close
{
  "message": "You have triggered an abuse detection mechanism and have been temporarily blocked from content creation. Please retry your request again later.",
  "documentation_url": "https://developer.github.com/v3/#abuse-rate-limits"
}
User agent required
All API requests MUST include a valid User-Agent header. Requests with no User-Agent header will be rejected. We request that you use your GitHub username, or the name of your application, for the User-Agent header value. This allows us to contact you if there are problems.
Here's an example:
User-Agent: Awesome-Octocat-App
cURL sends a valid User-Agent header by default. If you provide an invalid User-Agent header via cURL (or via an alternative client), you will receive a 403 Forbidden response:
curl -iH 'User-Agent: ' https://api.github.com/meta
HTTP/1.0 403 Forbidden
Connection: close
Content-Type: text/html
Request forbidden by administrative rules.
Please make sure your request has a User-Agent header.
Check https://developer.github.com for other possible causes.
Conditional requests
Most responses return an ETag header. Many responses also return a Last-Modified header. You can use the values of these headers to make subsequent requests to those resources using the If-None-Match and If-Modified-Since headers, respectively. If the resource has not changed, the server will return a 304 Not Modified.
Note: Making a conditional request and receiving a 304 response does not count against your Rate Limit, so we encourage you to use it whenever possible.
curl -i https://api.github.com/user
HTTP/1.1 200 OK
Cache-Control: private, max-age=60
ETag: "644b5b0155e6404a9cc4bd9d8b1ae730"
Last-Modified: Thu, 05 Jul 2012 15:31:30 GMT
Status: 200 OK
Vary: Accept, Authorization, Cookie
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4996
X-RateLimit-Reset: 1372700873
curl -i https://api.github.com/user -H 'If-None-Match: "644b5b0155e6404a9cc4bd9d8b1ae730"'
HTTP/1.1 304 Not Modified
Cache-Control: private, max-age=60
ETag: "644b5b0155e6404a9cc4bd9d8b1ae730"
Last-Modified: Thu, 05 Jul 2012 15:31:30 GMT
Status: 304 Not Modified
Vary: Accept, Authorization, Cookie
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4996
X-RateLimit-Reset: 1372700873
curl -i https://api.github.com/user -H "If-Modified-Since: Thu, 05 Jul 2012 15:31:30 GMT"
HTTP/1.1 304 Not Modified
Cache-Control: private, max-age=60
Last-Modified: Thu, 05 Jul 2012 15:31:30 GMT
Status: 304 Not Modified
Vary: Accept, Authorization, Cookie
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4996
X-RateLimit-Reset: 1372700873
Cross origin resource sharing
The API supports Cross Origin Resource Sharing (CORS) for AJAX requests from any origin. You can read the CORS W3C Recommendation, or this intro from the HTML 5 Security Guide.
Here's a sample request sent from a browser hitting http://example.com:
curl -i https://api.github.com -H "Origin: http://example.com"
HTTP/1.1 302 Found
Access-Control-Allow-Origin: *
Access-Control-Expose-Headers: ETag, Link, X-GitHub-OTP, X-RateLimit-Limit, X-RateLimit-Remaining, X-RateLimit-Reset, X-OAuth-Scopes, X-Accepted-OAuth-Scopes, X-Poll-Interval
This is what the CORS preflight request looks like:
curl -i https://api.github.com -H "Origin: http://example.com" -X OPTIONS
HTTP/1.1 204 No Content
Access-Control-Allow-Origin: *
Access-Control-Allow-Headers: Authorization, Content-Type, If-Match, If-Modified-Since, If-None-Match, If-Unmodified-Since, X-GitHub-OTP, X-Requested-With
Access-Control-Allow-Methods: GET, POST, PATCH, PUT, DELETE
Access-Control-Expose-Headers: ETag, Link, X-GitHub-OTP, X-RateLimit-Limit, X-RateLimit-Remaining, X-RateLimit-Reset, X-OAuth-Scopes, X-Accepted-OAuth-Scopes, X-Poll-Interval
Access-Control-Max-Age: 86400
JSON-P callbacks
You can send a ?callback parameter to any GET call to have the results wrapped in a JSON function. This is typically used when browsers want to embed GitHub content in web pages by getting around cross domain issues. The response includes the same data output as the regular API, plus the relevant HTTP Header information.
curl https://api.github.com?callback=foo
/**/foo({
  "meta": {
    "status": 200,
    "X-RateLimit-Limit": "5000",
    "X-RateLimit-Remaining": "4966",
    "X-RateLimit-Reset": "1372700873",
    "Link": [ // pagination headers and other links
      ["https://api.github.com?page=2", {"rel": "next"}]
    ]
  },
  "data": {
    // the data
  }
})
You can write a JavaScript handler to process the callback. Here's a minimal example you can try out:
<html>
<head>
<script type="text/javascript">
function foo(response) {
  var meta = response.meta;
  var data = response.data;
  console.log(meta);
  console.log(data);
}

var script = document.createElement('script');
script.src = 'https://api.github.com?callback=foo';

document.getElementsByTagName('head')[0].appendChild(script);
</script>
</head>

<body>
  <p>Open up your browser's console.</p>
</body>
</html>
All of the headers are the same String value as the HTTP Headers with one notable exception: Link. Link headers are pre-parsed for you and come through as an array of [url, options] tuples.
A link that looks like this:
Link: <url1>; rel="next", <url2>; rel="foo"; bar="baz"
... will look like this in the Callback output:
{
  "Link": [
    [
      "url1",
      {
        "rel": "next"
      }
    ],
    [
      "url2",
      {
        "rel": "foo",
        "bar": "baz"
      }
    ]
  ]
}
Timezones
Some requests that create new data, such as creating a new commit, allow you to provide time zone information when specifying or generating timestamps. We apply the following rules, in order of priority, to determine timezone information for API calls.
•	Explicitly providing an ISO 8601 timestamp with timezone information
•	Using the Time-Zone header
•	Using the last known timezone for the user
•	Defaulting to UTC without other timezone information
Explicitly providing an ISO 8601 timestamp with timezone information
For API calls that allow for a timestamp to be specified, we use that exact timestamp. An example of this is the Commits API.
These timestamps look something like 2014-02-27T15:05:06+01:00. Also see this example for how these timestamps can be specified.
Using the Time-Zone header
It is possible to supply a Time-Zone header which defines a timezone according to the list of names from the Olson database.
curl -H "Time-Zone: Europe/Amsterdam" -X POST https://api.github.com/repos/github/linguist/contents/new_file.md
This means that we generate a timestamp for the moment your API call is made in the timezone this header defines. For example, the Contents API generates a git commit for each addition or change and uses the current time as the timestamp. This header will determine the timezone used for generating that current timestamp.
Using the last known timezone for the user
If no Time-Zone header is specified and you make an authenticated call to the API, we use the last known timezone for the authenticated user. The last known timezone is updated whenever you browse the GitHub website.
Defaulting to UTC without other timezone information
If the steps above don't result in any information, we use UTC as the timezone to create the git commit.
# Gemfile
    REST API v3
•	Reference
 
•	Guides
 
•	Libraries
Media Types
i.	Comment body properties
ii.	Git blob properties
iii.	Commits, commit comparison, and pull requests
iv.	Repository contents
v.	Gists
Custom media types are used in the API to let consumers choose the format of the data they wish to receive. This is done by adding one or more of the following types to the Accept header when you make a request. Media types are specific to resources, allowing them to change independently and support formats that other resources don't.
All GitHub media types look like this:
application/vnd.github[.version].param[+json]
The most basic media types the API supports are:
application/json
application/vnd.github+json
Neither of these specify a version, so you will always get the current default JSON representation of resources.
Important: The default version of the API may change in the future. If you're building an application and care about the stability of the API, be sure to request a specific version in the Accept header as shown in the examples below.
You can specify a version like so:
application/vnd.github.v3+json
If you're specifying a property (such as full/raw/etc defined below), put the version before the property:
application/vnd.github.v3.raw+json
You can check the current version through every response's headers. Look for the X-GitHub-Media-Typeheader:
curl https://api.github.com/users/technoweenie -I
HTTP/1.1 200 OK
X-GitHub-Media-Type: github.v3
curl https://api.github.com/users/technoweenie -I \
 -H "Accept: application/vnd.github.full+json"
HTTP/1.1 200 OK
X-GitHub-Media-Type: github.v3; param=full; format=json
curl https://api.github.com/users/technoweenie -I \
 -H "Accept: application/vnd.github.v3.full+json"
HTTP/1.1 200 OK
X-GitHub-Media-Type: github.v3; param=full; format=json
Comment body properties
The body of a comment can be written in GitHub Flavored Markdown. issues, issue comments, pull request comments, and the gist comments APIs all accept these same media types:
Raw
application/vnd.github.VERSION.raw+json
Return the raw markdown body. Response will include body. This is the default if you do not pass any specific media type.
Text
application/vnd.github.VERSION.text+json
Return a text only representation of the markdown body. Response will include body_text.
HTML
application/vnd.github.VERSION.html+json
Return HTML rendered from the body's markdown. Response will include body_html.
Full
application/vnd.github.VERSION.full+json
Return raw, text and HTML representations. Response will include body, body_text, and body_html:
Git blob properties
The following media types are allowed when getting a blob:
JSON
application/vnd.github.VERSION+json
application/json
Return JSON representation of the blob with content as a base64 encoded string. This is the default if nothing is passed.
Raw
application/vnd.github.VERSION.raw
Return the raw blob data.
Commits, commit comparison, and pull requests
The commits API and pull requests API support diff and patch formats:
diff
application/vnd.github.VERSION.diff
patch
application/vnd.github.VERSION.patch
sha
application/vnd.github.VERSION.sha
Repository contents
Raw
application/vnd.github.VERSION.raw
Return the raw contents of a file. This is the default if you do not pass any specific media type.
HTML
application/vnd.github.VERSION.html
For markup files such as Markdown or AsciiDoc, you can retrieve the rendered HTML using the .htmlmedia type. Markup languages are rendered to HTML using our open-source Markup library.
Gists
Raw
application/vnd.github.VERSION.raw
Return the raw contents of a gist. This is the default if you do not pass any specific media type.
base64
application/vnd.github.VERSION.base64
The gist contents are base64-encoded before being sent out. This can be useful if your gist contains any invalid UTF-8 sequences.



