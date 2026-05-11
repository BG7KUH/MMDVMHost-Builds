# MMDVMHost-Builds

This repository builds the upstream MMDVMHost project for multiple platforms using GitHub Actions and publishes the build artifacts as release assets when you push a version tag.

## Build targets

- Linux x86_64 (gcc)
- Linux x86_64 (clang)
- Linux arm64 (gcc, via QEMU container)
- Windows x86 (MSVC, static)
- Windows x64 (MSVC, static)

## How it works

The workflow clones the upstream repo at build time and produces binaries. Windows builds use static vcpkg triplets so the resulting exe does not require runtime DLLs.

## Create a release

Push a tag that starts with "v" (for example, v0.1.0). The workflow will build all targets and upload the artifacts to a GitHub Release under that tag.

Example:

```powershell
git tag v0.1.0
git push origin v0.1.0
```

## Notes

- The upstream source is not stored in this repo; it is cloned during CI.
- The Windows exe still expects a valid config file at runtime. Run it with an ini file like:
	`MMDVMHost.exe MMDVMHost.ini`
