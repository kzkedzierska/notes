# Making changes to the repository (github)

## Basics

Never work on master, if working on new code, fixing bugs or adding features create a new branch. It's importnat to name the branch so it will describe its purpose. There are some guidelines to naming convention, like the ones in this [stack overflow post](https://stackoverflow.com/questions/273695/what-are-some-examples-of-commonly-used-practices-for-naming-git-branches). It's recommended to use grouping tokens, i.e. instead of having following branches:

* fixing_bug_345
* fix_bug_1212
* adding_intermediate_save
* exploring_parallerization
* test2

Group them into few groups. Example of grouping system from this [stack overflow response](https://stackoverflow.com/a/6065944/7636284)

* wip       Works in progress; stuff I know won't be finished soon
* feat      Feature I'm adding or expanding
* bug       Bug fix or experiment
* junk      Throwaway branch created to experiment 

The following example will look like this:

* bug/345
* bug/1212
* feat/intermediate_save
* wip/exploring_parallerization
* junk/test2

There are bunch of other naming convention like *dev* instead of *wip*, *issue* with work related to raised issues etc. There's no right answers. As long as you are consistant, everything will be fine.

To create a branch by simply typing.

git checkout -a NAME_OF_THE_BRANCH


## Merging branches 

After you worked on a project, you tested the code and you feel confident about the changes you made you can create a pull request. 


### Commiting changes 

But first, remeber to commit all your changes. Do it often, as soon as you finish a certain portion of work and describe the changes you made.

```bash
git add * # this will add all files, you can also add selected ones by replacing the * with their paths
git commit -m "descriptive message"
```

 If your commit is related to an issue, and you want to close it - reference it in the commit message by using one of the following words: *close(s/d), fix(es/ed), resolve(s/d)* and putting its number. For examples:

```bash
git add *
git commit -m "Fixed #78" # this will link this commit to the issue and close it
```

### Creating a pull request

After you commit to the repository you should open a pull request, you can do that by following the [step-by-step guide on the help.github.com pages](https://help.github.com/en/articles/creating-a-pull-request).