# OpenDeck Macro Builder

A visual keyboard tool for generating [OpenDeck](https://github.com/ninjadev64/OpenDeck) **Simulate Input** macro syntax. Built for use with Elgato Stream Deck on Linux.

No dependencies. No build step. Just open the HTML file in your browser.

## The problem

OpenDeck's Simulate Input action expects a shorthand syntax like this:

```
[k(Alt,p),k(uni('s')),k(Alt,r)]
```

Writing this by hand means memorizing the format, knowing which keys are modifiers, getting the press/release order right, and looking up key names from the source. This tool does all of that for you.

## Usage

1. Download `opendeck-macro-builder.html`
2. Open it in your browser
3. Click keys in the order you want them pressed
4. Copy the generated syntax into OpenDeck's Simulate Input field

## How it works

Click keys on the visual keyboard and the tool generates the correct syntax automatically. Each selected key gets a numbered badge showing its position in the sequence.

**Modifiers** (Shift, Ctrl, Alt, Super) are detected automatically and wrapped with press/release — released in reverse order, just like real typing.

**Regular keys** use OpenDeck's default click action.

| You click | Generated syntax |
|---|---|
| E | `[k(uni('e'))]` |
| Alt → S | `[k(Alt,p),k(uni('s')),k(Alt,r)]` |
| Ctrl → Shift → T | `[k(Control,p),k(Shift,p),k(uni('t')),k(Shift,r),k(Control,r)]` |
| F5 | `[k(F5)]` |
| Ctrl → Alt → Delete | `[k(Control,p),k(Alt,p),k(Delete),k(Alt,r),k(Control,r)]` |

## Features

- Full keyboard layout with function keys, nav cluster, and numpad
- Media keys (volume, play/pause, next/prev track)
- Order tracking with numbered badges and a visual flow display
- One-click copy to clipboard
- Zero dependencies — single self-contained HTML file

## Key names

Key names match the [OpenDeck keycodes](https://github.com/ninjadev64/OpenDeck) which come from the [enigo](https://github.com/enigo-rs/enigo) Rust crate. Regular character keys use `uni('x')` syntax. Special keys use their enum names like `Return`, `Backspace`, `UpArrow`, etc.
