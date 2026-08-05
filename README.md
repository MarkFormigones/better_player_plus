# Better Player Plus Fork

This repository is a **fork** of the original `better_player_plus` project.

It contains custom modifications required by our application while keeping a clean copy of the upstream repository. This branch strategy makes it easier to receive future updates from the original project while maintaining our own changes.

## Branch Strategy

This repository contains three long-lived branches:

| Branch | Purpose |
|--------|---------|
| `master` | Clean mirror of the upstream repository. |
| `develop` | Development branch containing all custom changes. |
| `release` | Stable production branch used for creating release tags. |

---

## master

The `master` branch is a **clean copy of the upstream repository**.

### Purpose

- Keep an unmodified copy of the upstream project.
- Synchronize the latest updates from the repository owner.
- Serve as the base for merging upstream changes into `develop`.

### Do

- Sync with the upstream repository.
- Keep this branch identical to the upstream `master`.

### Don't

- Add custom features.
- Fix application-specific bugs.
- Create release tags.

---

## develop

The `develop` branch is the **main development branch**.

It contains all custom modifications made for our application.

### Purpose

- Starting point for all development work.
- Implement new features and bug fixes.
- Merge updates from `master` after syncing with upstream.

### Do

- Create feature branches from `develop`.
- Merge completed work back into `develop`.
- Test all changes before preparing a release.

### Don't

- Create production release tags.

---

## release

The `release` branch contains the **production-ready code**.

This branch should always represent the latest stable version.

### Purpose

- Prepare production releases.
- Create Git tags.
- Publish GitHub Releases.

### Do

- Merge tested changes from `develop`.
- Create version tags and use the following format:
  ```
  v<upstream-version>+hotfix.<number>
  ```
  #### Examples
  ```
  v1.1.5+hotfix.1
  v1.1.5+hotfix.2
  v1.1.5+hotfix.3
  v1.1.6+hotfix.1
  ```
- Increment the `hotfix` number for each new release.
- Reset the `hotfix` number to `1` when upgrading to a new upstream version.

### Don't

- Perform active development directly on this branch.

---

## Development Workflow

```text
                 Upstream Repository
                        │
                        ▼
                    master
                        │
                Sync / Merge Updates
                        │
                        ▼
                    develop
                        │
             Feature Development
               Bug Fixes & Testing
                        │
                        ▼
                    release
                        │
                 Create Git Tag
                        │
                        ▼
                 GitHub Release
```

## Typical Workflow

1. Sync `master` with the upstream repository.
2. Merge the latest `master` into `develop`.
3. Implement and test changes in `develop`.
4. Merge tested changes into `release`.
5. Create a Git tag from `release`.
6. Publish a GitHub Release.

---

## Notes

- Never commit custom changes directly to `master`.
- Always start development from `develop`.
- Always create release tags from `release`.
- Keeping `master` synchronized with the upstream repository makes future updates much easier.
