# Building a Windows `.exe`

## Why you do not see an `.exe` in this repo right now

This repository only stores source code. The `.exe` is generated **after** running the build step.

## Option A (recommended): Build on GitHub Actions (no local setup)

A workflow was added at `.github/workflows/build-windows-exe.yml`.

1. Push this branch to GitHub.
2. Open the **Actions** tab.
3. Run **Build Windows EXE**.
4. Download the artifact named `GeometryDashV1-windows-exe`.

That artifact contains the generated `.exe` file(s).

## Option B: Build on your own Windows machine

### 1) Install dependencies

```bash
npm install
```

### 2) Build `.exe`

```bash
npm run dist:win
```

Output will be created in `dist/`, including:
- `GeometryDashV1-portable-1.0.0.exe` (single portable `.exe`)
- `GeometryDashV1-setup-1.0.0.exe` (installer)

## Troubleshooting

- If `npm install` fails with registry/network policy errors, the build cannot run in that environment.
- If you need just one file to copy machine-to-machine, use the `portable` `.exe` output.
- If GitHub Actions reports a lockfile/cache error, this workflow intentionally uses `npm install` (not `npm ci`) and does not require a committed `package-lock.json`.
