# ci-shared
Shared GitHub Actions workflow for all site projects. Public on purpose (contains no secrets). Change the pipeline here once, every project picks it up on its next deploy.

## Inputs
- `directory` (default `web`): the folder that is checked before the deploy.
- `build_command` (default none): runs before the deploy.
- `node_version` (default none): Node version for the build; without it the build uses the runner's Node.
- `require_index` (default `true`): fails if the folder has no `index.html`. Set `false` for server-rendered apps, where the Worker answers `/`.

## Notice for all projects: change of 2026-11-03 (aa8dcb5)
`node_version` and `require_index` were added for Night Vision. The defaults should leave every other project as it was, but this has not been run on them.

Projects using this workflow at that time: job-hunter, events-naturfreunde, dj-victor, theaterguide, tiboverse-hub, night-vision.

**When you next work on one of these projects:** check its next deploy (`gh run list --workflow deploy.yml --limit 1`, then open the site). If it fails because of this change, tell Victor, who decides on the rollback. Rollback, here in ci-shared: `git revert aa8dcb5` and push (Night Vision needs its own fix first, since it depends on these inputs). Then note the result here.

| Project | Deploy checked after the change |
|---|---|
| job-hunter | not yet |
| events-naturfreunde | not yet |
| dj-victor | not yet |
| theaterguide | not yet |
| tiboverse-hub | not yet |
