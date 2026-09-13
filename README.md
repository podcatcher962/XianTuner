# 闲听 XianTuner

**单文件本地音乐 / 播客播放器** — 双击即用，零依赖，零网络请求。

[中文](#中文) | [English](#english)

---

## 中文

闲听是一个**单个 HTML 文件**构成的本地音频播放器。用手机或电脑的浏览器打开就能用，不需要安装、不需要账号、不需要联网。所有音频与数据都留在你自己的设备上。

> 为什么做这个：安卓上想装一个「能整文件夹丢进播放列表、整夜循环」的干净播放器，要么下不到官方包，要么权限贪婪。索性自己做一个单文件网页版。

### 在线版

👉 **https://podcatcher962.github.io/XianTuner/**

手机浏览器打开后建议「添加到主屏幕」，用起来和 App 一样。

### 功能

| 分类 | 功能 |
| --- | --- |
| 📁 **曲库** | 单文件多选导入、整文件夹导入（自动建分组）、搜索、4 种排序（加入时间 / 最近播放 / 名称 / 时长） |
| 🗂 **分组与队列** | 每个文件夹自动成为一个分组；分组可整队入队、可记住自己的播放方式（循环 / 随机）；队列可合并、可持久化 |
| ▶️ **播放** | 队列游标驱动、单曲循环 / 列表循环 / 关闭循环、随机播放、倍速 0.8–3.0×、±15s / ±30s 快进后退、睡眠定时（到点淡出暂停） |
| 🎚 **均衡器** | 10 段图形均衡（31Hz–16kHz）、9 个预设（原声 / 流行 / 摇滚 / 爵士 / 古典 / 人声 / 低音增强 / 高音增强 / 助眠柔化）、低音增强、响度补偿、实时频响曲线 |
| 🎨 **主题** | 白天 / 深色 / 跟随系统三态，随系统深浅色自动切换 |
| ♿ **无障碍** | 界面缩放 85%–160%、高对比模式、加大触控热区（44px）、减少动效 |
| 🌐 **语言** | 简体中文 / English / 跟随系统 |
| 🎧 **播放体验** | 暂停淡入淡出、音频焦点（切到后台自动淡出暂停，不与其它应用抢音）、断点续播、Media Session（锁屏与通知栏控制） |
| 💾 **数据** | 音频存入本机 IndexedDB，曲库可导出 / 导入 JSON 备份；另提供「临时模式」不占额外空间 |

### 使用说明

1. **加入音频** — 点「添加音频」挑单个或几个文件；点「添加文件夹」一次导入整个目录（推荐，会自动建分组）。
2. **整夜循环一个文件夹** — 切到「按文件夹」视图 → 点分组 → 选「随机播放」；再到播放页把循环切到「列表循环」，最后设好睡眠定时。
3. **调音** — 设置页 →「均衡器」，选预设或手动拖 10 个频段。
4. **换主题 / 语言 / 字号** — 设置页顶部三张卡片，或顶栏右侧的月亮按钮快速切深色。

详细的帮助、常见问题都在应用内的「说明」标签页里。

### 存储说明

音频会被复制进浏览器的 IndexedDB，所以**数据量大约是原文件的两倍**，且清除浏览器数据会一并清掉曲库。重要音频请保留原始文件，并定期用「导出曲库」做备份。

### 技术说明

- 纯单文件 HTML，**无任何第三方库、无 CDN、无外部字体**
- 音频图：`AudioContext` → `MediaElementSource` → 10 × `BiquadFilter`（首段 lowshelf / 末段 highshelf / 中间 peaking）→ 低音 shelf → `GainNode`（淡入淡出）→ destination
- 存储：IndexedDB 分 `tracks`（元数据）/ `blobs`（二进制）/ `groups`（分组）三个 store，DB v4
- 全站零网络请求，可完全离线使用

### 免责声明

- 本工具为**个人自用的第三方开源工具**，与任何音频平台、内容提供方均无关联，未获其授权或认可。
- 工具**仅提供本地音频文件的播放能力**，本身不提供、不内置、不分发任何音频内容。
- 请仅用于播放你有权使用的音频文件。因使用本工具产生的任何版权或法律纠纷，由使用者自行承担。
- 所有数据仅存于使用者本机浏览器中，作者不收集、不上传、不存储任何用户数据。
- 浏览器存储可能因清理缓存、隐私模式、系统回收而丢失，请自行做好备份。
- 本软件按「现状」提供，不附带任何明示或暗示的担保。

### 作者

**永远的兰兰 (Lanlan Eternal)**

### 许可

MIT License

---

## English

XianTuner is a local audio player that ships as **a single HTML file**. Open it in any browser on your phone or desktop — no installation, no account, no network. All audio and data stay on your own device.

> Why it exists: finding a clean Android player that lets you drop a whole folder into the queue and loop it all night is surprisingly hard — official packages are often unavailable and permission-hungry. So here's a single-file web version instead.

### Live version

👉 **https://podcatcher962.github.io/XianTuner/**

On mobile, add it to your home screen for an app-like experience.

### Features

| Area | What you get |
| --- | --- |
| 📁 **Library** | Multi-file import, whole-folder import (auto-creates a group), search, 4 sort modes (added / recently played / name / duration) |
| 🗂 **Groups & queue** | Every folder becomes a group; groups can be queued in one tap and remember their own play mode (loop / shuffle); queues can be merged and persisted |
| ▶️ **Playback** | Cursor-driven queue, repeat-one / repeat-all / off, shuffle, speed 0.8–3.0×, ±15s / ±30s seek, sleep timer (fades out and pauses) |
| 🎚 **Equalizer** | 10-band graphic EQ (31Hz–16kHz), 9 presets, bass boost, loudness compensation, live response curve |
| 🎨 **Theme** | Light / dark / follow-system |
| ♿ **Accessibility** | UI scaling 85%–160%, high contrast, larger tap targets (44px), reduced motion |
| 🌐 **Language** | 简体中文 / English / follow system |
| 🎧 **Listening** | Pause fade in/out, audio focus (auto fade-and-pause when backgrounded), resume-where-you-left-off, Media Session (lock screen & notification controls) |
| 💾 **Data** | Audio stored in on-device IndexedDB; library export/import as JSON; a "temporary mode" that uses no extra space |

### Usage

1. **Add audio** — tap *Add audio* for individual files, or *Add folder* to import a whole directory (recommended; groups are created automatically).
2. **Loop a folder all night** — switch to folder view → tap the group → *Shuffle*; then set the player to repeat-all and configure the sleep timer.
3. **Tune the sound** — Settings → *Equalizer*, pick a preset or drag the 10 bands.
4. **Change theme / language / font size** — the top three cards in Settings, or the moon button in the header.

Full help and FAQ live in the *Docs* tab inside the app.

### Storage notes

Audio files are copied into the browser's IndexedDB, so **storage usage is roughly double the original size**, and clearing browser data will also clear your library. Keep your original files and use *Export library* for backups.

### Technical notes

- Single-file HTML — **no third-party libraries, no CDN, no external fonts**
- Audio graph: `AudioContext` → `MediaElementSource` → 10 × `BiquadFilter` (lowshelf / peaking ×8 / highshelf) → bass shelf → `GainNode` (fade) → destination
- Storage: IndexedDB with separate `tracks` / `blobs` / `groups` stores, DB v4
- Zero network requests — fully offline capable

### Disclaimer

- This is a **personal, third-party open-source tool**. It is not affiliated with, authorized by, or endorsed by any audio platform or content provider.
- The tool **only plays local audio files you already have**. It does not provide, bundle, or distribute any audio content.
- Please use it only with audio you have the right to use. Any copyright or legal issues arising from its use are the sole responsibility of the user.
- All data stays in your local browser. The author collects, uploads, and stores nothing.
- Browser storage can be lost to cache clearing, private mode, or system reclamation — keep your own backups.
- Provided "as is", without warranty of any kind.

### Author

**Lanlan Eternal (永远的兰兰)**

### License

MIT License
