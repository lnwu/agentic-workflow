# Agentic Workflow for Coding Agents

Agentic Workflow is a complete software development workflow for your coding agents, built on a set of composable "skills" and initial instructions that ensure your agent uses them.

## Credit

- Based on [Superpowers](https://github.com/obra/superpowers), with some customizations to fit my needs.

## How It Works

It kicks in the moment you fire up your coding agent. Instead of jumping straight into writing code, it steps back and asks what you're really trying to build.

Once it's extracted a plan and tasks from the conversation, it presents them in chunks short enough to actually read and digest.

After you've signed off on the plan, your agent follows the tasks using a red/green TDD workflow to build out the codebase. It also delegates to a "code reviewer" agent to check its work. If the reviewer finds issues, the code gets sent back for fixes.

From there, once you say "go", it launches the implementation process — agents work through each engineering task, inspecting and reviewing their output, and moving forward.

There's more to it than that, but this is the core of the system. And because the skills trigger automatically, you don't need to do anything special. Your coding agent just has Agentic Workflow.
