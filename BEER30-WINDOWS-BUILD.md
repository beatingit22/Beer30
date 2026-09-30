# Beer30 fork: Windows developer build

This checkout is **not yet a branded or tested Beer30 launcher**. It is a Prism Launcher source fork used to test direct Minecraft launch, Fabric instances and Microsoft sign-in before rebranding. It must not be redistributed as a Beer30 binary in its current form: Prism icons, links, identity and update settings remain.

## Prerequisites

Use a Windows 10/11 x64 machine with Visual Studio 2022 C++ desktop build tools, CMake 3.28+, Ninja, Git and the dependencies described in [Prism's build instructions](https://prismlauncher.org/wiki/development/build-instructions). The upstream CI workflow at `.github/workflows/build.yml` uses the `windows_msvc` CMake preset and installs its dependencies through `.github/actions/setup-dependencies`; it also relies on the `cmake/vcpkg` and `libraries/libnbtplusplus` Git submodules. A shallow ZIP download is insufficient.

From a Visual Studio developer PowerShell in this source checkout:

```powershell
git submodule update --init --recursive
$env:BUILD_PLATFORM = 'beer30-dev'
$env:ARTIFACT_NAME = 'Beer30-Windows-Dev'
cmake --preset windows_msvc
cmake --build --preset windows_msvc --config Release
ctest --preset windows_msvc --build-config Release --output-on-failure
```

If configure fails, follow the upstream setup-dependencies instructions for Qt 6.8+, ECM, cmark and vcpkg before retrying. Do not disable test failures. The resulting build is a **developer test**; run it only after reviewing the source and without overwriting an existing Prism installation.

## Sign-in and distribution gates

The existing upstream Microsoft identity client ID is still in this source. Prism's README says forks/custom builds may retain included keys only subject to the listed platform terms; this is not a promise that a rebranded Beer30 build will be accepted or supported. Do not collect passwords or copy account tokens. Test login with an account that owns Minecraft Java on Windows, then create a clean Fabric instance and launch the game. Do not send credentials or logs containing tokens to anyone.

The upstream CurseForge key is disabled in this fork because it is issued specifically to Prism. Modrinth and local jar installation should be tested independently. Before sharing any build: replace the upstream application ID/config paths/logos/news/update links, document GPL-3.0-only source and CC BY-SA asset obligations, keep Prism contributor notices, obtain original Beer30 artwork, and test a Windows installer and real sign-in. The unvalidated Beer30 movement diagnostic must remain optional and clearly identified as experimental.
