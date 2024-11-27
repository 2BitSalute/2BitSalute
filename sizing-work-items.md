---
layout: default
permalink: /articles/sizing-work-items
---

# Work Items vs. Area Paths in Azure DevOps

## TL;DR
The different work item types are supposed to represent the *time hierarchy*, **not** the *product hierarchy*.

**Instead of using work item types to represent product and feature hierarchy, use area paths**.

Not every user story has to have a parent epic or feature.

## Sizing

| Work Item Type | Time Scale |
|--|--|
| Epic | Semesters (months) |
| Feature/Milestone | Quarters (months) |
| User Story | Sprints (weeks) |
| Task | Hours or days; the smaller the better |

Roughly, you will come up with large and small chunks of work during planning or when an urgent need arises. The large chunks of work are epics, and the small ones are user stories. Features can be used user stories into epic milestones.

Epics have to be further broken down into user stories so they can be more easily reasoned about, scheduled, and prioritized.

User stories should be further broken down into tasks. This can be done as part of sprint planning. A large benefit of smaller work items is that they are much easier to estimate accurately. Another benefit is that creating small work items forces us to think through the implementation better. A small benefit is that tasks will show up on the Kanban board, while user stories will not. Whatever your motivation, you should try to break down work into small chunks.

Plenty has been written about this topic. Here's one classic post by Joel Spolsky of the Stack Overflow fame: [Painless Software Schedules](https://www.joelonsoftware.com/2000/03/29/painless-software-schedules/).

### Epics?
It's OK for some user stories not to have an epic parent. It simply means that the work they represent doesn't take months to complete.

### Features?

Reasons to be cautious using features:
- you don't need an intermediate work item size that's between weeks and months
- the name "feature" is overloaded and is suggestive of the *product* hierarchy, rather than the *time* hierarchy
- it's not necessarily obvious that an epic is larger than a feature

## The proper meaning of work item types

Work items must be time-bound: they must have a definite endpoint at which they can be closed. If a work item, however large, is not time-bound, it is wrongly defined. In particular, work item types are not supposed to represent product and feature hierarchy.

### Example: the wrong way
> We have an epic called *Priority Boost*, which is years old and is still in the `Active` state.
>
> Every time we have priority boost-related work, we make the *Priority Boost* epic the parent of the new user stories and tasks.

Some of the problems that come from using work item types this way:
- such work items can never be closed, as there may always be new work in that area
- over time, closed work item children will accumulate, making the list of linked items hard to use, both for seeing what's left to do and for seeing what's been accomplished recently

### Example: the right way
> During semester planning, we estimate that it will take half a semester to add the priority boost feature to the rewrite of our service.
>
> To track this work, we create an epic called *Priority Boost in v2*.
>
> During further planning, we break it down into user stories that represent smaller work items that should take a few weeks to implement.
>
> During sprint planning, we break down individual user stories into tasks that should take a few hours or days to implement and that could now be assigned to individual team members.

Using work item types this way, we are able to close even the largest ones once the work is finished.

Notice also that creating time-bound work items forces us to write titles that are more concrete and specific. Remember, when writing, if you want to be clear and intelligible, you should prefer *concrete and specific* to *general and abstract*.

## Area Paths

If you shouldn't use work item types to group related work, then what should you use?

Area paths.

This distinction, as obvious as it seems to me, appears to be a genuine Microsoft innovation. Its origin is *at least* as old as the early 2000s, when area paths were already an established feature of Microsoft's internal work item tracking application, Product Studio. After efforts were under way to deprecate Product Studio internally and simultaneously replace Visual Source Safe as a source control product (circa 2005-2006), area paths became a feature of the Team Foundation Server/TFS product. Eventually, TFS got rebranded, first as Visual Studio Online and then as Azure DevOps.

And area paths, thanks to Product Studio and possibly something that existed before it, are here to be used by you and me.

Since you now know that you should be using area paths instead of work item hierarchy to group items, here's how to add a new area paths:
- [Define area paths and assign to a team](https://learn.microsoft.com/en-us/azure/devops/organizations/settings/set-area-paths?view=azure-devops&tabs=browser)
