Hello-World
 <Window x:Class="OpenWindow.MainWindow"
         xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
         xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
         xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
         xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
         xmlns:local="clr-namespace:OpenWindow"
         mc:Ignorable="d"
         Title="MainWindow" Height="450" Width="800">
      <Grib>
          <Button
               Content="OpenWindow"
               HorizontalAlignment="Center"
               VerticalAlignment="Center"
               Width="90"
               Click="Button_Click"/>
       </Grib>
   </Window>
   
.md

  FROM goland
  
  ENV GO111MODULE=on
  
  WORKDIR /app
  
  COPY go.mod .
  COPY go.sum .
  
  RUN go mod download
  
  COPY . .
  
  RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build
  
  EXPOSE 8080
  ENTRYPOINT ["/app/tttpserver"]

 i686-linux    kube-router
 x86_64-linux  kube-router
 aarch64-linux kube-router
 
jekyll

 
 
   "script": {
   "test": "echo \"Error: no test specified\" && exit 1",
   "start": "node server.js",
   "server": "nodemon server.js"
   },
# Authentication

There are three ways to authenticate through GitHub API v3.Reguests that reguire authentication will
return 404 Not Found instead of 403 Forbidden in some places.This is to prevent the accidental
leakage of private repositories to unauthorized users.

Summary representations

When you fetch a list of resources, the reponse includes a subset of the attributes for that resource.
This is the "summary" representation of the resource.(Some attributes are computationally expensive

for the API to provide. For performance reasons, the summary representation excludes those attributes.
To obtain those attributes.fetch the detailed representation.)

# Example:When you get a list of repositories you get the summary representation of each repository.
Here we fetch the list of repositories owned by the octokit organization:

# Detailed representations

When you fetch an individual resource the response typically includes all attributes for that resource.
This is the detailed representation of the resource.(Note that authorization sometimes influences the

amount of detail included in the representation)

# Example:When you get an individual repository, you get the detailed representation of the repository
Here we fetch the octokit.rd repository:

# Accept

HTTP redirects

API v3 uses HTTP redirection where appropriate.Clients should assume that any reguest may result in a
redirection.Receiving an HTTP redirection is not an error and clients should follow that redirect.Redirect a

responses will have a Location header fieled which contains the URI of the resource to which the client
should repeat the reguests.

Pagination

Reguests that return multiple items will be paginated to 30 items by default.You can specify further
pages with the ?page parameter.For some resources you can also set a custom page size up to 100

with the ?per_page parameter.Note that for technical reasons not all endpoints respect the ?per_page
parameter,see events for example.

Accept

Get a single grant
GET /applications/grants/:grants_id

# Response
Status: 200 OK
{
  "id": 1,
  "url": "https://api.github.com/applications/grants/1",
  "app": {
    "url": "http://my-github-app.com",
    "name": "my github app",
    "client_id": "abcde12345fghij67890"
   },
   "created_at"": "2011-09-06T17:26:27Z",
   "updated_at":  "2011-09-06T20:39:23Z",
   "scopes": [
     "public_repo"
   ]
 }
 Accept
 Example
 
 This example removes two of three assignees leaving octocat assignee.
 {
 "assignees": [
   "hubot",
   "other_user"
 ]
}

Accept
Get a single grant
GET /applications/grant_id

Response
Status: 200 OK
{
  "id": 1,
  "url": "https://api.github.com/applications/grants/1",
  "app": {
    "url": "http://my-github-com",
    "name": "my github app",
    "client_id": "abcde12345fghij67890"
    },
    "created_at": "2011-09-06T17:26:27Z",
    "updated_at": "2011-09-06T20:3923Z",
    "scopes": [
      "public_repo"
    ]
  }
Accept

Check runs and check suites API

Allows a GitHub App to run external checks on a repository's code.See the Check runs and Check suites
APIs for more details.

Custom media type:antiope-preview #Announced:2018-05-07

Project card details
The RESR API v3 responses for issue events and issue timeline events now return the project_card field
for project-related events.

# Custom media type: starfox-preview Announced: 2018-12-09

