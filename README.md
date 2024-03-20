# CorrelAid NL Website

This is the repository associated with (the revamp of) our [website](https://correlaid.nl/).
It is built using [Jekyll](https://jekyllrb.com/)
and based on the [Vonge Template](https://jazzed-kale.cloudvent.net/) theme.

## Approach

Our original website was made by forking the main CorrelAid website made using [Hugo](https://gohugo.io/).
This was a quick way to get a website up and running with a familiar look and feel.
In 2022, we decided to reboot the website.
With the existing codebase being somewhat messy, we decided to start again from scratch.
The choice to use Jekyll, rather than Hugo, was motivated by its built-in support for website hosting via GitHub.
Unfortunately it turns out that our choice of template includes some packages that GitHub Pages does not support.
The list of packages can be found [here](https://pages.github.com/versions/). 
The naming of this page is unhelpful, but for things to work automatically, don't use something not on this list.
At the time of writing, they also do not have a meaningful build error message when using an unsupported package.
Fortunately there is a way around this which will be explained below.
The sharper reader may now realise that the original rationale for using Jekyll is somewhat undermined by this issue.

### How It Works

Our website is hosted with [GitHub Pages](https://pages.github.com/).
It allows us to host a website for free for our [GitHub organisation](https://github.com/CorrelAidxNL).
A special [.io repo](https://github.com/CorrelAidxNL/CorrelAidxNL.github.io) is made.
This creates our [github.io](https://CorrelAidxNL.github.io) website.
As owners of the [CorrelAid.nl](https://www.correlaid.nl) domain, we can make this appear at our preferred URL.

This repo holds the code base for generating the website and is where we make changes to it.
It follows a familiar CI/CD framework.
The idea that any commits to the master branch will trigger a redeployment of the website.
I deliberately say _redeployment_ here rather than _rebuild_ because we need to build the website locally ourselves.

As mentioned in the intro, the website is made using Jekyll.
This is a static website generator.
Rather than having to code HTML explicitly or have them generated by the server on the fly,
this approach allows us to work with templates, but all pages are generated upfront when building and deploying.
We are using a free Jekyll template made by [Cloud Cannon](https://cloudcannon.com/).
However, we are not using their interface or services to maintain the website.

### Updating the Website

If it is your first time updating the website, please first check the section _Getting Started_ below.
The basic recipe for making a change is as follows.

1. Create a new branch on this repo and checkout this new branch locally.
2. Make the desired changes and test locally, i.e. build and deploy on _localhost_. 
   The cmd line command for this is "bundle exec jekyll serve".
   You need to execute this from the 'site' sub-folder rather than the root directory.
   This command builds the website in the _\_site_ subfolder with your localhost of the root URL.
   The command prompt should give you a link with the server address so that you can check the website in the browser.
3. If you are happy with the result locally, then you need to locally prepare for deployment on the server.
   On the server, the _\docs_ folder will effectively be copy/pasted for deployment.
   To make a deployment ready version of the website, rebuild the website with the command "bundle exec jekyll build -d ../docs".
   This command (with build NOT serve) takes the actual URL of our website (correlaid.nl) as the root URL.
   If we didn't do this, and just used 'serve', we end up with references to localhost appearing on the website and some broken links.
   The '-d ../docs' part of the command sets the build destination to the _docs_ folder.
   GitHub pages only supports deployment from either the root or docs folder for some reason.
4. Push the changes to origin and merge to master branch.
5. Check that your changes are visible in the live website.

The most common change you are going to make is adding a new post to the website.
Here we assume this is a regular blog post, but for other content the process is similar.
1. In the _site_ folder (note the lack of _), go to the _collections_ folder. 
   In this example we pick the _\_posts_ section.
   At the time of writing, the only other option for adding additional basic content is the _\_projects_ section.
2. Take the latest post file, copy it and rename it in a logical way inline with the file naming convention. 
3. Adjust the content to fit your post and upload the image files you are using to the _images_ folder.

Further details about how to add certain standard content should be added here.

### General Tips

Sometimes websites don't work as you expect, welcome to the world of front end development! Here are some tips.

- **Cache**. To avoid continuously downloading the same files, browsers make extensive use of caching.
  This means that a change to an existing file will not be immediately visible,
  since the browser will simply serve the old version of that file from the cache rather than downloading the new one.
  To see you changes when this happens, do a hard refresh of the page (e.g. ctrl-shirt-r for Firefox on Windows.)
- **Tags**. The website allows you to assign tags to posts which are then displayed with the post as a link.
  This allows users to easily navigate to other posts on the same topic.
  However, the system automatically capitalises the first letter and doesn't support spaces.
  Please only use single word tags to avoid broken links or strange formatting.
- **Build Locally**. Since we are using packages not supported by GitHub Pages, we cannot build on the server.
  Please check that the instructions in the section _Updating the Website_ have been fully followed.
  If you haven't copied the newly made website files to the _docs_ folder, then it will redeploy the old version.
  If you haven't added the empty _.nojekyll_ file to the root of the _docs_ folder it will fail to build on the server.
  If you haven't built the website using the build command (i.e. using serve instead), then we will get references to localhost and broken links.
- **Case Sensitivity**. Behaviour can be inconsistent with regards to the cases of filenames and their extensions.
  To avoid a gotcha with filenames, make sure the extensions are in lower case.

### Getting Started

Certain standard items from the data science toolkit are assumed here.

- GitHub account with relevant access rights.
- Basic familiarity with git.
- Basic familiarity with [markdown](https://daringfireball.net/projects/markdown/).

In addition, experience with html and css is helpful, but not a must.
The main specific thing to do is to get set-up and familiar with [Jekyll](https://jekyllrb.com/docs/).
If you want to have some hands-on practice with Jekyll,
I suggest making your own personal GitHub pages website, which uses an identical approach.

Beyond installing Jekyll, there are two other dependencies for the specific template we are using.
This template uses Node.js which you can download and install from [here](https://nodejs.org/en/download/).
You may also need to set up [Jekyll Watch](https://github.com/CloudCannon/jekyll-watch),
but whether this is truly necessary is still to be verified by a new user.
You of course need to clone this repo, and then make sure you can build and run the website locally.

If you want to be able to make more significant changes,
it might also be good to check out the [codebase](https://github.com/CloudCannon/vonge-jekyll-bookshop-template) for the theme we are using.

An alternative approach to installing involved the following and is included here in case of further assistance to new users.

```bash
$ npm install
```

Install the Jekyll dependencies with [Bundler](http://bundler.io/):

```bash
$ cd site
$ npm run install-jekyll
```

Run the website:

```bash
$ npm start
```
