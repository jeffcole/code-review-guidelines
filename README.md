# Code Review Guidelines

This is an addendum to the excellent [Practical guide for better, faster code reviews][1] by @mawrkus, which is itself a compendium of points drawn from other sources. It contains my own additions of things to keep in mind as pull request authors, reviewers, and as a collaborative team.

[1]: https://github.com/mawrkus/pull-request-review-guide?tab=readme-ov-file#a-practical-guide-for-better-faster-code-reviews

## The Guidelines

See also the [Guidelines] in the aforementioned guide.

[guidelines]: https://github.com/mawrkus/pull-request-review-guide?tab=readme-ov-file#-guidelines

### For Authors

- Review your changes, commit by commit, in the GitHub compare view, _before_ opening a pull request. I've been surprised by how many things I've caught, after looking at my code for days in my editor, just by switching to the different context of GitHub in the browser.
- For each commit that _at all relates_ to the ticket at hand, put the applicable project management tool ticket number somewhere in the commit message. This will make it easier to find changes related to a given ticket in the future.
- Document your changes in the right place. If you're tempted to put something in the pull request description, ask yourself why you wouldn't put it in a commit message. The only things that should go in the PR description are things that _you don't want_ to go in a commit message (this should be exceedingly rare), or that _can't_ go in a commit message, such as screenshots.
- Put a navigable link to the applicable ticket in the PR description.
- See if you can anticipate anything about your changes that might end up being contentious. Explain your reasoning for taking the approach you did, along with any alternatives you explored. This process in-and-of-itself might help you find a better solution.
- Point out specific areas you're unsure about, or would like to solicit feedback on, by commenting on the code in the context of a commit, via the "Commits" page.
- Keep PRs small, and isolate dependent changesets from one another, by creating branches off of earlier branches, by using GitHub's base branch feature. This technique is also known as [stacking diffs].
  > Pull Request page > "Edit" button > "Choose a base branch" select

[stacking diffs]: https://newsletter.pragmaticengineer.com/p/stacked-diffs

### For Reviewers

- Schedule time in your day to review code. Setting aside time ensures that work gets reviewed and keeps things moving. Some folks like to start their day by reviewing pull requests, other prefer to end the day that way, still others like to break up their day with review sometime in the middle. Discover your own preferences and structure your day accordingly.
- After reading the PR description, start reviewing from the "Commits" page. Read through the list of commits first. This will give you an overview of the changeset. It can be valuable to load this context into your brain first. It can prevent cases of suggesting a change on one commit, only to find that the author already made that change themselves in a subsequent commit.
- Review the pull request commit-by-commit, via the "Commits" page. This allows you to provide feedback in the context of a single change. This workflow is also required in order to be able to give feedback on the [atomicity] and order of individual commits.

[atomicity]: https://www.mojotech.com/blog/mojotech-git-workflow/

### For the Team

- Avoid commenting on the "Files changed" pull request view. It divorces each change from the commit in which it was made.
- Code review is **_everyone's_** responsibility. Don't assume that other team members will handle review. Providing technical feedback is the duty of every developer on a team.
- Everyone has something to share. More junior folks can spot low-hanging issues, offloading these from more senior folks, and help keep the review process moving.
- Pull requests are excellent learning tools for everyone involved. Reading through PRs, even after having been merged, is an effective way for folks new to a language or team to level up their technical or domain knowledge, and get a feel for project conventions.
