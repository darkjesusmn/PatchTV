# PatchTV - Portable Windows x64 Testing Build

This package contains Patch TV and its authored data/branding, dependency
manifest and required notices, but no VLC, .NET runtime or LibVLCSharp binaries.
The native launcher embeds approved download URLs, sizes and hashes. The JSON
manifest is a readable copy, not an untrusted replacement for embedded policy.

The folder and ZIP are named PatchTV followed by the installed version number.
This is the only release format; no separate bundled/offline package is built.
Extract the entire folder to a writable location and open the top-level
Patch_TV.exe. Accept setup to download missing support files. Internet and
adequate disk space are needed for first setup. No global installation or normal
administrator permission is required. Do not open the internal app host.

Downloaded files, staging, installed dependencies, settings and logs stay under
this Patch TV folder. A verified compatible Windows host runtime may be reused
read-only; otherwise approved runtimes are installed privately here. VLC and its
managed wrappers are kept in separate component folders under dependencies.

If setup fails, use Retry or Close and reopen. Verified completed downloads are
reused; unfinished transfers currently restart from zero. Keep the folder
intact. Once setup succeeds, later launches reuse installed components; streaming
still requires internet. Move the whole folder only after closing the app.

This is an unsigned private testing build, NOT a public-distribution approval.
Source/license/feed/signing review remains open. Windows may display a security
warning; do not disable protection or run unverified downloads. Test on Windows
x64; this is not a smart-TV, macOS, Linux or Chromebook release.

Test first setup, logo/progress, channel browsing/playback, favorites/theme
persistence, restart and moving the closed folder. Do not overwrite an existing
used Patch TV folder. Application self-updates/rollback remain unavailable.
Real clean-machine and removable-device acceptance are separate outstanding
checks; a controlled missing-host fixture is not clean-machine certification.
