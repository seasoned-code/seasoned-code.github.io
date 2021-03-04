---
layout: post
title: git - yet another flow
category: code
tag: git
excerpt_separator:  <!--more-->
---
<script src="{{ site.gitgraph.src }}"></script>

### Another Git Flow

Since the title of this article starts with the word 'git' my team's source control solution is git.

I wanted to make a post about what we do on my team for a while. It's been in response to this relatively recent <a href="https://georgestocker.com/2020/03/04/please-stop-recommending-git-flow/" target="_blank">post</a>. With my team, we do not use "GitFlow", however we _do_ follow a flow and pattern.


#### Branch Arrangement

We have a CI/CD (Continuous Integration/Continous Deployment) arrangement. I can go more into that detail at another time. However, that pretty much sets the stage that we have a main line branch, in our case, **master**. All _Feature_ and past _Release_ branches are created off of **master**.

**master** contains _all_ known history on the application's life and branches. When we make a Sprint-End Release we will **tag** the release number on the commit.

_Feature_ branches are traditionally short running branches that contain the new set of features to complete a work requirement or "story."

_Release_ branches are long running branches that are theoretically _not_ temporary.

<div id="git-container"></div>

<script>
      // Get the graph container HTML element.
    const graphContainer = document.getElementById("git-container");

    // Instantiate the graph.
    const gitgraph = GitgraphJS.createGitgraph(graphContainer,
    {
      author: 'Seasoned Code <no-reply@seasoned-code.com>'
    });

    // Simulate git commands with Gitgraph API.
    const master = gitgraph.branch("master");
    master.commit("Merged PR 1235: This is the best release-- evar!");
    master.tag("release-20.3.121")

    const release20_3 = master.branch("release-20.3");

    master.commit("Merged PR 1236: Prepping 20.4 release");
    const aFeature = master.branch("a-new-feature");
    aFeature
      .commit("This better work")
      .commit("Okay, this is the best!")
      .commit("PR Prep");

    release20_3.commit("Merged PR 1237: Post release HotFix").tag("release-20.3.122")

    master.merge(release20_3, "Merged HotFix - 20.3.122");

    master.merge(aFeature, "Merged PR 1238: A better feature");

</script>

#### Feature Branches

While developing the developer can commit as many times as they would like and push up their changes to their remote (in our case _origin_). When the work is complete, a PR (Pull Request) is created and is up for review to be merged into **master**. After the review is complete the branch is _<a href="https://git-scm.com/docs/git-merge#Documentation/git-merge.txt---squash" target="_blank">Squash Merged</a>_. We do not need all of that developer commit history and it will clutter up the branch history. It makes traversing history very easy to find the culprit of an issue in the event there is one (such as using _bisect_). If necessary, create multiple Pull Requests to keep your commits small.
  * _rebase_ frequently off your target branch.
  * refrain from using a _merge_ as we prefer <a href="https://git-scm.com/docs/git-merge#Documentation/git-merge.txt---ff" target="_blank">fast-forward</a> merges, with the exception of the PR.

#### Release Branches

We have a GA (General Availability) release about 3-4 times a year. Before we increment the version number off the **master** branch we will create a _Release_ branch. Any future "hotfixes" will run off this branch. In the event of a hotfix, the _Release_ branch acts as a "master" branch. The _Feature_ branch will be created off of _Release_ and a PR will be made to the _Release_ as a _squash merge_. When testing has vetted the changes and we are ready for a release we will _merge_ back to **master**.
  * _merge_ _Release_ into **master** and **tag** the _HEAD_ commit on the _Release_ branch.
    * Since the _Release_ branch is a long-running branch this is _ideally_ the only time a _merge_ is necessary.
  * **DO NOT** rebase the _Release_ branch off of **master** if the latter branch has already been incremented.
  * Ideally, **DO NOT** make a change in **master** first and then cherry-pick it to the _Release_ branch. You will have conflicts in the event you ever need to merge back to **master** because you will then have a copy of a commit already in **master** which will be hard to track.

#### Long Running Feature Branches

There comes a time when you might want to have a longer running Feature Branch that you will want to have periodic review and custom builds on without the worry of it heading into **master**. In this case, you will treat _this_ Feature Branch as a "master" and create sub-feature branches off _this_ branch. 
  * PR the sub-feature branch into _this_ branch.
  * Periodically, you will rebase _this_ branch off of **master**, but ideally only when there are no sub-feature branches present.
    * If there are sub-feature branches still uncommitted to _this_, extra care will need to reset said sub-feature branch and cherry-pick range the commits from which have been a WIP (work-in-progress). Essentially performing one's own _rebase_ since the typical way will not be possible (the source branch history changes).
  * When the Long Running Feature Branch has run its course or is ready for an incremental inclusion to **master** perform a rebase of the Long Running Feature Branch and fast-forward merge back into **master**.
    * At this point you can either remove the Long Runnning Branch or continue more work.
  * Long running Feature Branches requires _very good_ communication with the team working on _this_ branch.

### Closing

That is really it. The process is relatively easy to handle and easy to read and follow through an entire application's lifecycle. If your team does not have need for a Long Running Feature branch, do not feel to use _that_ flow, but it can be handy for a sub-team to work on a feature that may cause many breaking changes throughout the application. Naturally, it will require your team to have some discipline on making some good choices when problems arise, but otherwise a tried and true method. We have been following this flow for about 3 years with very little hitch.