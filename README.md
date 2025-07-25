# 📊 Semi-Automated LINE Status Check-In  
### Stage 3: Make.com Automation + Webhook Processing + Row Updating

---

## 🚀 Overview
This stage documents the Make.com scenario logic that processes real-time check-in and check-out data sent from iPhone Shortcuts via Webhook. It automatically logs and updates Google Sheets entries using condition-based routing, row searching, and error handling.

This follows Stage 2, where we focused on building dynamic status selection via iOS Shortcuts.

---

## 🔧 What We Built

- **Webhook listener** (triggered by iPhone Shortcut)
- **Router with conditional filters**:
  - If `status = checkout` → add a new row
  - If `status = checkin` → search for last `checkout` row and update it
- **Google Sheets integration**:
  - Insert row for new entries
  - Search rows by sender + status
  - Update the most recent matching row with check-in data
- **Error handler** for update step (prevents failures if row not found)

---

## ⚠️ Problems We Encountered

### 1. Smart Apostrophe Breaking Router Filter
- Webhook sent `status = I’m out` (with smart quote `’`)
- Make.com filter expected `'` (straight ASCII apostrophe)
- Result: Router silently failed to match

**✅ Fix**: Replaced status values with simple lowercase keywords like `checkout` and `checkin` to eliminate formatting errors.

---

## 🧑‍💼 Who Is This For?

This automation is ideal for:
- Field teams (tour guides, maintenance, field researchers)
- Remote operations teams
- School trip or volunteer program leaders
- Emergency check-in/out workflows

---

## 💼 Benefits to Operations Teams

- Hands-free mobile logging
- Reduced admin work
- Real-time structured data
- Error-resilient updating
- Easy to scale or integrate into dashboards

---

## 📈 Future Potential

- ✅ LINE or WhatsApp message confirmations
- 📍 Escalation logic if no “checkin” received after a delay
- 🔔 Slack, Teams, or Email notifications
- 📊 Real-time dashboards (Google Sheets / Looker / Glide)
- 🛡 Offline logging and syncing support

---

## 📂 Files

- `Check-In logs.blueprint (1).json` — Final working Make.com scenario
- `README.md` — Overview and logic documentation

---

## ✅ Status

**Functional and Stable.**  
This is now a production-ready foundation for any check-in/out automation flow.

---

*Built using iPhone Shortcuts + Make.com + Google Sheets*
