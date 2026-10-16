# ⌘ Personal Bio — Terminal Edition

> A customizable, cyberpunk-inspired personal bio website featuring animated visuals, a live Discord presence, an interactive terminal, and a built-in SoundCloud music player.
A minimal, single-page personal website designed to showcase your identity, skills, social links, and current Discord activity — with a dark aesthetic, glitch effects, and a terminal-inspired interface.
Preview: https://superb-horse-71bf06.netlify.app/

**No frameworks. No build tools. Just HTML, CSS, and vanilla JavaScript.**

## ✨ Features

- **🖥️ Terminal Boot Screen** — An animated startup sequence with simulated commands and a click-to-enter transition.
- **👤 Animated Profile Card** — A profile avatar with a rotating gradient ring, glowing effects, a 3D flip animation, and a customizable username.
- **⚡ Glitch & Neon Effects** — Animated text, glowing accents, scanlines, background effects, and smooth transitions.
- **🎨 Customizable Theme** — Change the primary and accent colors to match your personal aesthetic.
- **🟢 Live Discord Presence** — Display your Discord status and activity in real time using the [Lanyard API](https://lanyard.rest/).
- **🎵 SoundCloud Music Player** — An integrated audio player with play/pause, volume control, seeking, track progress, and animated equalizer bars.
- **🔗 Social Links** — Configurable Discord, Telegram, TikTok, and other supported profile links.
- **💻 Interactive Terminal** — A draggable, resizable terminal window with custom commands and profile information.
- **⌨️ Dynamic Username** — Your configured username automatically updates the page title, profile heading, footer, and terminal prompts.
- **🧩 Custom Skills** — Display programming languages, technologies, or any other tags with optional icons.
- **📱 Responsive Design** — Adapts to different screen sizes, including mobile devices.
- **🖱️ Custom Cursor** — A glowing cursor effect on devices with a mouse or trackpad.
- **🔍 Social Preview Metadata** — Open Graph and theme-color metadata for browser and social sharing previews.

## 🛠️ Tech Stack

| Technology | Purpose |
| --- | --- |
| HTML5 | Website structure |
| CSS3 | Styling, animations, effects, and responsive layout |
| Vanilla JavaScript | Configuration, interactions, and dynamic content |
| WebSocket | Real-time Discord presence updates |
| Lanyard API | Discord status and activity data |
| SoundCloud Widget API | Embedded music playback |
| Google Fonts | Orbitron and JetBrains Mono typography |

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
cd YOUR_REPOSITORY
```

Replace `YOUR_USERNAME` and `YOUR_REPOSITORY` with your GitHub details.

### 2. Configure your profile

Open `index.html` and find the `SITE CONFIGURATION` section near the top of the file.

```js
window.CONFIG = {
    themeColor: "#ffffff",
    accentColor: "#d3d3d3",

    username: "yourname",
    discordId: "YOUR_DISCORD_ID",
    avatarPath: "avatar.png",

    musicUrl: "https://api.soundcloud.com/tracks/YOUR_TRACK_ID",
    trackTitle: "Your Favorite Song",

    about: "A short description about yourself",
    projects: "Your projects",

    contactLinks: {
        discord: "yourdiscord",
        telegram: "https://t.me/yourusername"
    },

    skills: [
        { name: "JavaScript", icon: "⚡" },
        { name: "Python", icon: "🐍" },
        { name: "HTML & CSS", icon: "🌐" }
    ]
};
```

This is an example configuration. Keep the existing structure in your `index.html` and replace the values with your own.

### 3. Add your avatar

Place your profile image in the project root and name it `avatar.png`, or change `avatarPath` to point to your own image.

```text
your-repository/
├── index.html
├── avatar.png
└── README.md
```

### 4. Run locally

You can open `index.html` directly in your browser. For a more consistent local development experience, run a simple HTTP server:

```bash
python -m http.server 8000
```

Then visit [http://localhost:8000](http://localhost:8000).

### 5. Deploy with GitHub Pages

1. Push your files to a GitHub repository.
2. Open the repository's **Settings → Pages**.
3. Under **Build and deployment**, select **Deploy from a branch**.
4. Select your branch (usually `main`) and the root (`/`) folder.
5. Save and wait for GitHub Pages to publish your website.

No compilation or package installation is required.

## ⚙️ Configuration Guide

Everything is designed to be easy to personalize from the `window.CONFIG` object.

| Option | Description |
| --- | --- |
| `themeColor` | Main theme color, used for accents and visual effects |
| `accentColor` | Glow color for borders, animations, and highlights |
| `username` | Profile name, page title, footer, and terminal username |
| `discordId` | Discord user ID used for Lanyard presence |
| `avatarPath` | Path to your profile picture |
| `musicUrl` | SoundCloud track URL |
| `trackTitle` | Custom title displayed in the player |
| `about` | Text returned by the terminal's `about` command |
| `projects` | Project information reserved for customization |
| `contactLinks` | Social profiles and contact information |
| `skills` | Array of skills displayed on the profile card |

### 🎨 Changing the colors

For example, to switch to a red theme:

```js
themeColor: "#ff003c",
accentColor: "#ff3355",
```

You can use any valid CSS color value, including HEX, RGB, and HSL.

### 🧑 Changing your skills

Add or remove entries in the `skills` array:

```js
skills: [
    { name: "Python", icon: "🐍" },
    { name: "C++", icon: "⚙️" },
    { name: "JavaScript", icon: "⚡" },
    { name: "SQL", icon: "🗄️" }
]
```

Each entry contains a `name` and an optional `icon`. Set `icon` to an empty string if you prefer text-only tags.

### 🔗 Configuring social links

The website supports Discord, TikTok, and Telegram links in its current implementation.

```js
contactLinks: {
    discord: "yourdiscord",
    telegram: "https://t.me/yourusername",
    tiktok: "https://www.tiktok.com/@yourusername"
}
```

- **Discord:** Clicking the icon copies the configured Discord username to the clipboard.
- **Telegram:** Opens the configured URL.
- **TikTok:** Opens the configured profile URL.

Optional links are rendered when their configuration values are present. The existing Discord integration expects a username for the copy action, rather than a Discord invite URL.

### 🎵 Setting up music

Set `musicUrl` to your SoundCloud track URL and `trackTitle` to the name you want displayed.

```js
musicUrl: "https://api.soundcloud.com/tracks/YOUR_TRACK_ID",
trackTitle: "Artist — Track Name"
```

The player uses the SoundCloud Widget API. Playback depends on the availability and embedding permissions of the selected track, and browsers may require a user interaction before audio can play.

## 💻 Interactive Terminal

The website includes a terminal-inspired window with a command prompt, command history, resizing, dragging, and minimize/maximize controls.

Type `help` into the terminal to see the available commands.

| Command | Description |
| --- | --- |
| `help` | List available commands |
| `about` | Display your configured description |
| `skills` | Display your configured skills |
| `contact` | Show configured contact information |
| `status` | Check your Discord presence |
| `music` | Toggle music playback |
| `discord` | Copy your Discord username |
| `clear` | Clear the terminal output |
| `dontopen` | Trigger a playful visual easter egg |

The terminal is an interactive front-end feature, not a real operating-system shell. Its commands do not execute system commands on your computer.

## 🟢 Discord Presence Setup

The live presence feature uses [Lanyard](https://lanyard.rest/) to retrieve Discord status and activity updates.

1. Join the [Lanyard Discord server](https://discord.gg/lanyard).
2. Find your Discord User ID. Enable Developer Mode in Discord, then right-click your profile and select **Copy User ID**.
3. Set `discordId` in `window.CONFIG` to your numeric user ID.
4. Open the website and check your profile status.

The integration can display online, idle, Do Not Disturb, and offline states, along with supported activity information such as games, Spotify listening, and custom status.

**Note:** Presence data depends on Lanyard availability, Discord activity visibility, and your account's current status. It may not always be available.

## 📂 Project Structure

```text
.
├── index.html      # Main website, styling, scripts and configuration
├── avatar.png      # Your profile image
└── README.md       # Project documentation
```

The project is intentionally lightweight. Most customization happens directly in `index.html`, while your avatar is stored as a separate asset.

## 🔒 Privacy & Third-Party Services

This website runs primarily in the visitor's browser. However, some features rely on external services:

- **Lanyard:** Provides Discord presence information for the configured user ID.
- **SoundCloud:** Provides embedded audio playback.
- **Google Fonts:** Loads the fonts used by the interface.

Review these services and their privacy policies before deploying your own version. Do not add private credentials, access tokens, or other secrets to a public repository.

## 🤝 Contributing

Contributions, improvements, bug reports, and feature suggestions are welcome!

1. Fork the repository.
2. Create a branch for your changes.
3. Make your changes and test them in a browser.
4. Submit a pull request with a clear description.

Ideas for future improvements include additional themes, more social integrations, accessibility improvements, and expanded profile customization.

## 📜 License

This project is intended to be open source. Add a `LICENSE` file to the repository to specify the permissions and conditions for using, modifying, and distributing the code.

Until a license is added, do not assume that the repository grants permission to reuse or redistribute the code.

---

<p align="center">
  <b>Made for developers who like their profiles a little different.</b>
  <br />
  Customize it, make it yours, and share it with the world.
</p>
