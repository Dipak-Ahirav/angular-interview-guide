# 🔵 Advanced Level

# 15️⃣ Angular CDK Overlay – Enterprise Deep Dive

---

## ✅ Short Interview Answer

Angular CDK Overlay is a low-level utility provided by Angular CDK that allows developers to create floating UI elements like modals, dialogs, tooltips, dropdowns, popovers, and context menus with full control over positioning, scrolling behavior, and backdrop handling.

---

# 🟢 What Is Angular CDK?

CDK (Component Dev Kit) provides:

- Low-level building blocks
- Accessibility utilities
- Overlay system
- Drag & Drop
- Virtual scrolling

CDK Overlay is used internally by Angular Material Dialog.

---

# 🧠 Why Use CDK Overlay?

Instead of manually handling:

- Z-index stacking
- Positioning logic
- Scroll behavior
- Backdrop handling
- Portal injection

CDK Overlay handles it cleanly and professionally.

---

# 🔥 Common Use Cases

- Custom Modal Dialog
- Dropdown Menu
- Tooltip
- Context Menu
- Floating Action Panel
- Side Panel Drawer

---

# 🟡 Core Concepts of CDK Overlay

1️⃣ Overlay  
2️⃣ OverlayRef  
3️⃣ Portal  
4️⃣ Position Strategy  
5️⃣ Scroll Strategy

---

# 🧠 Creating an Overlay

Install CDK:

```bash
npm install @angular/cdk
```

Import module:

```ts
import { OverlayModule } from "@angular/cdk/overlay";
```

---

# 🚀 Basic Overlay Example

```ts
constructor(private overlay: Overlay) {}

openOverlay() {
  const overlayRef = this.overlay.create();

  const portal = new ComponentPortal(MyPopupComponent);
  overlayRef.attach(portal);
}
```

---

# 🔥 Position Strategy

```ts
const positionStrategy = this.overlay
  .position()
  .global()
  .centerHorizontally()
  .centerVertically();

const overlayRef = this.overlay.create({
  positionStrategy,
});
```

---

# 🟢 Connected Position Strategy (Dropdown)

```ts
this.overlay
  .position()
  .flexibleConnectedTo(buttonRef)
  .withPositions([
    {
      originX: "start",
      originY: "bottom",
      overlayX: "start",
      overlayY: "top",
    },
  ]);
```

---

# 🧠 Scroll Strategy

Options:

- Noop
- Close
- Block
- Reposition

Example:

```ts
scrollStrategy: this.overlay.scrollStrategies.block();
```

---

# 🔥 Backdrop Handling

```ts
hasBackdrop: true,
backdropClass: 'dark-backdrop'
```

Close on backdrop click:

```ts
overlayRef.backdropClick().subscribe(() => overlayRef.dispose());
```

---

# 🟡 OverlayRef Lifecycle

Important methods:

- attach()
- detach()
- dispose()

Always dispose to avoid memory leaks.

---

# 🚀 CDK Overlay vs Angular Material Dialog

| Feature              | CDK Overlay | MatDialog  |
| -------------------- | ----------- | ---------- |
| Low-level control    | ✅ Yes      | ❌ Limited |
| Quick modal creation | ❌ No       | ✅ Yes     |
| Custom positioning   | ✅ Yes      | Limited    |
| Full customization   | ✅ Yes      | Partial    |

---

# 🚨 Common Mistakes

❌ Not disposing overlay  
❌ Hardcoding positions  
❌ Ignoring scroll behavior  
❌ Not handling focus

---

# 🎯 What Interviewer Is Testing

- What is CDK Overlay?
- Difference between CDK and Material?
- How positioning works?
- What is Portal?
- How to prevent memory leaks?

---

# 🏆 Perfect Interview Answer (2 Minutes)

> Angular CDK Overlay is a low-level utility that allows creating floating UI components like dialogs, dropdowns, and tooltips with full control over positioning and behavior. It provides OverlayRef, PositionStrategy, ScrollStrategy, and Portal injection. Unlike Angular Material Dialog, CDK Overlay offers complete customization and is commonly used in enterprise design systems.

---

# 💬 Common Follow-up Questions

1. What is OverlayRef?
2. How does flexibleConnectedTo work?
3. Difference between CDK and Material?
4. How to handle backdrop clicks?
5. How to prevent memory leaks?

---

## 🔙 Navigation

[⬅️ Back to Advanced Questions List](../../README.md)
