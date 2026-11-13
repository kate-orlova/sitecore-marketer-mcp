# Prompt and Skill library for Sitecore Marketer MCP
A collection of practical prompts, skills, examples and use cases for working with SitecoreAI through the Sitecore Marketer MCP server.

## Overview

This repository contains a growing collection of prompts and skills designed to demonstrate how the Sitecore Marketer MCP server can be used to interact with SitecoreAI and automate marketing-related activities.

The goal is to explore practical applications of Model Context Protocol (MCP) in the SitecoreAI ecosystem providing reusable prompts and skills that help marketers, content authors and developers perform common tasks using natural language and AI assistants.

Rather than relying on manual navigation through multiple SitecoreAI interfaces, these prompts and skills demonstrate how users can leverage AI assistants, such as Claude, to discover content, manage components and configure marketing experiments.

The library is a work in progress. New prompts, skills scenarios and examples will be added as additional Sitecore Marketer MCP capabilities and use cases are explored.

## Getting Started

### Prerequisites

To use the prompts and skills in this repository you will need:

- Access to a SitecoreAI environment
- A configured Sitecore Marketer MCP server connection
- An MCP-compatible AI assistant, such as Claude
- Appropriate SitecoreAI permissions to perform the requested operations

### How to Use the Prompts

1. Browse the prompt categories in the [prompts](/prompts) directory
1. Open the relevant .md file
1. Copy the example prompt from the Prompt section
1. Replace the example page, component or other parameters with the values relevant to your SitecoreAI environment
1. Submit the prompt to your connected AI assistant
1. Follow any additional instructions or permission requests from the assistant
1. Review and confirm operations that modify your SitecoreAI environment

Some operations require explicit confirmation before the MCP server executes them.

**Important:** Always review the proposed changes before confirming operations that create or modify SitecoreAI content, components or experiments.

## Prompt Library

The prompts are organised into functional categories to make it easier to discover relevant use cases:

1. [Component Management](/prompts/component%20management/) for discovering and working with components used across SitecoreAI pages.
2. [Experiments](/prompts/experiments/) for creating and managing marketing experiments through SitecoreAI.
3. [Page Management](/prompts/page%20management/) for retrieving and managing SitecoreAI pages.

## Skill Library
The skills are also structured into functional categories to make them easier to navigate and use:
1. [Safe Content Changes](/skills/sitecoreai-safe-content-changes/SKILL.md) provides a safety-first workflow for making changes to existing content in SitecoreAI through the Sitecore Marketer MCP server. It covers actions such as deleting or updating content items, removing or moving components, and replacing datasources, requiring the current state and potential impact to be reviewed before any change is made. The skill enforces explicit user confirmation for each mutation, keeps changes strictly within the requested scope, avoids automatic retries, and does not publish changes by default—ensuring that users understand what will change, what content or experiments may be affected, and whether the action can be reversed before it is applied.

## Disclaimer
This repository is a community-oriented collection of prompts and examples maintained by Kate Orlova.

The examples are provided for learning and experimentation. Actual behaviour may vary depending on the SitecoreAI environment, available MCP tools, user permissions and AI assistant capabilities.

Always review and validate operations before applying changes to production environments!


**Explore, experiment and discover what is possible with [SitecoreAI](https://doc.sitecore.com/sai/en/users/sitecoreai/sitecoreai.html) and [Sitecore Marketer MCP](https://doc.sitecore.com/sai/en/users/sitecoreai/sitecore-marketer-mcp-server.html)!**

