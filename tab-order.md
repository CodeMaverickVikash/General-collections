# DOM Tab Order & Accessibility

## What is Tab Order?
Tab order determines the sequence in which interactive UI elements receive keyboard focus when the user presses the <kbd>Tab</kbd> key.

---

## Focusable Elements
- **Implicitly Focusable:** Native interactive elements (e.g., `<input>`, `<select>`, `<button>`, `<textarea>`, `<a href="...">`) are included in the natural tab order automatically.
- **Non-Focusable by Default:** Structural containers and text elements (e.g., `<div>`, `<span>`, `<p>`) do not participate in tab navigation unless explicitly given a `tabindex` attribute.

---

## How Tab Order is Determined
- Natural tab order follows the actionable elements in the **DOM tree order**.
- Visual layout (CSS Flexbox, Grid, absolute positioning) does **not** change the DOM focus order.

---

## Best Practices for Resolving Tab Order Issues
- Instead of using positive `tabindex` attributes (e.g., `tabindex="2"`), rearrange and sort the underlying DOM structure to match the intended visual and logical flow.
- Use `tabindex="0"` to make a custom element focusable in its natural position.
- Use `tabindex="-1"` to make an element focusable via JavaScript (`.focus()`) without placing it into keyboard tab navigation.
