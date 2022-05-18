# CorrelAid NL Website
This is the repository associated with (the revamp of) our [website](https://correlaid.nl/). 
It is built using [Jekyll](https://jekyllrb.com/) 
and based on the [Feeling Responsive](http://phlow.github.io/feeling-responsive/) theme.

## Approach
Our original website was made by forking the main CorrelAid website made using [Hugo](https://gohugo.io/).
This was a quick way to get a website up and running with a familiar look and feel.
In 2022, we decided to reboot the website. 
With the existing codebase being somewhat messy, we decided to start again from scratch.
The choice to use Jekyll, rather than Hugo, was motivated by its built-in support for website hosting via GitHub.

### How It Works
Our website is hosted with [GitHub Pages](https://pages.github.com/).
It allows us to host a website for free for our [GitHub organisation](https://github.com/CorrelAidxNL).
A special [.io repo](https://github.com/CorrelAidxNL/CorrelAidxNL.github.io) is made.
This creates our [github.io](https://CorrelAidxNL.github.io) website.
We use our DNS service to make this appear under our desired URL, rather than the github one.

This repo holds the code base for generating the website and is where we make changes to it.
It follows a familiar CI/CD framework. 
The idea that any commits to the master branch trigger a rebuild of the website at the _.io repo_. 
The _.io repo_ should be seen in this context more as the deployment environment rather than a regular repo.
It is __not__ to be changed manually.

As mentioned in the intro, the website is made using Jekyll.
This is a static website generator.
Rather than having to code HTML explicitly or have them generated by the server on the fly, 
this approach allows us to work with templates, but all pages are generated upfront when building and deploying. 

### Updating the Website 
If it is your first time updating the website, please first check the section _Getting Started_ below.
The basic recipe for making a change is as follows.
1. Create a new branch on this repo and checkout this new branch locally.
2. Make the desired changes and test locally, i.e. build and deploy on _localhost_.
3. Push the changes to this repo and merge to master branch.
4. Check that your changes are visible in the live website.

Details about how to add certain standard content should be added here.

### Getting Started
Certain standard items from the data science toolkit are assumed here.
* GitHub account with relevant access rights.
* Basic familiarity with git.
* Basic familiarity with [markdown](https://daringfireball.net/projects/markdown/).

In addition, experience with html and css is helpful, but not a must.
The main specific thing to do is to get set-up and familiar with [Jekyll](https://jekyllrb.com/docs/).
At the very least, you will need to install it, clone our repo and make sure you can generate our website locally.
If you want to have some hands-on practice, 
I suggest making your own personal GitHub pages website, which uses an identical approach.
 
If you want to be able to make more significant changes, 
it might also be good to check out the [codebase](https://github.com/Phlow/feeling-responsive) for the theme we are using.