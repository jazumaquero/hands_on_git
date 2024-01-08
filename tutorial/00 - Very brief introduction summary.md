# Very brief Git fundamentals summary.
## Disclaimer
This repo aims to provide a holistic view about `Git` and how to use it in your day by day work, but on a very human-friendly way and focused more on hands-on learning than a formal explanation of every single concept.
Furthermore when just searching `Learnig Git` in any search engine will provide you a plenty list of learning resources (that probably will be much more accurated than this repo).
In other words, this repo should be considered more a useful tool for practicing `Git`.

What you should expect to find on this repo is how to resolver some version control use cases using `Git`:

* 🧪 How to use branches for testing different approach to solve your daily basis task.
* ♻️ How to re-use code from different branches.
* 💥 How to survive to a _rebase_ with conflicts.
* 🐙How to summon _Cthulhu_ on a merge.

What you should __not__ expect to find in this repo (but maybe worth that you learn by yourself once you feel confortable using `Git`):

* Listing every single `Git` command and their arguments.
* _Silver-bullet_ scripts that will solve very use case specific issue (I am not a Chatbot or GPT-like bot 🤖).

## Before start, please remember that....
### Version control system (VCS) is not a USB-stick
There is a common misconception on many people that start working with software about `VCS`, that usually find this sort of system confusing and more a blocker than a problem solver, 
and this is mainly due to most of them just consider `VCS` as a simple way of recalling previous version of a file, so that, __why not using just a USB-stick instead?__

Remember there are a lot of things you can do with a VCS:

* 🧑‍🤝‍🧑 You can collaborate with other in the same project, not only because working on different branches simplifies work, but also because knowledge sharing becomes easier (just by using `pull-request`).
* 🔍 You can easily compare not only a single file, but also a whole repository in two different moments.
* ☁️ You can easily have your code replicated on different machines with almost no effort in a secure way.

Remember, `Git` is an amazing VCS that will simplify your live when coding!

### When having code versions are not enough
Despite of _trunk based development_ is becoming more a more popular, there are many situations where is required to have separated version of the same project in the same repo.
Those versions is what we call _branches_.

Branching code is quite important on software development, and it is used many situations, among others:

* Simplify having _code reviews_, just by maintaining new code changes in a separate branch until they are ready.
* Simplify having _continuous integration_ (from my point of view, this is just an extension from _code reviews_, where some agent will verify that everything is correct before allowing a merge).
* Provides some mechanism for maintaining several versions from same code. For instance this is used by [GitFlow](https://www.atlassian.com/es/git/tutorials/comparing-workflows/gitflow-workflow).

### What is commit in Git? What about a branch? What about a tag?
_TL;DR._
You must remenber that a __commit__ is mainly 2 things:

* A _patch_ that includes all file differences between 2 versions of code, specifically this version and previous version.
* A _pointer_ to previous version of code, specifically, _pointer to a parent commit_ (or null when it is the first commit in a repo).

In a similar way, you should remember that a __branch__ is just a pointer to a commit! No voodoo magic, just _a pointer_.

Finally, there are some situations when we want the our branches will be inmutable (could not change what commit is being pointed). This special kind of branches are called __tags__, and are mainly used for release versioning.
_Tags_ are not commonly managed directly by developers but by _continuous integration_ system, but are a nice way of finding code in a fast way, specially a way of indicating where an specific release is.

### Local vs remote
On of the main benefit of using a VCS is having a base of code in a centralized server, so base code is shared by different people in a project.
But it is important to remember that usually _people work in asynchronous way_, and `Git` provides some efficient way of doing this: having _local_ and _remote_ versions of the same repository.

So that, code on _remote_ will became the base code will be shared by anyone involved in a project develooment. When some user is versioning new code, this version are stored in _local_, and changes won't appear on remove until a _push to remote_ is performed.
This feature allows to isolate users from other users changes, making collaboration easier. But, ..., there is a tradeoff should be paid: __conflicts__ 😨

### Working Areas
When you work with `Git` there are basically 3 main areas you should take into account:

* __Repository or storing area__: includes all commits, branches, tags, and any sort of files and metadata used. In other words, this is what you get when you clone a remote repository. 
* __Staging area__: include those changes that must be included in next commit.
* __Working area__: includes everything that is on your computer in the git directory. Everything. It also includes all files that are not tracked by `Git`.

`Git` is mainly tracking those files that has been included to the repository at some moment, but it won't track new files. On the other hand, empty directories won't be tracked.

Having in mind aforementioned areas will help you to understand what is happening when you work with `Git` and will help you to not to miss anything on your commits.

We will cover this 3 areas more deeper on first exercise, so, keep calm and hold on.

### Using git command line interface is not mandatory,...
You can currently found nice user interfaces for interacting with `Git`. Furthermore, most used IDEs already include their graphical Git clients, that will simplify your life.

However, there are many situations where using git command line interpreter (or git cli) is a convenient option, among others:

* When git operations are quite simple.
* When there are no user interface available (for instance, when you work in a remote machine using an SSH terminal)
* When you are working on DEV-OPS tasks that requires automating some continuous integration or continuous delivery tasks.

Thus, it is strongly recommended getting familiarized with git cli.

## References
[Git Book English version](https://git-scm.com/book/en/v2/).

[GitFlow](https://www.atlassian.com/es/git/tutorials/comparing-workflows/gitflow-workflow).
