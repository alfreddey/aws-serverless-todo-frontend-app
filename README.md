# Serverless To-Do App — Frontend (Java backend)

React + Vite + aws-amplify single-page app for the serverless to-do app. It talks
to the Java backend (Cognito auth + REST API) purely over HTTP, using the
`VITE_*` values below — there is no code-level link to the backend.

The backend lives in a separate repo (`aws-serverless-todo-app-java`).

## Configure

Copy the example env file and fill in the values from the backend stack outputs
(`UserPoolId`, `UserPoolClientId`, `ApiUrl`):

```bash
cp .env.example .env.local
```

| Variable                   | Comes from (backend stack output) |
| -------------------------- | --------------------------------- |
| `VITE_AWS_REGION`          | your AWS region                   |
| `VITE_USER_POOL_ID`        | `UserPoolId`                      |
| `VITE_USER_POOL_CLIENT_ID` | `UserPoolClientId`                |
| `VITE_API_URL`             | `ApiUrl`                          |

## Run locally

```bash
npm install
npm run dev
```

## Deploy (AWS Amplify Hosting)

The backend's SAM template provisions Amplify Hosting for this repo. Push this
repo to GitHub, then deploy the backend with `GitHubRepositoryUrl` pointing at
this repo (see the backend README). Amplify builds from the repo root and injects
the `VITE_*` variables automatically.
