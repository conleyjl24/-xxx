# Hello-World
# the-knight-is-the-winner
# creating magic code
# for universal use

# the creation of a knight the winner
# with perfect code

•	Version 
•	Contact Support
•	Return to GitHub
Collaborating with issues and pull requests / About pull requests
 
About pull requests
Pull requests let you tell others about changes you've pushed to a branch in a repository on GitHub. Once a pull request is opened, you can discuss and review the potential changes with collaborators and add follow-up commits before your changes are merged into the base branch.
Note: When working with pull requests, keep the following in mind:
•	If you're working in the shared repository model, we recommend that you use a topic branch for your pull request. While you can send pull requests from any branch or commit, with a topic branch you can push follow-up commits if you need to update your proposed changes.
•	When pushing commits to a pull request, don't force push. Force pushing can corrupt your pull request.
After initializing a pull request, you'll see a review page that shows a high-level overview of the changes between your branch (the compare branch) and the repository's base branch. You can add a summary of the proposed changes, review the changes made by commits, add labels, milestones, and assignees, and @mention individual contributors or teams. For more information, see "Creating a pull request."
 
Once you've created a pull request, you can push commits from your topic branch to add them to your existing pull request. These commits will appear in chronological order within your pull request and the changes will be visible in the "Files changed" tab.
Other contributors can review your proposed changes, add review comments, contribute to the pull request discussion, and even add commits to the pull request.
You can see information about the branch's current deployment status and past deployment activity on the "Conversation" tab. For more information, see "Viewing deployment activity for a repository."
After you're happy with the proposed changes, you can merge the pull request. If you're working in a shared repository model, the proposed changes will be merged from the head branch to the base branch that was specified in the pull request. For more information, see "Merging a pull request."
If status checks are required for a repository, the required status checks must pass before you can merge your branch into the protected branch. For more information, see "About required status checks."
You can close corresponding issues using a keyword in your pull request or commit message. For more information, see "Closing issues using keywords."
Tips:
•	To toggle between collapsing and expanding all outdated review comments in a pull request, hold down alt and click Show outdated or Hide outdated. For more shortcuts, see "Using keyboard shortcuts."
•	You can squash commits when merging a pull request to gain a more streamlined view of changes. For more information, see "About pull request merges."
You can visit your dashboard to quickly find links to recently updated pull requests you're working on or subscribed to. For more information, see "About your personal dashboard."
Further reading
•	"Pull request" in the GitHub Glossary
•	"About branches"
•	"Commenting on a pull request"
•	"Merging a pull request"
•	"Closing a pull request"
•	"Deleting unused branches"
•	"About pull request merges"
•	 Contact a human
Article versions
•	GitHub.com
•	GitHub Enterprise 2.15
•	GitHub Enterprise 2.14
•	GitHub Enterprise 2.13
•	GitHub Enterprise 2.12

Ordered
1. Item 1
1. Item 2
1. Item 3
   1. Item 3a
   1. Item 3b

Markdown is a lightweight and easy-to-use syntax for styling all forms of writing on the GitHub platform.
What you will learn:
•	How the Markdown format makes styled collaborative editing easy
•	How Markdown differs from traditional formatting approaches
•	How to use Markdown to format text
•	How to leverage GitHub’s automatic Markdown rendering
•	How to apply GitHub’s unique Markdown extensions
What is Markdown?
Markdown is a way to style text on the web. You control the display of the document; formatting words as bold or italic, adding images, and creating lists are just a few of the things we can do with Markdown. Mostly, Markdown is just regular text with a few non-alphabetic characters thrown in, like # or *.
You can use Markdown most places around GitHub:
•	Gists
•	Comments in Issues and Pull Requests
•	Files with the .md or .markdown extension
For more information, see “Writing on GitHub” in the GitHub Help.
Examples
•	Text
 
•	Lists
 
•	Images
 
•	Headers & Quotes
 
•	Code
 
•	Extras
It's very easy to make some words **bold** and other words *italic* with Markdown. You can even [link to Google!](http://google.com)
It's very easy to make some words bold and other words italic with Markdown. You can even link to Google!
Syntax guide
Here’s an overview of Markdown syntax that you can use anywhere on GitHub.com or in your own text files.
Headers
# This is an <h1> tag
## This is an <h2> tag
###### This is an <h6> tag
Emphasis
*This text will be italic*
_This will also be italic_

**This text will be bold**
__This will also be bold__

_You **can** combine them_
Lists
Unordered
* Item 1
* Item 2
  * Item 2a
  * Item 2b
Ordered
1. Item 1
1. Item 2
1. Item 3
   1. Item 3a
   1. Item 3b
Images
![GitHub Logo](/images/logo.png)
Format: ![Alt Text](url)
Links
http://github.com - automatic!
[GitHub](http://github.com)
Blockquotes
As Kanye West said:

> We're living the future so
> the present is our past.
Inline code
I think you should use an
`<addr>` element here instead.
GitHub Flavored Markdown
GitHub.com uses its own version of the Markdown syntax that provides an additional set of useful features, many of which make it easier to work with content on GitHub.com.
Note that some features of GitHub Flavored Markdown are only available in the descriptions and comments of Issues and Pull Requests. These include @mentions as well as references to SHA-1 hashes, Issues, and Pull Requests. Task Lists are also available in Gist comments and in Gist Markdown files.
Syntax highlighting
Here’s an example of how you can use syntax highlighting with GitHub Flavored Markdown:
```javascript
function fancyAlert(arg) {
  if(arg) {
    $.facebox({div:'#foo'})
  }
}
```
You can also simply indent your code by four spaces:
    function fancyAlert(arg) {
      if(arg) {
        $.facebox({div:'#foo'})
      }
    }
Here’s an example of Python code without syntax highlighting:
def foo():
    if not bar:
        return True
Task Lists
- [x] @mentions, #refs, [links](), **formatting**, and <del>tags</del> supported
- [x] list syntax required (any unordered or ordered list supported)
- [x] this is a complete item
- [ ] this is an incomplete item
If you include a task list in the first comment of an Issue, you will get a handy progress indicator in your issue list. It also works in Pull Requests!
Tables
You can create tables by assembling a list of words and dividing them with hyphens - (for the first row), and then separating each column with a pipe |:
First Header | Second Header
------------ | -------------
Content from cell 1 | Content from cell 2
Content in the first column | Content in the second column
Would become:
First Header	Second Header
Content from cell 1	Content from cell 2
Content in the first column	Content in the second column
SHA references
Any reference to a commit’s SHA-1 hash will be automatically converted into a link to that commit on GitHub.
16c999e8c71134401a78d4d46435517b2271d6ac
mojombo@16c999e8c71134401a78d4d46435517b2271d6ac
mojombo/github-flavored-markdown@16c999e8c71134401a78d4d46435517b2271d6ac
Issue references within a repository
Any number that refers to an Issue or Pull Request will be automatically converted into a link.
#1
mojombo#1
mojombo/github-flavored-markdown#1
Username @mentions
Typing an @ symbol, followed by a username, will notify that person to come and view the comment. This is called an “@mention”, because you’re mentioningthe individual. You can also @mention teams within an organization.
Automatic linking for URLs
Any URL (like http://www.github.com/) will be automatically converted into a clickable link.
Strikethrough
Any word wrapped with two tildes (like ~~this~~) will appear crossed out.
Emoji
GitHub supports emoji!      
To see a list of every image we support, check out the Emoji Cheat Sheet.