GitHub App Manifests
GitHub App Manifests allow people to create preconfigured GitHub Apps.See "Creating GitHub Apps
from a manifest" for more details.

# Custom media type: fury-preview

Doployment statuses
You can now update the environment of a deployment status and use the in_progress and gueued
states.When you create deployment statuses you can nowuse the auto_inactive parameter to mark

old production deployments as inactive
# Custom media type: flash-preview Announced: 2018-12-09

Repository creation permissions

You can now configure whether organization members can create repositories and which types of
repositories they can create.See "Edit an organization" for more details

# Custom media types:surtur-preview

Accept
# Response
Status: 200 OK
Link: <https://api.github.com/resource?page=2>; rel="next",
      <https://api.github.com/resource?page=5>; rel="last"
      
[
  {
    "id": 1,
    "ur1": https://api.github.com/applications/grants/1",
    "app": {
      "url": "http://my-github-app.com",
      "name": "my github app",
      "client_id": "abcde12345fghij67890"
    },
    "created_at": "2011-09-06T17:26:27Z",
    "updated_at": "2011-09-06T20:39:23Z",
    "scopes": [
      "public_repo"
    ]
  }
]

Accept
# Response if returning a new token
Status: 201 Created
Location: https://api.github.com/authorizations/1

{
  "id": 1,
  "url": "https://api.github.com/authorizations/1",
  "scopes": [
     "public_repo"
  ],
  "token": "abcdefgh12345678",
  "token_last_eight": "12345678",
  "hashed_token": "25f94a2a5c7fbaf499c665bc73d67c1c87e496da8985131633ee0a95819db2e8",
  "app": {
    "url": "http://my-github-app.com",
    "name": "my github app",
    "client_id": "abcde12345fghij67890"
  },
  "note": "optional note",
  "note_url": "http://optional/note/url",
  "updated_at": "2011-09-06T20:39:23Z",
  "created_at": 2011-09-06T17:26:27Z",
  "fingerprint": ""
 }
Accept
{
  "message": "Reguires authetication",
  "documentatation_url": "https://developer.github.com/v3"
}
Accept
send real money on my e-mail and that there was real money without investments of my means
and that there was displayed about $1000

-fingerprint-Get a single grant
-fingerprint-GET /applications/:grant_id
-fingerprint-Response
-fingerprint-Status: 200 OK
-fingerprint-{
-fingerprint-  "id": 1,
-fingerprint-  "url": "https://api.github.com/applications/grants/1",
-fingerprint-  "app": {
-fingerprint-    "url": "http://my-github-app.com",
-fingerprint-    "name": "my github app",
-fingerprint-    "client_id": "abcde12345fghij67890"
-fingerprint-  },
-fingerprint-  "created_at": "2011-09-06T17:26:27Z",
-fingerprint-  "updated_at": "2011-09-06T20:39:23Z",
-fingerprint-  "scopes": [
-fingerprint-    "public_repo"
-fingerprint-  ]
-fingerprint- }

-fingerprint-{
-fingerprint-  "message": "Reguires authentication",
-fingerprint-  "documentation_url": "https://developer.github.com/v3"
             }
-fingerprint
-string
-PATCH /authorizations/:authorization_id
{
  "add_scopes": [
    "repo"
   ],
   "note": "admin script"
 }

PUT /authorizations/client_id/:fingerprint
client_secret-{
client_secret-"client_secret": "abcdabcdabcdabcdabcdabcdabcdabcdabcdabcd",
client_secret-"scopes": [
client_secret-  "public_repo"
client_secret-  ],
client_secret-  "note": "admin script"
client_secret-}

gingrprint

Status: 200 OK
Link: <https://api.github.com/resource?page=2>; rel="next",
      <https://api.github.com/resource?page=5>; rel="last"
      
[
   {
     "id": 1,
     "url": "https://api.github.com/applications/grants/1",
     "app": {
       "url": "http://my-github-app.com",
       "name": "my github app",
       "client_id": "abcde12345fghij67890"
     },
     "created_at": "2011-09-06T17:26:27Z",
     "updated_at": "2011-09-06T20:39:23Z",
     "scopes": [
       "public_repo"
     ]
   }
 ]
 
       


