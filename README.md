# Benjamin Hayden Duncan's Resume

This repository manages my master resume library and generates targeted sub-resumes for deployment.

## Registry
My current targeted resume is hosted at:
https://registry.jsonresume.org/beduncs

## Resume Library Workflow
This project uses a "Resume Library" approach:
- `library.json`: The source of truth containing all work history and highlights.
- `resume.json`: The targeted sub-resume generated for specific roles.

### How to update
1.  Add new experiences to `library.json`.
2.  Use the Gemini CLI agent to subselect highlights into `resume.json`.
3.  Push to the `master` branch. The GitHub Action in `.github/workflows/gist.yml` will automatically update the Gist linked to the registry.

## Setup for Automatic Gist Updates
1. Create a Gist called `resume.json`.
2. Create a Personal GitHub token with the `gist` scope.
3. Add the token to repository secrets as `TOKEN`.
4. Ensure the `gist_id` in `.github/workflows/gist.yml` matches your Gist ID.
