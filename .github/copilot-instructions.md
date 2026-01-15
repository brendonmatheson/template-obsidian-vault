# General Rules

- Always confirm with the user before making any changes to the code or documentation.

# Documentation

## Overview

There are two types of documentation:
- Module documentation which represents the current state of the module
- Tickets which represent a change that is proposed to be made

## Module Documentation

Module documentation is represented by a single Markdown file called README.md located in the root directory.

Module documentation should strictly represent the current state of the module and should never include any discussion of future enhancements because these should all be captured by tickets.  Sections such as the following should never be part of a module document:
- Current Implementation Status
- Completed Features
- In Development
- Future Development

## Tickets

Tickets are stored in the tickets directory at the root of the main repository `./tickets/`

Tickets are created from the template file
./_templates/Ticket.md and contain the following YAML front matter:

```yaml
template: "[[Ticket]]"
kind: ticket
tags:
  - ticket
code: 
aliases:
name: 
ticket_status: 
```

Explantion of the YAML keys:
- `template`: Always set to "[[Ticket]]" to indicate the type of the file.
- `kind`: Always set to "ticket" to indicate the type of the file.
- `tags`: Always contains the tag "ticket" to indicate the type of the file.
- `code`: A unique code for the ticket which is also used at the beginning of the filename.
- `aliases`: Obsidian aliases for the ticket, typically the same as the `code`.
- `name`: A human-readable name for the ticket.
- `ticket_status`: The status of the ticket.

Valid values for `ticket_status` are:
- `[[Backlog]]`: The ticket is in the backlog and not yet started.
- `[[Ready]]`: The ticket is ready to be worked on.
- `[[In Progress]]`: The ticket is currently being worked on.
- `[[Done]]`: The ticket has been completed.

# Ticket Execution

You should only work on tickets that are in the `[[Ready]]` or `[[In Progress]]` status.  If the user asks you to work on a ticket that is in the `[[Backlog]]` status, you should ask them to change the status to `[[Ready]]` first.

When creating a new ticket, use the template file and fill in the required fields.  The `code` field should be unique and follow the format `T001`, `T002`, etc.  The `name` field should be a descriptive name for the ticket.  The `ticket_status` should be set to `[[Backlog]]` by default.

When picking up a new ticket, the first thing to do is to plan out the execution as a linear series of tasks.  This should be done in the `# Execution Plan` section of the ticket.  The execution plan should be a list of tasks that need to be completed to finish the ticket.  Each task should be a single line and should be written in the imperative mood, e.g. "Implement the API endpoint", "Write unit tests", etc.  Tasks should use the Markdown task list format, e.g. `- [ ] Task description`.

After writing the Execution Plan, always stop and ask the user if they want to proceed with the plan.  If they agree, you can start executing the tasks one by one.  If they ask for changes to the plan, update the plan accordingly and ask for confirmation again.

When executing in agent mode, do tasks one by one.

The first thing to do when starting on a task is to confirm that the spec is complete and correct.  Work with the user to update the spec documented in the ticket before proceeding to make changes.

After each tasks is completed, mark the task as done in the `# Execution Plan` section by changing the `- [ ]` to `- [x]`.  If you need to ask the user a question, do so before marking the task as done.  If you need to wait for a response from the user, pause the execution until you receive a response.

After each tasks is completed, also update the documentation file for the affected services.  Refer to the table above for the services and their documentation files.  The documentation file should be updated with the changes made in the ticket.  If the ticket affects multiple services, update all relevant documentation files.

# IDE Configuration

## Visual Studio Code

The settings for Visual Studio Code are stored in the `.vscode` directory at the root of the main repository.
