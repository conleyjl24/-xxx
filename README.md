Hello-World
# Getting started with the API
lf you're looking to automate common tasks back up your or create integrations that
extend GitHub our API has you covered
More information about the API is available in the GitHub Developer documentation.You
can also stay current with API-related news by following the GitHub Developer blog
(*)


# Getting the download count for your releases
You can collect metadata about your Releases via the API
To see how many times a file in a Release was downloaded make a GET reguest to the API
for a single release Within the JSON payload every asset has a key
called download count.

# GET reguest to the API

To see how many times a file in a Release was downloaded make a GET reguest to the API
for a single release Within the JSON payload every asset has a key called download count.
(*)

{
"tag name": "v1.0.0",
"target commitish": "master",
"name": "v10.0",
"body": "Description of the release",
"draft": false,
"prerelease": false

}


# interface X {
#   some field: String!
#   other field: String!
# }

# type Y implements X {
#   some field: String!
#   other field: String!
#   new field: String!
# }
# (*)

Accept
# GraphQL API v4

reguirements.txt
pipfile.lock

application/vnd.github[.version].param[+json]

Mutations are structured like this:

mutation {


mutationName(input: {MutationNameInput!} {


MutationNamePayLood


}

LIST contributors

List contributors to the specified repository and sorts them by the number of commits per contributor
in descending order.This endpoint may return information that is a few hours old because the GitHub

REST API v3 caches contributor data to improve performance.
GitHub identifies contributors by author email address. This endpoint groups contribution counts by GitHub user

which includes all associated email addresses.To improve perfomance only the first 500 author email addresses in
the repository link to GitHub users.The rest will appear as anonymous contributors without associated GitHub user information.

# Referencing and citing content
You can use third-party tools to cite and reference content on GitHub.

# lssuing a persistent identifier for your repository with
# Zenodo

To make your repositories easier to reference in academic litereture you can create persisitent
identifiers also known as Digital Object identifiers(DOLs) You can use the data archiving tool Zenodo

to archive a GitHub repository and issue a DOl for archive
# Tips:

>Zenodo can only access public repositories so make sure the repository you want to archive is public
>if you want to archive a repository that belongs to an organization owner may need to approve access

for the Zenodo application
>Make sure to include a license in your repository so readers know how they can reuse work.

# About

This homepage is maintained by editing files in the git/git.github.io repository on
GitHub.

It is meant to be edited collaboretively like a wiki except that instead of a web form you
get to use a text editor and git.What could be better.

If you want push access contact peff@peff.net and provide your GitHub username.You
may also send patches by mail(and feel free to cc git@vger.kernel.org if appropriate).

# Development

   . Make sure you've got ruby 2 with dev-packages installed
   . subo get install bundler
   . Clone this repo
   . subo apt-get install zliblg-dev # ref[1]
   
   
   . bundle install
   . bundle exec jekyll serve
   
   . browse the site on http://localhost:4000
   
 Based on https://help.github.com/articles/using-jekyll-with-pages/
 
 [1] http://www.nokogiri.org/tutorials/installing_nokogiri.html#ubuntu__debian
 (*)
 
 # Import status
 
 This section includes details about the possible of the status field of the Import Progress
 response.
 
 Animport that does not have errors will progress through these steps:
 
   . detecting the "detection" step of the import is in progress because the reguest did not
   . include a vcs parameter.The import is identifying the type of source control present at the
   . URL.
   
   . importing the "raw" step of the import is in progress.This is where commit data is fetched
   from the original repository.The import progress response will include commit_count(the
   
   total number of raw commits that willbe imported) and percent(0-100,the current
   progress through the import).
   
   mapping the "rewrite" step of the import is in progress.This is where SVN branches are
   converted to Git branches and where author updates are applied.The import progress
   
   response does not include progress information.
   
   . pushing the "push" step of the import is in progress.This is where the importer updates
   the repository on GitHub.The import progress response will include push_percent which is
   
   the percent value reported by git push when it "Writing objects".
   
   . complete the import is complete and the repository is ready on GitHub.
   
   If there are problems you will see one of these in the status field:
   
Reguired{The name of the tag
Specifles the "tag name": "v1.0.0",commitish value that
"is created               "target commitish": "master", from.Can be any
The name of the           "name": "v1.0 0",
Text describing the       "body": Description of the release", tag
true to create a          "draft": false draft
true to identify          "prerelease": false
        }

# About integrations

integrations are tools and services that connect with GitHub to complement and extend
your workflow

You can instal integrations in your personal account or organizations you own You can
also instal GitHub Apps from a third-paty in a specific repository where you have admin

permissions or which is owned by your organization.


