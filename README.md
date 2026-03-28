# myTvOnly — Personal Malaysian TV & Radio Playlist

Personal M3U playlist for Malaysian TV channels and radio. Maintained by me, used on Apple TV via IPTV app.

---

## Add to Apple TV

1. Push this repo to GitHub (see setup below)
2. Get the raw URL of `playlist.m3u`:
   ```
   https://raw.githubusercontent.com/YOUR_USERNAME/myTvOnly/main/playlist.m3u
   ```
3. Open your IPTV app on Apple TV (e.g. **GSE Smart IPTV**, **IPTV Smarters**, **Flex IPTV**)
4. Add playlist → paste the raw URL above

---

## Setup (first time)

```bash
cd myTvOnly
git init
git add .
git commit -m "init playlist"
git remote add origin https://github.com/YOUR_USERNAME/myTvOnly.git
git push -u origin main
```

Replace `YOUR_USERNAME` with your GitHub username. Make sure the repo is **public** so Apple TV can fetch the raw file without authentication.

---

## Channels

### TV Malaysia (HLS — works on Apple TV)
| Channel | Source | Notes |
|---------|--------|-------|
| TV1 | RTM / CloudFront | Stable |
| TV2 | RTM / CloudFront | Stable |
| TV6 | RTM / CloudFront | Stable |
| Okey TV | RTM / CloudFront | Stable |
| Berita RTM | RTM / CloudFront | Stable |
| Sukan RTM | RTM / CloudFront | Stable |
| Astro Awani | CloudFront HLS | Usually stable |
| TV Ikim | vediostream HLS | May need update |

### TV Malaysia (DASH+DRM — may not work on all IPTV apps)
| Channel | Notes |
|---------|-------|
| TV3 | Astro JITP, clearkey DRM |
| 8TV | Astro JITP, clearkey DRM |
| TV9 | Astro JITP, clearkey DRM |
| TV Alhijrah | Astro JITP, clearkey DRM |

> **Apple TV note:** DASH+DRM channels require your IPTV app to support MPEG-DASH and ClearKey decryption. If they don't work, try **Flex IPTV** or **GSE Smart IPTV**.

### Radio Malaysia
Hot FM, Fly FM, Hitz FM, Best FM, Era FM, Sinar FM, 8 FM, Kool 101, Nasional FM, Radio Klasik, Johor FM, Asyik FM, Ikim FM

---

## How to Update a Broken Stream

When a channel stops working, edit `playlist.m3u` directly on GitHub or locally:

1. Find the broken channel entry (search by channel name)
2. Replace the stream URL with the new one
3. Commit and push — the IPTV app will pick up changes on next refresh

### Where to find new stream URLs
- Check [siaranMy](https://github.com/MIFNtechnology/siaranMy) — they maintain a similar community playlist
- For RTM channels: the CloudFront base URL is `d25tgymtnqzu8s.cloudfront.net/smil:{channel}/chunklist_b1096000_slENG.m3u8`
  - Known channel names: `tv1`, `tv2`, `tv6`, `okey`, `berita`, `sukan`
- For Astro DASH: the MPD URL format is `https://linearjitp-playback.astro.com.my/dash-wv/linear/{channel_id}/default_primary.mpd`

### Useful channel IDs (Astro JITP)
| Channel | ID |
|---------|----|
| TV3 | 809 |
| 8TV | 911 |
| TV9 | 705 |
| TV Alhijrah | 1113 |

---

## EPG (TV Guide)

Playlist uses EPG from [AqFad2811/epg](https://github.com/AqFad2811/epg). Your IPTV app should pick it up automatically if it supports M3U EPG. If not, manually add:
```
https://raw.githubusercontent.com/AqFad2811/epg/main/epg.xml
```

---

## File Structure

```
myTvOnly/
├── playlist.m3u          ← edit this to add/fix/remove channels
└── README.md             ← this file
```

That's it. One file to maintain.
