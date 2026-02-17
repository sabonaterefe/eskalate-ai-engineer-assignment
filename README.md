## AI Experts Assignment (Python)
This repository contains my completed solution for the AI Experts Assignment.
The project demonstrates how to set up a reproducible Python environment, identify and fix a bug with minimal changes, and document the process clearly.
---



## Project Overview
Environment setup: Runs reliably both locally and inside Docker.

Dependencies: All packages are pinned in requirements.txt for reproducibility.

Testing: Focused tests were written to expose the bug and confirm the fix.

Bug fix: Applied the smallest possible change to make all tests pass.

Documentation: README updated with usage instructions, and EXPLANATION.md describes the bug and solution.


## Running the Tests
# Run locally
Install dependencies:
pip install -r requirements.txt
Run the test suite:
python -m pytest -v


# Run in Docker
Build the image:
docker build -t ai-experts-assignment .
Run the tests inside the container:
docker run --rm ai-experts-assignment


## Bug Fix Summary
Issue: The client failed to attach the Authorization header when the OAuth2 token was stored as a dictionary.

Fix: Added a condition to refresh when the token is a dict, converting it into a proper OAuth2Token.

Result: All 5 tests now pass, both locally and in Docker.

Details are documented in EXPLANATION.md.


## Repository Structure
<pre>
app/                # Application code (http_client, tokens)
tests/              # Pytest test suite
Dockerfile          # Container setup
requirements.txt    # Pinned dependencies
README.md           # Project instructions
EXPLANATION.md      # Bug explanation and fix
</pre>
## Submission
This repository is public and ready for review.
All requirements have been met: Dockerfile, requirements.txt, README updates, bug fix with tests, and EXPLANATION.md.
