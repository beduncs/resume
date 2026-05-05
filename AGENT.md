# Resume Management Workflow

This project uses a "Resume Library" approach to manage multiple targeted resumes from a single source of truth.

## Project Structure
- `library.json`: The comprehensive "Source of Truth" containing all work history, highlights, skills, and certifications. **Never deploy this directly.**
- `resume.json`: The targeted sub-resume generated for a specific role or focus. **This is the file deployed to the Gist.**

## Workflow

### 1. Update the Library
Always add new experiences, projects, or skills to `library.json` first. This ensures your master history is always up to date.

### 2. Generate Targeted Resume
To generate or update the targeted resume (`resume.json`), provide the AI agent with specific focus areas. 
*Example:* "Generate a resume focused on AI/ML Engineering roles. Include LLM and Kubernetes highlights, but omit Systems Engineering testing details."

**The Agent Process:**
1.  Read `library.json`.
2.  Subselect and refine content based on the user's target.
3.  Write the validated result to `resume.json`.

### 3. Deployment
The CI/CD workflow in `.github/workflows/gist.yml` is configured to deploy `resume.json` to your Gist automatically upon a push to the `master` branch.

## Rules & Constraints
- **Strict Factual Accuracy:** Do not hallucinate, invent, or embellish details. Every claim, highlight, and summary must be derived strictly from the content in `library.json`.
- **Do not edit `resume.json` directly** for persistent changes; they will be overwritten during the next generation.
- **Schema Compliance:** All files must remain compliant with the [JSON Resume Schema](https://jsonresume.org/schema/).
- **Sanitization:** Ensure personal contact info (Email/Phone) is cleared in both files before committing to public repositories.
