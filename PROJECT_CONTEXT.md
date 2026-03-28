# Project Context — cowork-backlink-intelligence

## Purpose
Backlink Intelligence Cowork Plugin for Claude Cowork. Packages domain-specific skills, commands, and an autonomous agent into a single installable plugin.

## Architecture
- **Skills (4):** link-discovery, competitor-gap, expired-domains, link-verify
- **Commands (4):** /links:discover, /links:gap, /links:expired, /links:verify
- **Agent:** link-campaign

## Design Decisions
- Skills contain the domain knowledge and step-by-step instructions
- Commands are lightweight entry points that invoke the right skill
- The agent chains multiple skills into an autonomous workflow
- MCP connectors declared in .mcp.json (user configures credentials)

## Installation
Cowork → Customize → Browse Plugins → Upload → select ZIP.

## Author
Artur Ferreira / The GEO Lab (thegeolab.net)
