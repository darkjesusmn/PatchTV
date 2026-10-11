<img width="1254" height="1254" alt="PatchTV Raccoon Lounge Logo" src="https://github.com/user-attachments/assets/40776525-17f1-4b60-ba7f-adec25443a8b" />

## PatchTV

**Free, portable IPTV and live TV for Windows — built to make finding and watching channels simple.**

> **Release documented:** patchTV 3.2.31 (Windows x64)  
> **Status:** Actively developed; streaming availability varies by provider and region.  
> **Platform:** Windows 10/11, 64-bit.

patchTV is a Windows desktop television application built around a large, organized catalog of publicly accessible internet TV streams. Its goal is to bring live news, movies, TV, sports, local stations, documentaries, music, and more into a single easy-to-use interface—without forcing users to jump between dozens of websites.

The app started with a focus on **one-click TV for people who want television, not a complicated media center**. It remains focused on simple navigation, legible controls, straightforward categories, and an experience that is practical for older family members as well as enthusiasts.

**patchTV is a player and catalog interface, not a broadcaster or paid-TV provider.** It does not grant subscriptions or guarantee access to any particular station.

## Contents

- [What patchTV does](#what-patchtv-does)
- [Project scope and design principles](#project-scope-and-design-principles)
- [Features in the 3.2.22 baseline](#features-in-the-3222-baseline)
- [Channels and catalog](#channels-and-catalog)
- [Requirements](#requirements)
- [Download and installation](#download-and-installation)
- [First launch: what to expect](#first-launch-what-to-expect)
- [How to use patchTV](#how-to-use-patchtv)
- [Updating patchTV manually](#updating-patchtv-manually)
- [Troubleshooting](#troubleshooting)
- [Known limitations and issues](#known-limitations-and-issues)
- [Development roadmap](#development-roadmap)
- [Technical overview](#technical-overview)
- [Privacy, network access and content](#privacy-network-access-and-content)
- [Reporting issues and contributing](#reporting-issues-and-contributing)
- [Disclaimer](#disclaimer)

## What patchTV does

patchTV aggregates stream listings from supported public channel catalogs, organizes them into browsable TV categories, and plays supported streams through an embedded VLC-based player.

Typical uses include:

- Watching a live news broadcast without visiting the station's website.
- Browsing movie, television, documentary, entertainment, and specialty channels.
- Discovering regional/local programming.
- Finding channels by name or category rather than remembering stream URLs.
- Keeping favorite channels handy for repeat viewing.
- Using a convenient portable Windows application instead of a collection of browser tabs.

Some entries may be FAST (*free ad-supported streaming television*) channels rather than conventional over-the-air television stations. Availability, ads, programming, and quality are controlled by their respective sources.

## Project scope and design principles

**The primary goal is a reliable, simple, one-click TV experience.** The app should be approachable for someone who rarely uses computers, while still providing discovery tools and optional advanced controls.

Core principles:

1. **Easy to start:** Launch from the extracted application folder, without requiring a complex installation workflow.
2. **Easy to navigate:** Clear categories, search, favorites, and practical controls.
3. **English-first, not English-only:** Favor English-language discovery while retaining a path to international programming.
4. **No unnecessary channel hiding:** Unclassified, niche, and international entries should stay discoverable rather than silently disappearing.
5. **Portable by design:** Make it practical to move or back up an installation folder.
6. **No paid API requirement for basic use:** Basic TV discovery and playback should not depend on a paid guide service.
7. **Honest playback status:** Not every listed URL will work forever. Failures should be communicated rather than silently ignored.
8. **Preserve personal choices:** Favorites, settings, and future history should survive upgrades when possible.
9. **Low-maintenance TV:** Reduce repeated configuration, pop-ups, dead ends, and unnecessary clicking.

### What patchTV is not

- Not an official service from Netflix, Hulu, Tubi, Pluto TV, Samsung, Roku, Plex, or any television network.
- Not a replacement for an internet connection.
- Not an IPTV subscription or a supplier of premium-channel credentials.
- Not a guarantee that a channel will always be online or available in your country.
- Not a tool for bypassing DRM, subscriptions, geographic restrictions, or content licensing.
- Not yet a full DVR, recording service, or universal TV-guide platform.

## Features in the 3.2.22 baseline

The established patchTV design includes:

| Area | Description |
| --- | --- |
| Desktop interface | Windows application designed for straightforward channel navigation and playback |
| Portable distribution | Release supplied as an extractable Windows application folder |
| Embedded playback | VLC/LibVLC-based media playback |
| Large catalog | **10,560 entries** in the audited 3.2.22 categorized catalog; *entries are not a count of unique working channels* |
| Categories | Browsing by television or content type, with categorized and international content |
| Channel search | Find channels by name rather than scanning every category |
| Favorites | Keep preferred channels easy to access |
| Themes/UI | Dark, television-oriented application experience |
| Multiple sources | Catalog combines entries attributed to multiple public streaming sources |
| Multiple stream candidates | Some catalog entries include multiple URL candidates; **automatic failover is not confirmed as implemented** |
| Verification metadata | Catalog includes historical stream-check information; **not a live uptime guarantee** |

**Important:** The presence of an entry, category, stream candidate, or verification flag in the catalog does not mean the channel is playable right now. Features shown on planned mockups or discussed for a future release should not be assumed to exist in 3.2.22.

## Channels and catalog

The audited 3.2.22 channel data contains:

| Catalog characteristic | Audited value |
| --- | ---: |
| Catalog entries | 10,560 |
| Distinct `StableChannelId` values | 9,990 |
| Entries with two or more stream candidates | 2,092 |
| Entries with one stream candidate | 8,468 |
| Historical stream verification | September 13–14, 2026 |

The difference between catalog entries and distinct identifiers is under investigation. A channel *entry* may be duplicated, may have several stream links, or may not be currently accessible. Do not interpret 10,560 as 10,560 simultaneous, unique, playable stations.

The baseline catalog contains provider/source labels including **IPTV-org, Free-TV, Samsung TV Plus, Roku, Plex, Pluto TV, Tubi, and LegalStream**. Those labels describe source attribution, not ownership, endorsement, or guaranteed access.

### Expected content areas

Depending on catalog coverage and source availability, patchTV aims to make these types of television easy to find:

- Movies, TV shows, and classic television
- Local, regional, national, and international news
- Sports and sports-related programming
- Science, history, and nature
- Kids and family content
- Anime, music, and entertainment
- Cooking, travel, cars, and outdoor programming
- Relaxation and ambient video
- Minnesota and other regional/local stations
- International-language channels

Category names and the selection of playable stations may change between catalog versions. Not every premium-sounding channel listing is an authorized or working stream.

## Requirements

- **OS:** Windows 10 or Windows 11, 64-bit.
- **Internet:** Required for retrieving and playing live online streams.
- **Architecture:** x64 release.
- **Storage:** Enough room to extract the entire release and retain cache/settings; actual size depends on the release archive.
- **Media engine:** The 3.2.22 application uses LibVLC. Keep any packaged native playback files together with the release.
- **Permissions:** A normal writable folder is recommended. Avoid installing into protected locations when possible.

The audited implementation is based on **.NET 10 Windows Forms** with **LibVLCSharp.WinForms 3.10.1**. Do not assume installing the standalone VLC desktop application substitutes for the native libraries required by a particular build. Follow any dependency/setup prompts provided by the *official release launcher*.

## Download and installation

**Use the packaged release ZIP, not GitHub's automatic “Source code (zip)” archive, unless you intend to build the application yourself.**

1. Open this repository's **Releases** section.
2. Download the latest Windows x64 patchTV release ZIP.
3. In Windows File Explorer, right-click the ZIP and choose **Extract All**.
4. Choose a simple location, for example `C:\Apps\patchTV\` or a folder in your user profile.
5. **Extract the complete folder.** Do not run the app directly from inside the ZIP and do not move only the EXE away from its supporting files.
6. Open the extracted folder and launch the **included patchTV launcher** (the Windows executable/launcher supplied with that release).
7. Follow any first-run setup or dependency dialogs displayed by the launcher.
8. Once the main window opens, use the catalog or search to select a channel.

> **Packaging note:** The exact launcher executable filename and any first-run setup prompts should be taken from the downloaded release. This README does not claim a filename that has not been verified against the release ZIP.

### Portable installation

patchTV is designed for use as a self-contained folder. You can normally keep the extracted directory on a local drive and create a desktop shortcut to its launcher.

**Do not move, rename, or delete individual runtime DLLs, the `Data` directory, or bundled media components.** A portable app still depends on its complete file structure.

For best results, put patchTV in a user-writable folder rather than `C:\Program Files\`.

### Creating a desktop shortcut

Right-click the launcher in the extracted folder and choose **Show more options → Send to → Desktop (create shortcut)** (wording differs by Windows version). Use that shortcut for future launches.

## First launch: what to expect

The first run may take longer than a normal launch because the portable launcher may need to validate its packaged components, check prerequisites, or create application data. Exactly which setup actions occur depends on the specific release.

The expected user experience is:

1. Start the release's included launcher.
2. Allow legitimate, expected setup prompts from that release.
3. Wait for the patchTV interface and available channel catalog to load.
4. Browse categories or search for a familiar station.
5. Select a channel to begin streaming.
6. Adjust favorites, theme, and other available settings to your preference.

For troubleshooting, test with a few different stations. A single stream failing is **not** proof the application is broken.

**Security:** Do not accept unexplained administrator prompts, install unknown codecs, or disable security software to make the app run. If Windows blocks an unfamiliar build, confirm you downloaded it from the repository's intended Releases page and verify published hashes if supplied.

**Data:** First launch may create or update user configuration and cache. Back up the application folder before major upgrades if you want to retain personalized settings.

## How to use patchTV

### Find something to watch

Open the app, choose a relevant category, or use Search. Select a channel from the results and allow a moment for the stream to load. Startup speed varies by source and internet connection.

### Browse by category

Use categories for discovery, including movie and TV content, news, regional channels, and international programming. A category is an organizational convenience, not a statement that every listed feed is live and accessible.

### Search

Search for a station name, program brand, or channel keyword. If nothing appears, try a shorter term, a regional call sign, or a broader category. Some catalog names are provider-specific.

### Favorites

Use the app's favorite controls to save frequently watched stations. The release's interface determines the exact control location.

### Playback and fullscreen

Select a stream to open it in the embedded player. Use the playback controls provided by the current release to stop playback or change viewing mode. If a feed freezes, switch to a different station and return, or restart playback.

### Local and international stations

Availability is determined by the source. A listed local station may be a news-only feed rather than a full broadcast affiliate, and some feeds may be geographically restricted.

### What to do if a channel fails

Try another channel first. If others play, the problem is probably stream-specific rather than a complete app failure. See [Troubleshooting](#troubleshooting).

## Updating patchTV manually

**Recommended method: clean versioned upgrade with a backup.**

1. Close patchTV completely.
2. Locate your existing installation folder.
3. Make a full backup of that folder, especially saved settings, favorites, and any `Data/user/` content if present.
4. Open the GitHub repository's **Releases** page and download the newer **packaged Windows x64 release ZIP**.
5. Extract the new release to **a new folder**, e.g. `C:\Apps\patchTV-3.3\`; do not overwrite the old installation initially.
6. Read that release's changelog or migration notes.
7. If the release documents a settings/favorites migration procedure, follow it. **Do not blindly replace all of the new `Data` directory with the old one**, because catalog formats or defaults may have changed.
8. Launch the new version and verify playback, categories, theme, and favorites.
9. Update your desktop shortcut to point to the new launcher.
10. Keep your previous working release until the new version is confirmed stable.

### If favorites or settings do not transfer

Do **not** delete the old install. Restore it, then check the new release notes for the supported data migration path. The channel identifier scheme has known collision concerns, and copying files between schema versions without a documented migration can introduce lost or misassigned favorites.

### Updating channel listings versus updating the application

These are different:

- **Application update:** Download and extract a new patchTV release as described above.
- **Catalog/playlist refresh:** Use the refresh/update function *if your installed version exposes one*. Its behavior is version-dependent. A catalog refresh does not necessarily update the program binaries or repair a dead upstream stream.

### Rolling back

Close the new version and launch the prior version from the backup folder. Restore only matching settings backups for that release. Avoid loading data migrated to a newer format into an older version unless rollback support is documented.

## Troubleshooting

| Problem | What to check |
| --- | --- |
| App does not launch | Confirm Windows x64, full ZIP extraction, correct launcher, complete native DLL/dependency files, and a writable location |
| Windows warns about the application | Verify the download source and published checksums/signatures, if available; do not blindly bypass security warnings |
| No channels appear | Confirm catalog files were included, restart, and test the configured update/refresh action if available |
| One station will not play | Try another station; the original stream may be offline, removed, region-blocked, or incompatible |
| Many stations fail | Check internet access, local firewall, source outages, time/date settings, and whether the catalog is stale |
| Playback freezes or buffers | Check connection stability; try a different feed or lower-bandwidth station |
| Video plays without sound | Check Windows output device and player volume; some streams have broken audio tracks |
| Favorites disappear after an update | Return to the previous installation backup; inspect migration notes rather than overwriting data files blindly |
| Cannot save preferences | Move the portable folder to a writable location; avoid protected system directories |
| Channels have incorrect names/categories | Report the channel, source, category, and the expected placement |
| Provider link works in a browser but not patchTV | The provider may use tokens, headers, DRM, browser-specific playback, or region checks that are not supported by this player |

### Before reporting a bug

Test whether it happens on one channel or multiple channels, and whether restarting the application changes the result. Record your patchTV version, Windows version, error message, and the steps needed to reproduce the issue.

**Do not publish account credentials, access tokens, full signed stream URLs, or private data in issues or logs.**

## Known limitations and issues

This section distinguishes **audited catalog risks** from **symptoms that still need reproduction**. It is not a claim that every item reproduces for every user.

| Status | Issue / limitation | Impact |
| --- | --- | --- |
| **Confirmed in the audited data** | Catalog contains 10,560 entries but only 9,990 distinct `StableChannelId` values | Some IDs are not unique. Future favorites/history migration must handle collisions safely |
| **Confirmed in the audited data** | 8,468 entries have only one stream candidate | No alternative URL is stored for those entries if the stream fails |
| **Confirmed in the audited data** | Stream-check metadata dates to September 2026 | “Previously verified” does not equal “currently online” |
| **Confirmed in the audited data** | Catalog rows do not include EPG/program/TVG scheduling fields | A complete Now/Next guide requires separate EPG ingestion and channel mapping |
| **Expected external limitation** | Providers can remove links, rotate URLs, restrict regions, or change playback requirements | Some channels will fail without any app change |
| **Needs targeted testing** | Duplicated entries, unexpected categorization, or lost favorites following future migration | Requires regression testing across application updates |
| **Not confirmed as delivered in 3.2.22** | Automatic stream failover and continuous channel health scoring | Treat as roadmap features, not guarantees |
| **Not confirmed as delivered in 3.2.22** | Real EPG Now Playing, Simple/Advanced split, personalized home screen | Planned work, not baseline behavior |

If you discover a reproducible application bug, please open an issue with enough detail to investigate it.

## Development roadmap

These are **planned improvements**, not claims about completed features. Exact scope, order, and delivery dates may change.

### Next major feature set: proposed 3.3 series

- [ ] **Automatic stream failover:** Detect a failed or stalled stream, try sensible alternate candidates, and avoid rapid endless retry loops.
- [ ] **Channel-health monitoring:** Track successful playback, recent failures, and likely stream reliability over time. Distinguish historical metadata from current observations.
- [ ] **Real Now Playing / Next guide:** Use optional XMLTV-compatible guide data when available, map channels to programming, handle time zones, and clearly mark missing/stale schedules.
- [ ] **Simple Mode:** Large, obvious controls, reduced visual clutter, and easier use from a couch or by an older viewer.
- [ ] **Advanced Mode:** More details and controls for troubleshooting, diagnostics, provider/stream selection, and enthusiast settings.
- [ ] **Personalized home screen:** Favorites, recently watched, last channel, useful categories, and configurable home sections.
- [ ] **Safe upgrade migrations:** Preserve favorites and preferences despite legacy channel ID collisions.
- [ ] **Safer caching and persistence:** Versioned user data, backups, atomic saves, and graceful handling of damaged settings files.
- [ ] **Playback stress testing:** Validate rapid channel switching, long play sessions, network drops, and shutdown behavior.

### Longer-term ideas

- [ ] Better source freshness reporting and on-demand catalog validation.
- [ ] Easier channel corrections and report-a-broken-channel workflow.
- [ ] More accurate local/regional metadata and category auditing.
- [ ] More robust channel artwork and metadata handling.
- [ ] Improved keyboard navigation, high-DPI support, and accessibility.
- [ ] A release changelog, upgrade checks, and optional update notifications.
- [ ] Additional personalization controls without an account or cloud tracking.

**Roadmap rule:** Reliability, stream handling, and simple navigation take priority over adding complexity for its own sake.

## Technical overview

The audited 3.2.22 baseline uses:

| Component | Technology |
| --- | --- |
| Desktop framework | C# / .NET 10 / Windows Forms |
| Playback integration | LibVLCSharp.WinForms 3.10.1 |
| Launcher | Portable native launcher built with Zig |
| Channel catalog | JSON |
| Application assembly | `DJMN.TV.Core` |
| Verified catalog location in audited baseline | `Data/verified/verified_channels_categorized_v10_final_global_sorted.json` |

Catalog records may include multiple stream objects, URL hashes, verification timestamps, video/audio check flags, visibility metadata, and language/category information.

**For developers:** A packaged release ZIP is not necessarily the editable application source repository. Do not assume the extracted binary package contains everything necessary to rebuild patchTV. Build instructions, source code, and test projects should be published separately when available.

The roadmap requires careful handling of channel identity, cancellable background operations, network timeouts, UI threading, LibVLC resource disposal, and local data migrations.

## Privacy, network access and content

patchTV requires network access to load online media streams and may use network access for catalog updates or optional future program-guide data. The source provider may see ordinary request information (including IP address and user-agent) when a stream is requested.

The project is intended to work without requiring a patchTV user account or paid API service for basic television playback. This is a **design goal**, not an independent audit of telemetry or every network request.

Please obtain streams from authorized sources and comply with the terms and regional restrictions of each provider. Listings do not imply patchTV owns or redistributes the underlying programming. Channels can contain advertising controlled by third-party providers.

## Reporting issues and contributing

Use the repository's **Issues** tab to report:

- Broken launch or update flows
- Reproducible crashes and playback failures
- Channels with stale, incorrect, or duplicate metadata
- Missing categories, inappropriate categorization, or hidden entries
- Accessibility and simple-mode usability problems
- Feature requests aligned with the roadmap

A helpful bug report includes:

```text
patchTV version:
Windows version:
What I tried:
What happened:
What I expected:
Can I reproduce it?:
One channel or multiple?:
Error text / screenshots:
Did it work in a previous version?:
```

Do not paste private IPTV credentials, signed URL tokens, or unrelated personal information into public issues.

Pull requests and technical contributions should be targeted, documented, and tested against existing playback and favorite-management behavior. Preserve existing catalog entries unless removal is explicitly justified and reviewed.

## Disclaimer

patchTV is an independent software project. All channel names, logos, trademarks, and programming remain the property of their respective owners. Stream availability and legality depend on the underlying source and jurisdiction. The app does not authorize access to restricted or subscription-only content. No stream uptime, completeness, or uninterrupted playback is guaranteed.

---

**patchTV — turn on the TV, find a channel, and watch.**
