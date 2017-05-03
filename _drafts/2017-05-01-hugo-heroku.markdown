  ---
layout: post
title: "How to run Hugo on Heroku"
date: 2017-05-01
categories:
  - Music
description:
image: /img/musiccode.jpg
image-sm: /img/musiccode.jpg
---

I have some parallel projects that are not related to the coding life. One of them is my collection of short fiction stories. I always wrote them in Portuguese, my native tongue, but lately I decided to venture into some English tales and it has already proved to be a big challenge. But I am learning. In order to stimulate myself in keep going with this project, I decided to publish some of my pieces online and for that I chose [Hugo](#), a static website generator written in [Golang](#).

After having my Hugo project done, with some content, I went to the next natural step in the process: where to publish it. I decided to put a stage website on [Heroku](#) before deciding for a free host solution where I could use my custom domain (currently Heroku would charge me $7/month and I am not keen to spend any money on this project yet).

So here I have the steps I took to run my small blog in Hugo.
I am creating a whole new project to show you each part of it.

## Getting Hugo

I installed Hugo directly from the link source. I am using a Ubuntu 16.04 machine. You can choose the best Hugo release for you operational system [here](https://github.com/spf13/hugo/releases).

`$ wget https://github.com/spf13/hugo/releases/download/v0.20.6/hugo_0.20.6_Linux-64bit.deb
`

Check your version.

`$ hugo version`

I recommend anything higher than version 0.18.


## Creating a Hugo blog locally

Let's the fun begin! So you must create a new folder with your new blog name (in this case, Go Hugo).

`$ mkdir go-hugo`

`$ cd go-hugo`

Create the new blog:

`$ hugo new site .`

`$ la`       

It must have 6 directories and 1 file.

![Folders list](/img/tree-0.jpg)

Then you need to create your first content.

`$ hugo new content/post/first-post.md`

(OR you can simply download [these files](https://github.com/spf13/hugo/tree/master/examples/blog/content/post) from Github and move them to your `/content` folder).

By what I read on the Hugo themes, all .md files in the content folder root are pages.

If you open this new `first-post.md` file in your code editor (Atom, Sublime, Vim or Gedit, etc) you can edit its metadata by adding this to the top of the file:

```
+++

title = "My first post"   
date = "2017-01-01T14:11:55+09:00"

+++

Your content goes here (and you must use that old and nice markdown).
[There is a cheatset here] (https://github.com/adam-p/markdown-here/wiki/Markdown-Here-Cheatsheet)
```

## Hugo customization and serve

Add a theme to your Hugo blog. I am taking the Tropic theme as our example.

`$ git clone https://github.com/halogenica/beautifulhugo.git themes/beauty `

After this last step in your configuration, your blog is ready to be run.

`$ hugo server --theme=beauty`

Check your new blog on your browser by typing `http://localhost:1313`.

![Running new website](/img/hugo-run-0.png)



## Build and deploy Hugo on Heroku

I assume that you already have an account on Heroku at this point. If not, you must create one to go further in this tutorial.

- create .hugotheme with git theme path inside.
--- example

.change config.toml
edit the defautl utl (https://go-hugo.herokuapp.com)

`$ git init`

`$ git add -a`

`$ git commit -m "this is a commit but could also be the flying spaghetti monster"`

`$ heroku login`

`heroku git:remote -a go-hugo`

Success message:
`set git remote heroku to https://git.heroku.com/go-hugo.git`

heroku create --buildpack https://github.com/roperzh/heroku-buildpack-hugo.git



`git push heroku master`
