# Code Review Guidelines

This is an addendum to the excellent [Practical guide for better, faster code reviews][1] by @mawrkus, which is itself a compendium of points drawn from other sources. It contains my own additions of things to keep in mind as pull request authors, reviewers, and as a collaborative team.

[1]: https://github.com/mawrkus/pull-request-review-guide?tab=readme-ov-file#a-practical-guide-for-better-faster-code-reviews

It also contains my answers to the "can you spot which guideline applies?" items in the [Interactions] section of the aforementioned guide.

[Interactions]: https://github.com/mawrkus/pull-request-review-guide?tab=readme-ov-file#-interactions

## The Guidelines

See also the [Guidelines] in the aforementioned guide.

[guidelines]: https://github.com/mawrkus/pull-request-review-guide?tab=readme-ov-file#-guidelines

### For Authors

- Review your changes, commit by commit, in the GitHub compare view, _before_ opening a pull request. I've been surprised by how many things I've caught, after looking at my code for days in my editor, just by switching to the different context of GitHub in the browser.
- For each commit that _at all relates_ to the ticket at hand, put the applicable project management tool ticket number somewhere in the commit message. This will make it easier to find changes related to a given ticket in the future.
- Put a navigable link to the applicable ticket in the pull request description.
- Document your changes in the right place. If you're tempted to put something in the pull request description, ask yourself why you wouldn't put it in a commit message. In general, the only things that should go in the PR description are:
  - things that apply to the overall changeset that don't belong in individual commit messages (again, ask yourself why not duplicate that info in multiple commit messages in order to make it accessible from the Git log);
  - process notes, such as a "follow-up PR coming;" or
  - things that can't go in a commit message, such as screenshots.
- See if you can anticipate anything about your changes that might end up being contentious. Explain your reasoning for taking the approach you did, along with any alternatives you explored. This process in-and-of-itself might help you find a better solution.
- Point out specific areas you're unsure about, or would like to solicit feedback on, by commenting on the code in the context of a commit, via the "Commits" page.
- Keep PRs small, and isolate dependent changesets from one another, by creating branches off of earlier branches, by using GitHub's base branch feature. This technique is also known as [stacking diffs].
  > Pull Request page > "Edit" button > "Choose a base branch" select

[stacking diffs]: https://newsletter.pragmaticengineer.com/p/stacked-diffs

### For Reviewers

- Schedule time in your day to review code. Setting aside time ensures that work gets reviewed and keeps things moving. Some folks like to start their day by reviewing pull requests, other prefer to end the day that way, still others like to break up their day with review sometime in the middle. Discover your own preferences and structure your day accordingly.
- After reading the PR description, start reviewing from the "Commits" page. Read through the list of commits first. This will give you an overview of the total changeset. It can be valuable to load this context into your brain first. It can prevent cases of suggesting a change on one commit, only to find that the author already made that change themselves in a subsequent commit.
- Review the pull request commit-by-commit, via the "Commits" page. This allows you to provide feedback in the context of a single change. This workflow is also required in order to be able to give feedback on the [atomicity] and order of individual commits.

[atomicity]: https://www.mojotech.com/blog/mojotech-git-workflow/

### For the Team

- Avoid commenting on the "Files changed" pull request view. It divorces each change from the commit in which it was made.
- Code review is **_everyone's_** responsibility. Don't assume that other team members will handle review. Providing technical feedback is the duty of every developer on a team.
- Everyone has something to share. More junior folks can spot low-hanging issues, offloading these from more senior folks, and help keep the review process moving.
- Pull requests are excellent learning tools for everyone involved. Reading through PRs, even after having been merged, is an effective way for folks new to a language or team to level up their technical or domain knowledge, and get a feel for project conventions.

## Interactions

In the following interactions, can you spot which guideline applies?

These are from the [Interactions] section of @mawrkus's guide, for purposes of displaying my answers alongside.

See also the [Guidelines] in the aforementioned guide.

### 1

> **Alan**:
> Please don't do this, you are actually creating a layer that the application does not require, and don't say that is temporary, because it isn't.
>
> **Billy**:
> I don't understand.
>
> **Alan**:
> That you don't need the copy-paste that you are doing.
>
> **Billy**:
> Let’s talk, your comment does not help me understand.

<details>
  <summary>Answer</summary>

