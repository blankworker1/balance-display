# BALANCE

A live Bitcoin Lightning exhibition system. Visitors exchange coins for satoshis at a physical ATM. The satoshis can be tipped to any of 21 artworks in the space. Four HTML files run locally on an Android display screen, requiring no server or internet infrastructure beyond the Blink Lightning API.

---

## Files

### `balance-rotator.html`
The main entry point. Opens this file in Chrome on the display device. Cycles through the three displays below in sequence — Hub, ATM Dashboard, Balance — with a smooth horizontal slide transition. Duration per display is configurable. All three displays load simultaneously in the background so each is live when it slides into view.

### `hub-display.html`
A real-time participation map rendered on a 1080×1920 canvas. A central hub dot represents the ATM. Twenty-one artwork dots orbit it in a ring, one per artwork, pulsing amber when a tip is received. Visitor dots accumulate in a swarm around the hub as participants withdraw sats, with each Lightning address briefly displayed at the bottom of the screen. A running participant count is shown. Polls the ATM wallet for outgoing transactions to detect new visitors.

### `atm-dashboard.html`
Mounted above the coin-exchange ATM. Displays the live SAT balance of the ATM wallet as a full-screen fill gauge — a coloured layer rising from the bottom of the screen representing the percentage of the starting balance remaining. Colour shifts from deep teal-green when full through amber to dusky red as sats are depleted. Polls the Blink API every 30 seconds.

### `balance-display.html`
A tip acknowledgement display. Rests on a white BALANCE splash screen between events. When any of the 21 artwork wallets receives a tip, the screen crossfades to show the SAT amount, artwork name, and memo if one was included, before fading back to the splash. Tips queue if they arrive in quick succession. Polls all 21 artwork wallets simultaneously.

---

## Setup

See `BALANCE-setup-guide.md` for full configuration instructions.

PIN for all screens: **1928**

All four files must be in the same folder on the device. Open `balance-rotator.html` in Chrome via `file:///sdcard/Download/balance-rotator.html` or equivalent path.

---

## Dependencies

- [Blink](https://blink.sv) Lightning wallet API
- [Nunito](https://fonts.google.com/specimen/Nunito) via Google Fonts
- No frameworks, no build step, no server required
