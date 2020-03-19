# ARROW

## Contributing

<!--What the common contributing model is, give overview of JIRA -->

### Merging Model

<!--Discuss SPARK and ARROW's merging model. Refer to script that is being used-->

Apache Arrow uses a similar process to Apache Spark in that items are brought in, in complete
patches. A PR relates to a specific JIRA issue and then this is reviewed. If successfull, the
`dev/merge_arrow_pr.py` script is run which formats the git log message.

Recently it was decided to drop the listing of squash commits in the merged PR git logs:

```diff
12:39:38 ✔ ~/Github/forks/arrow (master) :: git log -p dev/merge_arrow_pr.py
commit 5ca82175e9c06b1f3308fb07544c3f4812b613fa
Author: Wes McKinney <wesm+git@apache.org>
Date:   Tue Mar 10 13:05:12 2020 -0700

    ARROW-7530: [Developer] Do not include list of PR commits in commit message when using PR merge tool

    We've been including these since the beginning of the project, but my sense from reading commit logs is that they add noise and little extra information to our commit log. Since the commit message links back to the original PR, if someone is interested in looking at the evolution of a PR, they can look at the PR in the GitHub UI.

    I got this from Apache Spark originally (IIRC) and Spark has also stopped including the commit messages in their merges.

    Closes #6565 from wesm/ARROW-7530 and squashes the following commits:

    60020d1ca <Wes McKinney> Do not include list of commits in PR message when merging

    Authored-by: Wes McKinney <wesm+git@apache.org>
    Signed-off-by: Neal Richardson <neal.p.richardson@gmail.com>

diff --git a/dev/merge_arrow_pr.py b/dev/merge_arrow_pr.py
index 92fb628bb..39214c19c 100755
--- a/dev/merge_arrow_pr.py
+++ b/dev/merge_arrow_pr.py
@@ -367,9 +367,6 @@ class PullRequest(object):
             # If there is only one author, do not prompt for a lead author
             primary_author = distinct_authors[0]

-        commits = run_cmd(['git', 'log', 'HEAD..%s' % pr_branch_name,
-                          '--pretty=format:%h <%an> %s']).split("\n\n")
-
         merge_message_flags = []

         merge_message_flags += ["-m", self.title]
@@ -400,12 +397,8 @@ class PullRequest(object):
         # close the PR
         merge_message_flags += [
             "-m",
-            "Closes #%s from %s and squashes the following commits:"
+            "Closes #%s from %s"
             % (self.number, self.description)]
-        for c in commits:
-            stripped_message = strip_ci_directives(c).strip()
-            merge_message_flags += ["-m", stripped_message]
-
         merge_message_flags += ["-m", authors]

         if DEBUG:

```

This has the effect that git logs such as:

```bash
commit 8d967d04e45a1a8204d6c1faf8316cfe27256919
Author: Krisztián Szűcs <szucs.krisztian@gmail.com>
Date:   Thu Mar 12 20:51:50 2020 +0100

    ARROW-8097: [Dev] Comment bot's crossbow command acts on the master branch

    It changes the previous behavior to clone the repository and branch referenced by the pull request as arrow and execute its crossbow command with its configuration files.

    Closes #6599 from kszucs/ARROW-8097 and squashes the following commits:

    19475471f <Krisztián Szűcs> use the crossbow.py from the PR
    7868d3911 <Krisztián Szűcs> move into the context mngr
    7cbb68368 <Krisztián Szűcs> use clone_url instead of the url referencing the api endpoint
    b08caee0a <Krisztián Szűcs> clone arrow again with the PR's reference

    Authored-by: Krisztián Szűcs <szucs.krisztian@gmail.com>
    Signed-off-by: Krisztián Szűcs <szucs.krisztian@gmail.com>

```

are no longer a thing, i.e. the:

```bash
...squashes the following commits:

19475471f <Krisztián Szűcs> use the crossbow.py from the PR
7868d3911 <Krisztián Szűcs> move into the context mngr
7cbb68368 <Krisztián Szűcs> use clone_url instead of the url referencing the api endpoint
b08caee0a <Krisztián Szűcs> clone arrow again with the PR's reference
...
```

Apache Arrow Explained by Dremio
https://www.dremio.com/apache-arrow-explained/
