---

# Nemu-X-WL

Custom whitelist ruleset for **Clash Verge / Clash.Meta**.

This ruleset forces selected domains to use your proxy group (e.g. `♻️ Automatic`) instead of going `DIRECT`.

Supports automatic updates via `rule-providers`.

![maintained](https://img.shields.io/badge/maintained-by%20Nemu--x-purple)

---

## 📦 What This Is

**Nemu-X-WL** is a personal whitelist containing domains that should always use a proxy connection.

Includes domains such as:

* AI services (OpenAI, Anthropic, Mistral, etc.)
* GitHub & developer tools
* Media & streaming platforms
* Region-restricted or blocked websites

---

## ⚙️ How to Use in Clash Verge

### 1️⃣ Open Profile Settings

Go to:

```
Profiles → Your Active Profile → Edit → Extend Config
```

---

### 2️⃣ Paste This Configuration

```yaml
rule-providers:
  Nemu-X-WL:
    type: http
    behavior: classical
    url: "https://raw.githubusercontent.com/Nemu-x/privWL-clash/main/clV2_provider.yaml"
    path: ./ruleset/Nemu-X-WL.yaml
    interval: 86400

rules:
  - RULE-SET,Nemu-X-WL,♻️ Automatic
  - MATCH,DIRECT
```

---

### 3️⃣ Save & Reload

* Click **Save**
* Reload profile
* Restart Clash core if necessary

---

## 🔄 How It Works

Rule priority:

1. Domains listed in `Nemu-X-WL` → `♻️ Automatic`
2. Everything else → `DIRECT`

If you use a different proxy group, replace:

```
♻️ Automatic
```

with your group name.

Example:

```yaml
- RULE-SET,Nemu-X-WL,Proxy
```

---

## 🔁 Auto Updates

The ruleset updates automatically every 24 hours:

```
interval: 86400
```

You can change this value:

* `3600` → update every hour
* `43200` → update every 12 hours
* `86400` → update every 24 hours

---

## 📁 File Structure

```
clV2_provider.yaml  → main whitelist ruleset
```

Format example:

```yaml
payload:
  - DOMAIN-SUFFIX,example.com
  - DOMAIN-SUFFIX,github.com
```

---

## ⚠️ Important Notes

* `MATCH` rule must always be the **last rule**
* Rule names are **case-sensitive**
* Proxy group name must match exactly
* After editing, always reload profile or restart core

---

## 🚀 Customization

You can:

* Fork this repository
* Add or remove domains
* Change proxy group in Clash
* Adjust update interval

---

**Made for Clash Verge / Clash.Meta users who want simple and clean proxy control.**