- [Be respectful] (reviewer)
- [Empathize] (reviewer)
- [Avoid selective ownership] (reviewer)
- [Seek the author's perspective] (reviewer)
- [Stop the "reply" hemorrhage] (all)
</details>

### 2

> **Jamie**:
> Do we really need this? I don’t see the gain.
>
> **Billy**:
> It’s a polyfill used in lazyLoad.js
>
> **Jamie**:
> Yes I got that, but why not importing there instead of here? I know that the import is not executed always in lazyload.js, but I see it weird.. Maybe a require() instead?
>
> **Billy**:
> Good point, I don’t know actually!
> I’ll make some tests.

<details>
  <summary>Answer</summary>

- [Clarify the code first] (author)
- [Be proactive / Provide context] (author)
- [Explain] (author & reviewer)
- [Leave this world a little better than you found it] (author)

</details>

### 3

> **Alan**:
> Maybe it is time to stop the tradition of providing all the arguments as props.

<details>
  <summary>Answer</summary>

- [Explain, Suggest] (reviewer)
- [Provide references] (reviewer)
- [Ensure the best review quality] (reviewer)
- [Agree on a coding style / Automate] (all)
- [Create new tasks] (author)

</details>

### 4

> **Alan**:
> I'm not sure if it's a good idea to return to this, it's a screenshot from project X.
>
> **Billy**:
> It’s not human-friendly indeed. But do we need human-friendly?
>
> **Alan**:
> Yes.
>
> **Jamie**:
> Do you know why?

<details>
  <summary>Answer</summary>

- [Explain] (reviewer)
- [Provide references] (reviewer)
- [Be proactive] (author)
- [Don't be a gatekeeper] (reviewer)
- [Stop the "reply" hemorrhage] (all)

</details>

### 5

> **Evan**:
> Do you want to keep this line?

<details>
  <summary>Answer</summary>

- [Seek the author's perspective] (reviewer)
- [Explain, Suggest] (reviewer)
- [And the first reviewer is... you!] (author)
- [Be proactive] (author)

</details>

### 6

> **Alan**:
> It's not consistent this tracking, because it directly depends on the provided options.
>
> **Billy**:
> Ok, what do you suggest we should do instead?

<details>
  <summary>Answer</summary>

- [Assess your code] (author)
- [Suggest] (reviewer)
- [Be proactive] (author)

</details>

### 7

> **Alan**:
> I can imagine why you are putting this fix here now, but our mission is to make the templates simpler, and the only way to accomplish that is to move all the business logic related to the page to the model. It's a bit more complicated, but this is the way that we need to follow now. There are many benefits of doing that, and one of them is to have tests. If you need some help about it, drop me a message.

<details>
  <summary>Answer</summary>

- [Leave this world a little better than you found it] (author)
- [Improvements have a threshold] (reviewer)
- [Create new tasks] (author)

</details>

[Agree on a coding style / Automate]: https://github.com/mawrkus/pull-request-review-guide?tab=readme-ov-file#agree-on-a-coding-style--automate
[And the first reviewer is... you!]: https://github.com/mawrkus/pull-request-review-guide?tab=readme-ov-file#and-the-first-reviewer-is-you--assess-your-code
[Assess your code]: https://github.com/mawrkus/pull-request-review-guide?tab=readme-ov-file#and-the-first-reviewer-is-you--assess-your-code
[Avoid selective ownership]: https://github.com/mawrkus/pull-request-review-guide?tab=readme-ov-file#avoid-selective-ownership--its-our-code
[Be proactive]: https://github.com/mawrkus/pull-request-review-guide?tab=readme-ov-file#be-proactive--provide-context
[Be proactive / Provide context]: https://github.com/mawrkus/pull-request-review-guide?tab=readme-ov-file#be-proactive--provide-context
[Be respectful]: https://github.com/mawrkus/pull-request-review-guide?tab=readme-ov-file#be-respectful--ask---explain---suggest
[Clarify the code first]: https://github.com/mawrkus/pull-request-review-guide?tab=readme-ov-file#clarify-the-code-first--help-future-developers
[Create new tasks]: https://github.com/mawrkus/pull-request-review-guide?tab=readme-ov-file#rome-wasnt-built-in-a-day--create-new-tasks
[Don't be a gatekeeper]: https://github.com/mawrkus/pull-request-review-guide?tab=readme-ov-file#dont-be-a-gatekeeper--improvements-have-a-threshold
[Empathize]: https://github.com/mawrkus/pull-request-review-guide?tab=readme-ov-file#empathize--the-other-person-is-you
[Ensure the best review quality]: https://github.com/mawrkus/pull-request-review-guide?tab=readme-ov-file#ensure-the-best-review-quality
[Explain]: https://github.com/mawrkus/pull-request-review-guide?tab=readme-ov-file#be-respectful--ask---explain---suggest
[Explain, Suggest]: https://github.com/mawrkus/pull-request-review-guide?tab=readme-ov-file#be-respectful--ask---explain---suggest
[Improvements have a threshold]: https://github.com/mawrkus/pull-request-review-guide?tab=readme-ov-file#dont-be-a-gatekeeper--improvements-have-a-threshold
[Leave this world a little better than you found it]: https://github.com/mawrkus/pull-request-review-guide?tab=readme-ov-file#leave-this-world-a-little-better-than-you-found-it--the-boy-scout-rule
[Provide references]: https://github.com/mawrkus/pull-request-review-guide?tab=readme-ov-file#provide-references
[Seek the author's perspective]: https://github.com/mawrkus/pull-request-review-guide?tab=readme-ov-file#seek-the-authors-perspective--we-always-learn
[Stop the "reply" hemorrhage]: https://github.com/mawrkus/pull-request-review-guide?tab=readme-ov-file#stop-the-reply-hemorrhage--offer-to-talk-in-person
[Suggest]: https://github.com/mawrkus/pull-request-review-guide?tab=readme-ov-file#be-respectful--ask---explain---suggest
