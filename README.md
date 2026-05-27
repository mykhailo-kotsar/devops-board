# DevOps Task Board

A lightweight, offline-first Kanban task manager — single HTML file, zero dependencies, works directly in the browser.

![HTML](https://img.shields.io/badge/HTML-single%20file-orange?style=flat-square)
![No Dependencies](https://img.shields.io/badge/dependencies-none-success?style=flat-square)
![Languages](https://img.shields.io/badge/languages-EN%20%7C%20RU%20%7C%20UK-blue?style=flat-square)
![License](https://img.shields.io/badge/license-MIT-green?style=flat-square)

---

## Features

| Feature | Description |
|---|---|
| 🗂 **Kanban Board** | Drag & drop tasks between customizable columns |
| ✅ **Subtasks** | Subtasks with checkboxes and progress bar per card |
| ⏱ **Timers** | Per-task countdown timers with start / pause |
| 📅 **Deadlines** | Deadline badges with urgency highlighting (3 days) |
| 🔔 **Reminders** | DateTime reminders with startup popup |
| ⚡ **Inbox** | One-time incoming tasks, separate from the board |
| 🗄 **Archive** | Completed tasks auto-archive with restore |
| ✈ **Telegram** | Optional bot integration for notifications |
| 💾 **Import / Export** | Full data export and import as JSON |
| 🌐 **Multilingual** | English / Russian / Ukrainian — toggle in header |
| 🎨 **Dark UI** | Terminal-inspired dark theme, no external CSS |

---

## Quick Start

**Run locally — no server needed:**

```bash
git clone https://github.com/your-username/devops-board.git
cd devops-board

open index.html        # macOS
xdg-open index.html    # Linux
start index.html       # Windows
```

**GitHub Pages:**

1. Fork this repo
2. Go to **Settings → Pages**
3. Set source: `main` branch, root `/`
4. Live at `https://your-username.github.io/devops-board/`

---

## File Structure

```
devops-board/
├── index.html      # Full application — single file
└── README.md
```

---

## Usage

### Tasks

| Action | How |
|---|---|
| Add task | Click `+` in column header or `+ Add task` at bottom |
| Edit task | Click ✏ on the card |
| Move task | Drag and drop between columns |
| Complete task | Click ✓ — moves to archive automatically |
| Delete task | Click ✕ (with confirmation) |

### Task Fields

| Field | Description |
|---|---|
| **Title** | Required |
| **Description** | Optional details |
| **Priority** | High 🔴 / Medium 🟡 / Low 🟢 — colored left border |
| **Subtasks** | Individual checkboxes + progress bar |
| **Timer** | Duration in minutes, start/pause with ▶/⏸ |
| **Deadline** | Badge turns red within 3 days |
| **Reminder** | Date + time, popup fires at that moment |
| **Group** | Which column the task belongs to |

### Columns

- **Add:** `+` button at the right edge of the board
- **Rename:** ✏ in the column header
- **Delete:** ✕ in the column header (removes all tasks inside)
- **Colors:** Blue, Orange, Green, Red, Purple, Cyan

### Inbox

One-time tasks that don't fit the regular workflow (e.g. "Fix server issue"):

- Add via **⚡ Incoming** in the header
- Mark done by clicking the task text
- Archive with `→` or delete with `✕`

### Archive

- Completed tasks move here automatically on ✓
- Expand the archive panel at the bottom
- Restore any task with ↩
- Clear all with **Clear archive**

---

## Telegram Integration

Notifications on task complete, timer expire, and reminders.

**Setup:**

1. Create a bot via [@BotFather](https://t.me/BotFather) → `/newbot`
2. Copy the **Bot Token**
3. Get your **Chat ID** from `https://api.telegram.org/bot<TOKEN>/getUpdates`
4. Open **⚙ Settings** → enter Token and Chat ID → enable toggle → **Test connection**

| Event | Message |
|---|---|
| Task completed | `✅ Task completed: <title>` |
| Timer expired | `⏱ Timer expired: <title>` |
| Reminder fired | `🔔 Reminder: <title>` |

---

## Data

All data is saved to **browser localStorage** — no server, no account, no cloud.

> ⚠️ Incognito mode or clearing browser data will erase the board. Export your data regularly.

- **Export:** Settings → Export JSON — saves `devops_board_YYYY-MM-DD.json`
- **Import:** Header → ⬆ Import → select any previously exported `.json`

---

## Customization

Single HTML file — open and edit directly.

**Default columns** — edit `S.columns` in `init()`:

```javascript
S.columns = [
  { id: uid(), title: 'Backlog', color: '#6b7280' },
  { id: uid(), title: 'In Progress', color: '#f59e0b' },
  { id: uid(), title: 'Done', color: '#10b981' }
];
```

**Color theme** — edit CSS variables:

```css
:root {
  --bg: #0a0c10;
  --accent: #00d4ff;
  --danger: #ef4444;
  --success: #10b981;
}
```

**Add a language** — extend `LANGS` object and add a button:

```javascript
de: { settings: 'Einstellungen', cancel: 'Abbrechen', ... }
```

```html
<button class="lang-btn" onclick="setLang('de')">DE</button>
```

---

## Browser Support

Chrome 90+, Firefox 88+, Safari 14+, Edge 90+, Mobile Chrome, Mobile Safari.

---

## Contributing

1. Fork the repository
2. Edit `index.html`
3. Test in at least two browsers
4. Submit a pull request

---

## License

MIT — free to use, modify, and distribute for any purpose.
