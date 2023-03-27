---
description: Overview of roles in Ango Hub
---

# User Roles

All users in Ango Hub belong to both organizations and projects. As such, all users have different roles both at the organization and the project level.&#x20;

This page is an overview of all roles available to users, both at the organization and at the project level.

{% hint style="info" %}
For more on inviting new users to your organization, and on organization-level roles in detail, check the [Organizations](organizations.md#inviting-new-users-to-your-organization-admin-only) page.

For more on inviting users to projects, and on project-level roles in detail, check the [Managing Users in Projects](../labeling/managing-users-in-projects/) page.
{% endhint %}

## User Roles in Ango Hub

| Level        | Role     | Properties                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| ------------ | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Organization | Admin    | <ul><li>Can see and edit all data in all projects in organization (equivalent to having the <em>Manager</em> role in all projects)</li><li>Can invite and remove org members</li><li>Can edit other members' org- and project-level role</li><li>Can see org-level statistics</li><li>Can see Ango Hub usage/plan details</li><li>Can install and remove plugins</li></ul>                                                                                                                                                                                          |
| Organization | Member   | <ul><li>Cannot see/edit organization-level data (statistics, plugins, usage, etc.)</li><li>Can only see assigned projects</li><li>In projects, can only see data according to assigned project-level role</li></ul>                                                                                                                                                                                                                                                                                                                                                 |
| Project      | Labeler  | <ul><li><p>Available actions:</p><ul><li><a href="labeling-core-concept.md">Labeling</a></li><li>Opening, responding to, solving, deleting own <a href="issues.md">issues</a></li></ul></li><li><p>Available data</p><ul><li><a href="assets.md">Assets</a> he has labeled</li><li><a href="tasks.md">Tasks</a> he has completed</li><li>Project <a href="instructions.md">instructions</a> and <a href="samples.md">samples</a></li><li>Personal statistics</li><li><a href="issues.md">Issues</a> in which he's been mentioned or he's opened</li></ul></li></ul> |
| Project      | Reviewer | <p>Everything a <em>Labeler</em> can do/see, plus:</p><ul><li><p>Available actions:</p><ul><li><a href="reviewing.md">Reviewing</a></li><li>Adding, requeuing, reassigning, deleting labeling tasks</li><li>Set samples</li><li>Opening, responding to, solving, deleting any issue</li><li>Set <a href="benchmarks.md">benchmark</a> tasks</li></ul></li><li><p>Available data</p><ul><li>All data except for exporting and project settings</li></ul></li></ul>                                                                                                   |
| Project      | Manager  | <p>Everything a <em>Reviewer</em> can do/see, plus:</p><ul><li><p>Available actions:</p><ul><li><a href="../data/importing-and-exporting-annotations/exporting-annotations.md">Exporting</a> labels</li><li>Editing project settings</li></ul></li></ul>                                                                                                                                                                                                                                                                                                            |
