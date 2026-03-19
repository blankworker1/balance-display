# BALANCE — Display Setup Guide

PIN for all screens: **1928**

---

## 1. Rotator (`balance-rotator.html`)

Open this file first. It will immediately prompt for PIN.

**How to open settings:** Single tap — top-right corner of the screen.

| Field | What to enter |
|---|---|
| Hub Display URL | `hub-display.html` |
| ATM Dashboard URL | `atm-dashboard.html` |
| Balance Display URL | `balance-display.html` |
| Hub duration | Time in seconds to show Hub before sliding |
| ATM Dashboard duration | Time in seconds to show ATM before sliding |
| Balance duration | Time in seconds to show Balance before sliding |

The URL fields just need the filenames — no path needed as long as all four files are in the same folder. Default duration is 30 seconds each. Tap **Save + Start** and the rotation begins immediately.

---

## 2. ATM Dashboard (`atm-dashboard.html`)

Monitors the ATM's Bitcoin wallet and displays the live SAT balance as a fill gauge.

**How to open settings:** Single tap — the yellow coin logo, top-left.

| Field | What to enter |
|---|---|
| Blink API Key | The API key for the ATM's Blink wallet account |
| Starting Balance (sats) | The SAT balance the ATM starts with — this sets the 100% full mark on the gauge |

The starting balance determines the visual. If the ATM starts with 500,000 sats, enter `500000`. As sats are dispensed, the fill level drops proportionally. Tap **Save** and the live balance will appear immediately.

---

## 3. Hub Display (`hub-display.html`)

Shows the participation map — artwork ring, visitor swarm, and Lightning address readout.

**How to open settings:** Single tap — the BALANCE box, bottom-left.

| Field | What to enter |
|---|---|
| ATM Wallet ID | The wallet ID of the ATM's Blink wallet |
| ATM API Key | The API key for the ATM's Blink wallet account |
| Poll Interval (seconds) | How often to check for new transactions — default 10, minimum 5 |

The wallet ID and API key are used to watch for outgoing transactions from the ATM — each withdrawal represents a visitor receiving sats, which triggers a new dot on the participation map. The **Clear Session** button resets all visitor dots and the participant count back to zero — useful at the start of each day.

---

## 4. Balance Display (`balance-display.html`)

Shows the tip acknowledgement — crossfades between the BALANCE splash and live tip details whenever a visitor tips an artwork.

**How to open settings:** Single tap — the *Tip the Art* text at the bottom of the splash screen.

| Field | What to enter |
|---|---|
| Artwork Config | A JSON array containing the name, API key, and wallet ID for each of the 21 artworks |
| Poll Interval (seconds) | How often to check for new tips — default 10, minimum 5 |

The artwork config is the most involved setup step. It must be a valid JSON array in this format:

```json
[
  { "name": "Open Secret 1", "apiKey": "...", "walletId": "..." },
  { "name": "Open Secret 2", "apiKey": "...", "walletId": "..." }
]
```

One object per artwork, 21 total. Use the **Validate** button to check the JSON is correctly formatted before saving. If there are errors it will tell you exactly what is wrong. Tap **Save** once validated — the display will confirm it is saved and prompt you to reload.

---

## What you need before setup

| Item | Used in |
|---|---|
| ATM Blink API key | ATM Dashboard + Hub Display |
| ATM Blink wallet ID | Hub Display |
| ATM starting SAT balance | ATM Dashboard |
| API key for each of 21 artwork wallets | Balance Display |
| Wallet ID for each of 21 artwork wallets | Balance Display |
