This page describes how we track issues in the `vscode` repository.

## Popular queries

- [Inbox tracking](https://github.com/Microsoft/vscode/issues?utf8=%E2%9C%93&q=is%3Aopen%20no%3Aassignee%20-label%3Afeature-request%20-label%3Atestplan-item%20-label%3Aplan-item%20-label%3Aextension-candidate)
- [Bugs to be Verified](https://github.com/Microsoft/vscode/issues?utf8=%E2%9C%93&q=is%3Aissue%20label%3Abug%20-label%3Averified%20is%3Aclosed%20-label%3Aduplicate%20-label%3Ainvalid%20) - VS Code only
- [Verification Needed](https://github.com/Microsoft/vscode/issues?q=is%3Aissue+-label%3Averified+is%3Aclosed+label%3Averification-needed) - VS Code only


## Inbox tracking and Issue triage
New issues or pull requests submitted by the community are triaged by a team member. The team rotates the inbox tracker on a weekly basis. A bot assists the inbox tracker.

### Inbox Tracking

The [Inbox query](https://github.com/Microsoft/vscode/issues?utf8=%E2%9C%93&q=is%3Aopen%20no%3Aassignee%20-label%3Afeature-request%20-label%3Atestplan-item%20-label%3Aplan-item%20-label%3Aextension-candidate) contains all the
- **open issues or pull requests** that
- are **not feature requests** nor **test plan items** nor **plan items** nor **extension candidates** and
- have **no owner assignment**.

The **inbox tracker** should do the following initial triage:
- Is the issue **invalid**? Close it and justify the reason.
- Is the issue **a general question**, like *How can I compile TypeScript*? Close it and redirect the user to [Stack Overflow](http://stackoverflow.com/questions/tagged/vscode) with [this message](https://gist.github.com/joaomoreno/960b4f643b2ff09bcdf7).
- Is the issue best covered by an extension then add the `extension-request` label.
- Else, assign the issue to the **owner** of a feature area.
- Note: Assign JS/TS issues to @mjbvz

**Everyone** should do the following secondary triage to their assigned issues (the **inbox tracker** may do some of these steps too, if obvious):
- If an issue needs more info, assign the `needs more info` label, add an assignee (yourself if still unknown) and ask for more information in a comment. (Adding a comment `/needsMoreInfo` lets the bot add the label and a generic comment asking for more info and a review of the issue guidelines.)
- Ensure that the issue has a **type** label, that is, `bug`, `feature-request`, `debt`, `needs more info`
- Ensure that the issue has a **feature-area** label and optionally a sub area, see [Feature Areas](https://github.com/Microsoft/vscode/wiki/Feature-Areas).
- Do a best effort to identify duplicates
- If the issue is a feature-request then the initial owner optionally unassigns himself from the issue. 
- If the issue is an important `bug`, assign an `important` label and optionally mention @microsoft/vscode to get the attention of the entire team.
- If the issue needs to be fixed in this release, assign it to the current milestone (eg: blocks a scenario, completes a new feature, etc.). 
- If needed, follow-up with the author.
- If the issue is a performance issue use some of the questions, experiments, measurements collected here [[Performance Issues]].

#### GitHub issue tracking tip

Use `l` and `a` to quickly edit labels and assignees.  
See a complete list of GitHub shortcuts [here](https://help.github.com/articles/using-keyboard-shortcuts/#issues-and-pull-requests). (Or try pressing `?` when not focusing any input field on GitHub's UI)

### Ongoing Issue Management
- Issues labelled with `needs more information` are automatically closed by the bot when no additional information is provided for 7 days.
- We close issues that we are not planning to work during the next 12 months. (Adding the `*out-of-scope` label lets the bot close the issue and add a generic comment.)

### Issue Types

Issues are classified into following types and the owner of the issues must make sure that the issues are assigned to one of these labels.

- `bug` - the implementation of a feature is not correct
- `feature-request` - request to change the proper implementation of a feature or a request for a new feature that needs to be implemented.
- `under-discussion` - not decided whether the issue is a bug or feature
- `debt` - improve the implementation/architecture
- `needs more info` - not possible to assign a type label due to missing information
- `question` - we should direct questions to SO
- `upstream` - an issue used to track an issue in an upstream component
- `engineering` - an issue used to track changes to the engineering areas
- others - All labels coloured grey (#dcdcdc)


### Planning
During the iteration planning process we use the following sources as input:
- Review feature requests with many reactions.
Issues we plan to work on during an iteration are assigned to the current milestone.

## Filing bugs as development team member
When team members files a bug they perform steps of the inbox tracker for the issue they filed. Therefore bugs filed by the development team do not need to be triaged by the inbox tracker. 
 
## Verification

Issues need to be verified.

Verification is a service that you request from others either implicitly with the `bug`-label or explicitly with the `verification-needed`-label. Find issue that are to be verified with these queries

- [bugs to be verified, VS Code](https://github.com/Microsoft/vscode/issues?utf8=%E2%9C%93&q=is%3Aissue%20label%3Abug%20-label%3Averified%20is%3Aclosed%20-label%3Aduplicate%20-label%3Ainvalid%20)
- [verification needed, VS Code](https://github.com/Microsoft/vscode/issues?q=is%3Aissue+-label%3Averified+is%3Aclosed+label%3Averification-needed)
- [bugs to be verified, all GitHub projects](https://github.com/issues?utf8=✓&q=is%3Aissue+is%3Aclosed+-label%3Averified+label%3Abug+repo%3AMicrosoft%2Fvscode)
- [verification needed, all GitHub projects](https://github.com/issues?utf8=✓&q=is%3Aissue+is%3Aclosed+-label%3Averified+label%3Averification-needed)

Follow the these rules:

1. Query for issues that are to be verified
2. Start with issues you created (filter by `Author`) but didn't close
3. Pick an item
    - Start with setting `verified`-label (prevents duplicate verifications)
    - Verify the issue
    - If you cannot verify the issue due to missing or hard-to-understand repro steps, add a `verification-steps-needed` label and remove the `verified` label
    - If the issue still shows, add the `verification-found`-label and remove the `verified` label
    - Go back to #3

## Duplicates
Duplicate bugs are closed with a comment `duplicates #issue`. Please try to reference an earlier issue **unless** a later issue is more appropriate (has more context, better scenarios, repro steps, etc.).

### Debug type to extension mapping

- `lldb`: `vadimcn.vscode-lldb`
- `gdb`, `lldb-mi`: `webfreak.debug`
- `cppdbg`, `cppvsdbg`: `ms-vscode.cpptools`

## Consistent labels across vscode repositories

Visual Studio Code consists of multiple repositories and we should use consistent work flows and labels across all our repositories.

To establish consistent labels across all our repositories use the [Label Manager](http://www.dorukdestan.com/github-label-manager/) tool.

## Consistent milestones across vscode repositories

To enable planning across repositories all the Visual Studio Code related repositories need to define the same milestones.

## Iteration Planning
We use issues for iteration plans and the wiki for the test plan. 
- Iteration Plans have a label `iteration-plan` with `tasks` [ ] for the different items. The individual items are tracked in existing issues (bugs, feature requests). If there is no existing issue then a new issue with the label `plan-item` is created. Here is an [example](https://github.com/Microsoft/vscode/issues/917).
- We use a wiki page for a test plan. Here is an [example](https://github.com/Microsoft/vscode/wiki/December-Test-Plan).