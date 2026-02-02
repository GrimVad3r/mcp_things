
# Tenx MCP Analysis: VS Code Deployment Guide

## Overview

The **Tenx MCP Analysis server** is a tool designed to gather real-time data on developer interactions with AI Coding Agents. It utilizes a non-invasive background framework where the LLM acts as an evaluator to provide feedback and measure competencies like clarity and context without interrupting your workflow.

## Prerequisites

* 
**VS Code:** Must be updated to the latest version.


* 
**Extensions:** Both **GitHub Copilot** and **GitHub Copilot Chat** must be installed from the marketplace.



## Deployment Steps

### 1. Project Configuration

Within your working directory, establish the necessary structure for agent instructions and MCP configurations:

* 
**Agent Rules:** Create a folder named `.github/` and a file inside called `copilot-instructions.md`.


* 
**MCP Config File:** Create a folder named `.vscode/` and a file inside called `mcp.json`.



### 2. MCP Server Setup

Follow these steps to connect to the Tenx proxy:

1. Open the VS Code interface and locate the **"Add Server..."** button at the bottom.


2. Choose the server type as **HTTP**.


3. Enter the URL: `https://mcppulse.10academy.org/proxy`.


4. Set the name to: `tenxfeedbackanalytics`.



### 3. Header Configuration

Edit your `.vscode/mcp.json` file to include the required headers. Replace `<your device type>` with `mac`, `linux`, or `windows` as appropriate.

```json
{
  "servers": {
    "tenxfeedbackanalytics": {
      "url": "https://mcppulse.10academy.org/proxy",
      "type": "http",
      "headers": {
        "X-Device": "<your device type>",
        "X-Coding-Tool": "vscode"
      }
    }
  },
  "inputs": []
}

```



### 4. Authentication & Activation

* Click the **"Start"** button on the MCP server entry in VS Code.


* You will be redirected to your browser to authenticate via **GitHub**.


* After authorizing, you will be redirected back to VS Code to confirm successful authentication.



## Verifying the Connection

To ensure the agent has access to the MCP tools:

1. Open **Copilot Chat**.
2. Switch to **"Agent"** mode.


3. Click the **tools icon** to view the available MCP tools (e.g., `tenxanalysismcp`).



## Interaction Flow

Once active, the process is seamless:

1. 
**User Initiates:** You pose a query to the agent.


2. 
**Agent Action:** The agent performs the task and simultaneously calls the MCP tool in the background.


3. 
**Analysis:** The Tenx server logs high-fidelity data on the interaction, including intent, turn counts, and competency scores.