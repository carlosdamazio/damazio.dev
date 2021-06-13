---
title: Yet another blogging reboot 
summary: About my reasons to start on blogging my stuff and how to create one using Hugo.
publishDate: 2021-05-25
images:
  - /img/post-hello/hello.png
slug: hello-world
tags: ["general"]
aliases: [
  "/blog/hello-world"
]
draft: false

---

Hey folks! Here we are again, you reading another blogging reboot post from my blog, and me, trying to handle
it.

At first, as always, I was a bit conflicted with the idea of maintaining or expose my knowledge
or my process of acquiring it to public. Neither was something comfortable or that I 
had some kind of drive to it, I was compeled to it due to the many attempts in doing so. It was a bit scary
and overwhelming to be subjected to judgement from others regarding your knowledge. Scary, doesn't it?

Yelp, not anymore.

For many years, I've been struggling with mental health issues, I took for about 6
years to start on recovery and get some proper treatment. Nowadays, I'm great and I have
healthy ways on cope with my issues. This is another topic for another post, but I can guarantee that I'm able to
start over and bring something to the table with my perspective, without fear or resentment.

## Reasons to start over

YMMV. Not everyone is up to the task of blogging, getting yourself exposed and bringging something
to others. My purpose is not being what we call "digital influencer", neither being 
altruistic and hugging a tree afterwards. This all started due to reading about [Learn in Public]()
and how can we take advantage of it to leverage our learning game (thanks for the recommendation, [Gilson]()).

Since the day that I've came to know I am who I am, I do really love Computer Science and I love to study it.
There are several projects and things that I've worked on, but I took them for granted and lost 60% of those
things due to a problem we call *taking things for granted in our memory*. And when I try to explain these
things that I've worked/currently working to my peers, potential employers and etc, I've found it incredibly
difficult. With that in mind, this is going to be a great tool to unload this experiences and findings on my
learning process, and to teach others to do the same that I did.

Again, this is not for the sake of helping others. To summarize my purpose of doing what I'm
doing for now, they're, at least, for:

- Learn more;
- Lessen my weaknesses by practicing them.

## How can I do the same?

I really recommend you do two things by now:

- Read more about [Learn in Public]()
- Find your inner purposes on doing things.

Sure, everybody wants to be noted by others based on their craft. But let me take a moment to
be blunt about something here: Fame, money and attention are easily attainable and they take
less work than to write a serious technical blog. But seriously, you can ask yourself 2 questions:

- Do you want to learn about topics you want to master?
- Do you want to help others while you're doing that?

There's no right answer. If you get at least a yes in one of them, you're good go. Regardless,
you don't even need a reason at all. You'll never know unless you try it, and I'll give you a little push
to it. :)

## How to create a static blog with Hugo

A long time ago, I was using Jekyll to create one of my first blogs. Initially, it fulfilled my needs,
but it really upset me to use something that I couldn't extend it due to being written in a language
that I didn't have any kind of interest, like Ruby. And the themes were awful.

So then, I found that [Hugo]() fits like a glove. I was creating a prototype with Wagtail, but it seemed
a bit overkill for me to create a blog and a resume page with it. So, Hugo it is, and along with the
[colordrop]() theme that Humberto created, it made the blog project cool.

Now I'm going to show a step by step on how to create a blog project with colordrop theme. I'm using Arch with Pacman package manager.

[Download Hugo](https://gohugo.io/getting-started/installing) to your preferred distribution/Windows/macOS:

{{< highlight console >}}
$ sudo pacman -Syu hugo
{{</highlight>}}

After that, create a directory, initialize a Git repository and type hugo. To use the colordrop theme,
we'll need to import the theme as a submodule.

{{< highlight console >}}
$ mkdir meu-blog 
$ git init 
$ hugo
$ git submodule add git@github.com:humrochagf/colordrop.git themes/colordrop
{{</highlight>}}

Add colordrop theme as a current theme to your blog configuration file.

{{< highlight yaml "hl_lines=4">}}
baseURL: https://damazio.dev/
DefaultContentLanguage: en
title: Carlos Damázio
theme: colordrop
enableRobotsTXT: true
{{< / highlight>}}

Don't forget to fully configure as said by Hugo and colordrop docs.

Run Hugo server to see the magic happen. Acesse o http://localhost:1313.

{{< highlight console >}}
$ hugo server -D
{{< / highlight >}}

Don't forget to import a remote repository to your local repository and commit everything you've done so far.

{{< highlight console >}}
$ git remote add origin git@github.com:seu_username/seu_repo.git
$ git add -A
$ git commit -m "feat: initial blog structure"
$ git push origin main
{{< / highlight >}}

I recommend you use [Netlify](https://app.netlify.com/) to publish your blog. With that, you're good to
go, congrats!

Well, that's a plenty for an introduction of what I'll try to bring to you in the regards of
information. See ya on the next posts, there are some good stuff coming up! ;)

