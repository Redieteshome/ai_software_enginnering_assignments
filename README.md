# AI Software Engineer Assignment (JS/TS)

This repository contains the solution for the AI JS/TS Code Review Assignment at Eskalate.

It demonstrates:

- Running a small JavaScript/TypeScript project reliably (locally + in Docker).

- Pinning dependencies for reproducible installs.

- Writing focused tests that reproduce a bug.

- Implementing a minimal, reviewable fix.

## Prerequisites

- Node.js and npm installed locally.

- Git installed.

- Docker installed (for CI-style environment).

## Running the tests locally
  
### Clone this repository:

`git clone https://github.com/Redieteshome/ai_software_enginnering_assignments.git `

`cd ai-software-engineer-assignment-ts`



1. Install dependencies:
   - `npm install`
2. Run the test suite:
   - `npm test`

All tests should pass, including the edge case for plain object tokens.

### Running Tests with Docker

Note: Docker Desktop required for local Docker builds.

- Build the Docker image:

`docker build -t eskalate-assignment .`


- Run the tests inside the container:

`docker run --rm eskalate-assignment`


The tests run automatically via the CMD `["npm", "test"]` instruction.

## Pinning Dependencies

- All dependencies in `package.json` are pinned to exact versions.

- No lockfiles `(package-lock.json, yarn.lock)` are committed to ensure reproducible installs in Docker.

## Bug Fix

- The original HttpClient class did not refresh tokens that were plain objects.

- The fix ensures the token is refreshed whenever it’s not an OAuth2Token instance or if it has expired.

- Tests reproduce the bug and validate the fix.

## Notes

 - Changes are minimal and reviewable.

- No unrelated refactors were applied.

- Tests cover the main bug and key edge cases.

- See `EXPLANATION.md` for a concise reasoning of the bug and fix.
