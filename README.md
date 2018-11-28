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


