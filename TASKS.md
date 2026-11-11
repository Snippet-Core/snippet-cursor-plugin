# USE-611 distribution verification

- [x] Confirm the approved distribution PR is merged: https://github.com/Snippet-Core/snippet-cursor-plugin/pull/1 (merged 2026-11-09).
- [x] Verify public repository: https://github.com/Snippet-Core/snippet-cursor-plugin.
- [x] Record canonical package revision: `3f394ceefd3cd1f7dce35e28d2e721d0b46dd4f6`.
- [x] Verify that revision is an ancestor of main and is anonymously accessible (HTTP 200).
- [x] Parse both package JSON files, confirm MIT license and measure both distribution PNGs at 400×400.
- [x] Adversarial review: distinguish approved source head `ac07956df1dc666a35f5fc46acf89350e19cd4ff` from the actual merged revision above. No new merge or package changes needed. Prior review approved all seven checks; live OAuth compatibility is not asserted.

USE-656 and USE-621 can proceed using the canonical public package revision above. Hermes-specific files added later require their own later revision.

Rollback: revert PR #1 through the normal PR process; its parent revision is `f0590c8f8bf50de2506ccb824462cdbb3df47f21`.
