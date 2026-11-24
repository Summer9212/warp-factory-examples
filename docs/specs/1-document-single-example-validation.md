# Document single-example validation (#1)

## Summary

Document the SDLC-only validation command in the root README. State that exit
code 2 means validation did not run and is not a pass.

## Behavior

1. The root `README.md` documents this command exactly:

   ```bash
   python3 scripts/validate_factory_files.py examples/*sdlc-issue-to-pr
   ```

2. The documentation states that exit code 2 means the validator did not run.
   It must not describe exit code 2 as a successful validation result.
3. The implementation proposes this short plan in the pull request and waits
   for explicit approval of this specification revision before editing
   `README.md`.

## Implementation notes

- Change only the root `README.md` after approval.
- Add the guidance beside the existing `## Validate an example` section.
- Preserve the command's glob exactly as requested.
- Report the actual outcomes of the convention check and the targeted validator
  command. Treat validator exit code 2 as not validated, not as a pass.
- Report the final pull request scope check in the pull request description.

## Acceptance criteria

1. Run `python3 scripts/check_conventions.py`; report its actual exit code and
   result in the pull request.
2. Run `python3 scripts/validate_factory_files.py examples/*sdlc-issue-to-pr`;
   report its actual exit code and result in the pull request.
3. Review `README.md` manually to confirm it contains the exact command and
   the exit-code-2 warning.
4. Run `git diff --name-only blueprint-demo...HEAD`; the final pull request
   diff lists exactly `README.md` and
   `docs/specs/1-document-single-example-validation.md`. Report that command
   and its observed result in the pull request description.

## Out of scope

- Changes to example files, validation scripts, or other documentation.
- Running validation for every example.
- Merging the draft pull request.
