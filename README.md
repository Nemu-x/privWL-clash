# Nemu-X-WL-clash

Custom whitelist ruleset for **Clash Verge / Clash.Meta**.

This ruleset forces selected domains to use your proxy group (e.g. `♻️ Automatic`) instead of going `DIRECT`.

Supports automatic updates via `rule-providers`.

![maintained](https://img.shields.io/badge/maintained-yes-purple)
![platform](https://img.shields.io/badge/platform-Clash_Meta-blue)
![format](https://img.shields.io/badge/type-rule--provider-green)
![license](https://img.shields.io/badge/license-MIT-lightgrey)

---

## 📦 What This Is

**Nemu-X-WL** is a curated whitelist of domains that should always use a proxy connection.

Includes:

* AI services (OpenAI, Anthropic, Mistral, etc.)
* GitHub & developer tools
* Media & streaming platforms
* Region-restricted websites

---

## ⚙️ Usage

### 1️⃣ Open Config

```
Profiles → Your Profile → Edit → Extend Config
```

---

### 2️⃣ Choose Your Setup

You can use:

* `Nemu-X-WL` → general whitelist
* `Nemu-X-TG` → Telegram IP rules
* or both together

---

## 🧩 Whitelist Only

```yaml
rule-providers:
  Nemu-X-WL:
    type: http
    behavior: classical
    url: "https://raw.githubusercontent.com/Nemu-x/privWL-clash/main/clV2_provider.yaml"
    path: ./ruleset/Nemu-X-WL.yaml
    interval: 86400

rules:
  - RULE-SET,Nemu-X-WL,<PROXY_GROUP>
  - MATCH,DIRECT
```

---

## 📡 Telegram + Whitelist

```yaml
rule-providers:
  Nemu-X-WL:
    type: http
    behavior: classical
    url: "https://raw.githubusercontent.com/Nemu-x/privWL-clash/main/clV2_provider.yaml"
    path: ./ruleset/Nemu-X-WL.yaml
    interval: 86400

  Nemu-X-TG:
    type: http
    behavior: classical
    url: "https://raw.githubusercontent.com/Nemu-x/privWL-clash/main/tgprx.yaml"
    path: ./ruleset/Nemu-X-TG.yaml
    interval: 86400

rules:
  - RULE-SET,Nemu-X-TG,<PROXY_GROUP>
  - RULE-SET,Nemu-X-WL,<PROXY_GROUP>
  - MATCH,DIRECT
```

---

## 🎯 Proxy Group

Replace:

```
<PROXY_GROUP>
```

With your actual group name:

| Panel      | Example      |
| ---------- | ------------ |
| Marzban    | ♻️ Automatic |
| Pasarguard | ⚡️ Fastest   |

Example:

```yaml
- RULE-SET,Nemu-X-WL,♻️ Automatic
```

---

## 🔄 Auto Updates

```yaml
interval: 86400
```

| Value | Meaning  |
| ----- | -------- |
| 3600  | 1 hour   |
| 43200 | 12 hours |
| 86400 | 24 hours |

---

## 📁 Files

```
clV2_provider.yaml  → main whitelist
tgprx.yaml          → Telegram IP rules (optional)
```

---

## ⚠️ Notes

* `MATCH` must be **last**
* Rule names are **case-sensitive**
* Proxy group must match exactly
* Reload config after changes

---

## 🚀 Customization

You can:

* Fork this repo
* Modify domains
* Change proxy group
* Adjust update interval

---

## 📌 Disclaimer

This repository provides only routing rules.

It does **not** include proxy servers or bypass mechanisms.
