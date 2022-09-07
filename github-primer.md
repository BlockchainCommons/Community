# GitHub Primer

Blockchain Commons does much of its work through [GitHub](https://github.com/BlockchainCommons). Not only is it the site for all of our code repositories, but it's also used for documentation and discussions. 

## Creating an Account

In order to interact with GitHub, you _must_ have an account. You can create one through the "Sign Up" button on GitHub.

https://github.com/signup

Though you will have to provide an email, it need not be publicly visible, and you can choose a username that either corresponds with your real name or not, as you prefer.

## An Intro to Repos

Blockchain Commons is an "organization" on GitHub. It contains many "repositories", or "repos". Generally, every individual code base has its own repo: so not only is there a repo for our [Spotbit Server](https://github.com/BlockchainCommons/spotbit) but there are also individual repos for [our lifehash library in C](https://github.com/BlockchainCommons/bc-lifehash) and [our lifehash library in python](https://github.com/BlockchainCommons/bc-lifehash-python), as an example.

Repos are also sometimes used to organize related topics and to hold documents. Major repos at Blockchain Commons include:

* [Gordian](https://github.com/BlockchainCommons/Gordian) — Our architecture, from principles to apps
* [Research](https://github.com/BlockchainCommons/Research) — Our specifications
* [Crypto Commons](https://github.com/BlockchainCommons/crypto-commons) — Our developer resources such as docs & libraries
* [SmartCustody](https://github.com/BlockchainCommons/SmartCustody) — Our responsible key management course
* [Learning Bitcoin from the Command Line](https://github.com/BlockchainCommons/Learning-Bitcoin-from-the-Command-Line) — Our Bitcoin Core tutorial
* [Community](https://github.com/BlockchainCommons/Community) — Administrative info on Blockchain Commons & its procedures

## Engaging in Community

Our repos include community Discussions areas where you can talk about a wide variety of topics.

There are two major Discussions areas at Blockchain Commons:

* [Blockchain Commons](https://github.com/BlockchainCommons/Community/discussions) — Our main discussions area for Blockchain Commons administration
* [Airgapped Wallet](https://github.com/BlockchainCommons/Airgapped-Wallet-Community/discussions) — Our discussion area for interacting with the larger ecosystem, focusing on specifications & advances

## Filing Issues

If you encounter a problem with software or documentation in a repo, but you don't know how to fix it, please file an Issue.

There will be an "Issues" item in the top bar of each repo; just select it and then click the "New Issue" button. 

Include a good Title and as much detail as you can, including specific info on how to replicate the problem (including the platform where the problem occurred and what error message it returned, if appropriate). Also please click on the gear next to the Labels area to help to classify the Issue.

When you're done "Submit New Issue" and it'll go to the developers responsible for the repo.

## Forks, Branches, and Clones

You can also make changes to repos. This allows you to directly correct documentation or code and to make additions to a repo. To do so you have to make your own copy of the repo and edit it. This is the most confusing element of GitHub, because there are a variety of different methods to make copies of repos. Most frequently you will _fork_ a repo and then _clone_ it to your home machine.

But, here's an overview of all the options:

* **Fork.** You can fork a repo by going to the repo in question and hitting the "Fork" button at the top of the page. This will make a copy of the repo into your own GitHub account. Afterward, you can edit it directly within your own account.
* **Clone.** Usually you don't want to be working on a repo at github.com, but instead on your home machine. To do so, you make a clone of the repo on your home machine using GitHub software. To be precise, you should make a clone of the fork that you created.
* **Branch.** GitHub also supports branches, which are variants of a repo, often used to hold in-progress work, such as new, untested code or documentation for a future version of software. You won't usually have to worry about creating branches, but you may be asked to use an existing branch to help segregate your work. In this case, when you create a Fork, you'll uncheck the box that says "Master only", and then when you work on the repo on your local machine, you'll have to change to using that branch.
 
## GitHub Software

If you want to work on a GitHub repo at github.com you can do so using their web-based interface.

However, you'll more often want to work on a repo on your home machine, because it'll allow you to more easily test code, because it's sometimes faster than working across the internet, and because there are some limitations to the web-based GitHub interface (e.g., you can't easily revert). To do so, you'll need GitHub software on your local machine.

* [**GitHub Desktop**](https://desktop.github.com/) is the official GUI for GitHub. You can clone a repo you've forked, make changes with an editor of your choice, and then upload it back to your GitHub account
   * Once you've installed `Desktop`, you should see an "Add" button on the left which you can click to see an option to "Clone Repository".
* **Git Command-Line Tools** are the other major option. See [here](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) for how to install them under a variety of operating systems.
   * Once you've installed Git Tools, you can clone a repo with a command such as: "git clone https://github.com/shannona/Community.git". The exact URL should be available under the green "Code" button on the webpage for your fork.

## Making Changes to a Repo

The primary methodology for editing a repo on your local machine is, as noted, to _fork_ to your own account, then _clone_ to your local machine, then _edit_ using your favorite text editor.

When you're done, the primarily methodology for submitting those changes to the master repo is to _commit_ the changes you've made on your local machine, _push_ them from your local machine to your repo on github.com, and then _pull request_ to ask that your fork be merged into the main branch of the original repo.

The first two steps are both done using the tools you donwloaded to your local machine. 

In `Desktop`, you should be able to write a summary (and optionally description) of your changes, "Commit to Master" and then "Push".

Using Git Tools, you will either, commit an individual file:
```
$ git add [file]
```
Or commit all changes on your local machine:
```
$ git commit -a
```
For example:
```
$ git commit -a
[master f7d2f20] addition to README, mainly as test.
 1 file changed, 4 insertions(+)
```
Afterward, you `git push` your changes. For example:
```
$ git push
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 1.04 KiB | 1.04 MiB/s, done.
Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/shannona/Community.git
   30c025a..f7d2f20  master -> master
```
At that point, your changes will be uploaded to your fork on github.com, but not to the main repo. To merge them in you need to create a "pull request" (PR), which is basically a request to the owner of the original repo that your changes be incorporated.

You can make this request by going to your fork on the repo on github.com, clicking on the "Pull requests" item in the top bar, and then selecting "New pull request".

At that point, you should see a "diff", showing your changes. If they all look proper to you, click "Create pull request". Make any changes to the summary to ensure that you have a clear overview of your changes, write additional descriptions as comments, and then click "Create pull request" (one more time).

You will then see a PR created on the original repo, which will incorporate your changes if the owner of the repo merges it.

(Whew.)

