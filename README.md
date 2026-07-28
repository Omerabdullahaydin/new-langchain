# LangGraph.js Starter App

A lightweight LangGraph.js starter project showing how to build a simple state-based conversational agent.

This repo includes:
- `src/agent/graph.ts`: the main graph implementation and routing logic
- `src/agent/state.ts`: shared state definitions used by the graph
- `langgraph.json`: LangGraph configuration for the local graph runtime
- `.env.example`: environment variable examples
- tests for graph behavior and integration flows

## What this project does

The app demonstrates a state graph that:
- receives user input
- preserves conversation state
- routes execution through a single model node
- returns a response and updates the message history

It is intentionally minimal so you can extend it with your own LLM calls, tools, and graph logic.

## Setup

1. Navigate to the app folder:

```bash
cd path/to/your/app
```

2. Install dependencies:

```bash
yarn install
```

3. Create a local environment file:

```bash
cp .env.example .env
```

4. Add your API key if you want to enable provider integrations:

```bash
LANGSMITH_API_KEY=YOUR_LANGSMITH_API_KEY_HERE
```

> The project runs with placeholder state logic by default, so an API key is not required unless you add an LLM integration.

## Scripts

Available commands:

- `yarn build` - compile TypeScript to `dist`
- `yarn test` - run unit tests
- `yarn test:int` - run integration tests
- `yarn lint` - lint `src`
- `yarn format` - format files with Prettier
- `yarn lint:langgraph-json` - validate LangGraph paths
- `yarn lint:all` - run lint and format checks
- `yarn test:all` - run all tests and linting

## Project structure

- `src/agent/graph.ts` - graph builder and routing logic
- `src/agent/state.ts` - graph state annotation definitions
- `tests/agent.test.ts` - unit tests for agent behavior
- `tests/graph.int.test.ts` - integration tests for graph execution
- `langgraph.json` - local graph runtime config

## Customize the graph

To extend the starter app:

1. Update `callModel` in `src/agent/graph.ts` to call a real LLM or external API.
2. Add new nodes and edges to the `StateGraph` builder.
3. Change `route()` to add conditional graph branching.

Example provider ideas:
- `@langchain/anthropic`
- `openai`
- `@langchain/openai`

## Environment variables

Use `.env` to store secrets and local settings. Example values:

```env
LANGSMITH_API_KEY=YOUR_LANGSMITH_API_KEY_HERE
ANTHROPIC_API_KEY=<your-anthropic-api-key>
```

Keep `.env` out of source control. The repo already ignores `.env` via `.gitignore`.

## Development tips

- Modify the graph and rerun your local server to test changes.
- Use state annotations in `src/agent/state.ts` to enforce types across nodes.
- Add new unit tests when you add logic or branching paths.

## Notes

This repository is a starter template and does not include production deployment configuration. It is designed for experimentation and rapid prototyping with LangGraph.js.

