# USE-611 distribution verification

- [x] Confirm the approved distribution PR is merged: https://github.com/Snippet-Core/snippet-cursor-plugin/pull/1 (merged 2026-11-09).
- [x] Verify public repository: https://github.com/Snippet-Core/snippet-cursor-plugin.
- [x] Record canonical package revision: `3f394ceefd3cd1f7dce35e28d2e721d0b46dd4f6`.
- [x] Verify that revision is an ancestor of main and is anonymously accessible (HTTP 200).
- [x] Parse both package JSON files, confirm MIT license and measure both distribution PNGs at 400×400.
- [x] Adversarial review: distinguish approved source head `ac07956df1dc666a35f5fc46acf89350e19cd4ff` from the actual merged revision above. No new merge or package changes needed. Prior review approved all seven checks; live OAuth compatibility is not asserted.

USE-656 and USE-621 can proceed using the canonical public package revision above. Hermes-specific files added later require their own later revision.

Rollback: revert PR #1 through the normal PR process; its parent revision is `f0590c8f8bf50de2506ccb824462cdbb3df47f21`.

## Batch cos-2026-11-11

- [x] Merge USE-611 verification commit `33f1334b632c5ddf879d833e457065f82dcc41d1` into the batch based on current main.
- [x] Recheck PR #1 merged SHA, public repository visibility, revision ancestry and anonymous HTTP 200.
- [x] Parse all four JSON manifests; verify MIT license and both distribution PNG dimensions (400×400).
- [x] Review the combined documentation-only diff and run `git diff --check`.
- Test suite, lint, typecheck and build: unavailable; this static plugin repository has no corresponding tooling or CI workflows.
- Deployment: no deployment or release workflow exists in this repository; distribution is the public Git repository.
- Batch rollback: revert the batch PR merge through a new PR; pre-batch main is `f23aa7a`.

Reproduce the package verification from this checkout:

```sh
gh pr view 1 --json state,mergeCommit,headRefOid
gh repo view --json isPrivate
git merge-base --is-ancestor 3f394ceefd3cd1f7dce35e28d2e721d0b46dd4f6 origin/main
curl --fail --silent --output /dev/null --write-out '%{http_code}\n' https://github.com/Snippet-Core/snippet-cursor-plugin/tree/3f394ceefd3cd1f7dce35e28d2e721d0b46dd4f6
python3 - <<'PY'
import json, pathlib, struct
for p in pathlib.Path('.').rglob('*.json'):
    json.loads(p.read_text())
assert 'MIT License' in pathlib.Path('LICENSE').read_text()
for name in ['assets/icon-400.png', 'assets/logo-padded.png']:
    data = pathlib.Path(name).read_bytes()
    assert data[:8] == b'\x89PNG\r\n\x1a\n'
    assert struct.unpack('>II', data[16:24]) == (400, 400)
print('PASS: manifests, license, PNG dimensions')
PY
git diff --check origin/main...HEAD
```
