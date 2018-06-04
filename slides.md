---
title: Create your own website with git and github-pages
theme: white
---

### Create your own website with jekyll and github-pages

<img align="center" width="30%" src="https://www.uibk.ac.at/public-relations/grafik_design/images/logo/download/sublogos/institute-sublogos/atmospheric-and-cryospheric-sciences.png"/>

ARMU-DPs Workshop, 05.06.2018

[Fabien Maussion](http://fabienmaussion.info)


---

## How to use these slides

- ``<space>`` : go to the next slide
- ``<shift+space>``: go back
- ``<left right up down arrows>``: navigate through the presentation structure
- ``<esc>``: toggle overview mode

---

## Agenda

- Create a static web-page with [jekyll](https://jekyllrb.com/)
- Learn the basics of the version control system [git](https://git-scm.com/)
- Use git to publish and handle the web page

---

## Static web pages?

- [Why use a static site generator?](https://learn.cloudcannon.com/jekyll/why-use-a-static-site-generator/)
- [Wikipedia: static web page](https://en.wikipedia.org/wiki/Static_web_page)
- [Wikipedia: dynamic web page](https://en.wikipedia.org/wiki/Dynamic_web_page)

----

## Advantages

- Light, fast, cheap and secure
- Full control
- Markdown syntax
- Growing community

----

## Drawbacks

- (No dynamical content)
- Some technical skills required
- Customizable only with css/html knowledge

----

## Examples

- personal website: [fabienmaussion.info](http://fabienmaussion.info/)
- project website: [oggm.org](http://oggm.org/)
- educational website: [transparency-lecture.github.io](https://transparency-lecture.github.io/])

---

## Let's get started!

1. Install [jekyll](https://jekyllrb.com/docs/installation/)
2. Download the default template website:

    ``$ jekyll new my_blog``

3. In the my_blog folder:

    ``$ bundle exec jekyll serve``

3. **That's it!** Open  http://localhost:4000/ in browser

----

```bash
$ jekyll build
# => The current folder will be generated into ./_site
```

<br/>

```bash
$ bundle exec jekyll serve
# => A development server will run at http://localhost:4000/
# Auto-regeneration: enabled. Use `--no-watch` to disable.
# "bundle exec" is optional for simple sites
```

---

## The markdown format

----

### Text

<section style="text-align: left;">

```markdown
## Sub-heading

Paragraphs are separated by a blank line.

Text attributes: _italic_, **bold**, `monospace`.
```

<br/>

## Sub-heading

Paragraphs are separated by a blank line.

Text attributes: _italic_, **bold**, `monospace`.

----

### Images and links

<section style="text-align: left;">

```markdown
![alt](/img/logo_jekyll.png)

This is a [link](http://acinn.uibk.ac.at/).
```

<br/>

![alt](/img/logo_jekyll.png)

This is a [link](http://acinn.uibk.ac.at/).

----

### And more...

Markdown is [well documented](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
and has several flavors, the one used by Jekyll
is [kramdown](https://kramdown.gettalong.org/index.html).

---

<section style="text-align: left;">

### Hands on: a simple page

Create a new file called `research.md` (use `about.md` as template). Adapt
the header at your convenience and add at least one of each:
- title and subtitle
- short text including links
- image (copy it into `/img/`)
- an enumerated list

Repeat with a new blog post.

----

<section style="text-align: left;">

### Hands on: add latex support

<small>
From your site's folder, run:
```bash
$ bundle show minima
```
This gives the location
of the template files used by the theme. Copy

```bash
_includes/head.html
```
to your site's folder.

Add the following line to the file (just before `</head>`):

```html
<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.4/MathJax.js?config=TeX-MML-AM_CHTML' async></script>
```

You should now be able to write latex formulas in your pages/posts!
</small>

---

## Themes

<section style="text-align: left;">

"[gem-based themes](https://jekyllrb.com/docs/themes/)" are the new default
in Jekyll. They simply hide the site's layout in a "gem" folder: these defaults
an be overridden at wish.

Most sites are still "old-school". See [jekyllthemes.org](http://jekyllthemes.org/)
for an overview.

Example theme: [academicpages](https://academicpages.github.io/)

----

<section style="text-align: left;">

### Hands on: use another theme

Download the template from the [repository](https://github.com/academicpages/academicpages.github.io)
(either with git or by direct download).

Run

```bash
$ bundle install  
```

from the site's root directory, followed by a

```bash
$ bundle exec jekyll serve
```

This is a theme with more customization options, but this comes with more
complexity!

---

<section style="text-align: left;">

## One way to publish your site

The `_site` folder is a self-contained, fully functional website. You can
deploy it on your own server or deploy it locally with tools like
python's SimpleHTTPServer.

Most Jekyll users are going to use [github-pages](https://pages.github.com/) though.

---

## Resources

- [Jekyll](https://jekyllrb.com/)
- [Jekyll Academic Quickstart](https://ncsu-libraries.github.io/jekyll-academic-docs/)
- [github-pages](https://pages.github.com/)


---

**The version control system**

![git](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e0/Git-logo.svg/200px-Git-logo.svg.png)

---

## Objectives

- why git?
- git semantics
- basic git workflow with local and remote repository (no branches, no forks)
- more advanced use: workshop in two weeks

----

<section style="text-align: left;">

## Installing git

Linux:

```bash
$ sudo apt install git
```

<br>

Elsewhere:

https://git-scm.com/downloads

<br>

On Windows: use Git Bash!

---

## Version control?

- keep record of changes to files and folders
- keep track of major versions (tags: e.g. V1.3.2) <!-- .element: class="fragment" -->
- allows for collaborative development <!-- .element: class="fragment" -->
- allows you to know who made changes and when (attribution) <!-- .element: class="fragment" -->
- allows you to revert any changes and go back to a previous state <!-- .element: class="fragment" -->

----

## git?

- created in 2005 by a (frustrated) Linus Torvald
- distributed: entire code and history on local and remote machines <!-- .element: class="fragment" -->
- no internet access necessary (except in two urgent situations: <!-- .element: class="fragment" -->
  pushing/pulling and getting help) <!-- .element: class="fragment" -->
- most popular VCS (by far) <!-- .element: class="fragment" -->
- command line tool (but GUIs available) <!-- .element: class="fragment" -->

---

![git xkcd](https://imgs.xkcd.com/comics/git.png)

<small>[xkcd.com](https://xkcd.com/1597/)</small>

---

## git - when?

- managing files where *history* is important: code, latex document, CV
- for **text files** mostly - everything else possible but not optimal
- collaborative work

---

# Semantics

----

## Semantics: snapshot

- picture of how your files look like at a point in time
- you decide when to make a snapshot
- you can *always* go back to old snapshots

----

![snapshots](https://git-scm.com/book/en/v2/images/snapshots.png)

----

## Semantics: commit

- the act of creating a snapshot (verb or noun: *"I commited code"*, *"He just made a new commit"* )
- a project is made up of a lot of commits

----

![gitlog](/img/git-log.png)

----

## A commit contains

1. information about changes to previous commits
2. a reference to the previous (parent) commit
3. a hash code name

----

## Semantics: repository

- a collection of all the files and their history
- contains a ``.git`` folder
- can live on a local machine or a remote server (GitHub, GitLab, BitBucket)

----

## Semantics: cloning

- copying an entire repository from a remote server to a local machine

----

## Semantics: pulling

- downloading commits that don't exist on your local machine from a remote directory

----

## Semantics: pushing

- adding your local changes to the remote repository

----

## Semantics: branch

- all commits live in some branch
- there can be many of them
- the main branch of a project is called **master branch**

----

## Semantics: fork

- a remote copy of a remote directory
- useful for: collaborative work, or for a fresh start (e.g. template websites)

----

## Semantics: hosting service

- where to store your remote repository
- [GitHub](https://github.com/): free for open repositories, most famous (by far),
  just aquired by Microsoft (?)
- [BitBucket](https://bitbucket.org/): free for private repositories, less famous
- [GitLab](https://about.gitlab.com/): not a hosting service - but an open-source
  platform: UIBK has its own deployment (https://git.uibk.ac.at)


---

## Hands-on!

----

## First-time setup

```bash
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
$ git config --global color.ui auto
```

----

## Create an online repository

- create a repository on gitlab: https://git.uibk.ac.at or github
- clone the repository (demo)
- **Alternative:** start from a local (empty) folder: ``$ git init``

----

## Top 5 git commands for beginners

```bash
$ git status
$ git add
$ git commit -a -m ""
$ git push origin master
$ git log
```
----

## Ignoring files

- ``.gitignore`` file

----

Git is best learned "by doing"! Try it at home and come back in two weeks
with questions ;-)

----

## Resources

- [git reference book](https://git-scm.com/book/en/v2)
- [git handbook from github](https://guides.github.com/introduction/git-handbook/)


---

## Github-pages

----

<section style="text-align: left;">

- [github-pages](https://pages.github.com/): service to host your
website as a git repository
- each time you push to the online repository, the website is built and updated <!-- .element: class="fragment" -->
- good: free, easy, custom domains allowed <!-- .element: class="fragment" -->
- bad: all your content is on github.com <!-- .element: class="fragment" -->

----

## Demo + hands-on in five steps

---

# Thank you for your attention!
