# Beer30 launcher fork feasibility

This source tree is based on Prism Launcher develop at commit 1a1a11458231fb897941bf4360531768f9dbf556. It is NOT yet a Beer30 executable or installer.

Prism Launcher is GPL-3.0-only. Redistribution of a modified binary requires the corresponding source and license notices. Its art has separate CC BY-SA 4.0 terms; replace branding with original Beer30 assets rather than presenting Prism logos as Beer30. This fork must state it is not endorsed by or affiliated with Prism Launcher.

Prism's README explicitly permits forks/custom builds and says to replace API keys or disable them; it separately says that retaining its included Microsoft identity client ID means accepting Microsoft Identity Platform terms. Before a distributable release, confirm the applicability of those terms and test real account sign-in; this is not a guarantee that Microsoft will accept a Beer30-branded build. The CurseForge key was issued specifically for Prism and has been disabled here; do not re-enable it without Beer30's own authorization.

The project requires CMake, Qt 6.8, KDE ECM, cmark and platform build tooling. None were present in the current sandbox, and Windows execution is unavailable. No binary was compiled and no Microsoft sign-in was tested. A proper rebrand needs separate app identity, icons, resource manifests, configuration paths, links and update channels, not only a renamed window or filename. Keep the old launcher download labeled as a setup helper until a runnable standalone build exists.
