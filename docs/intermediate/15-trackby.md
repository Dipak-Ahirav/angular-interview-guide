# 🟡 Intermediate Level

# 15️⃣ trackBy in Angular – Detailed Guide

---

## ✅ Short Interview Answer

trackBy is a function used with *ngFor to improve performance by helping Angular identify which items have changed, added, or removed in a list. It prevents unnecessary DOM re-rendering.

---

# 🟢 Simple Explanation

Imagine you have a list of 100 users.

If one user changes, Angular by default may re-render the entire list.

That is inefficient.

👉 trackBy tells Angular:
“Use this unique ID to track each item.”

So Angular updates only the changed item instead of the whole list.

---

# 🔹 Why Do We Need trackBy?

Without trackBy:

- Angular uses object reference comparison
- Entire list may re-render
- Poor performance in large lists

With trackBy:

- Angular tracks items by unique ID
- Only changed elements re-render
- Better performance

---

# 🟡 Default Behavior of *ngFor

```html
<div *ngFor="let user of users">
  {{ user.name }}
</div>
```

Angular compares object references.

If array changes, Angular may recreate DOM elements.

---

# 🔥 Using trackBy

```html
<div *ngFor="let user of users; trackBy: trackByUserId">
  {{ user.name }}
</div>
```

---

# 💻 trackBy Function Example

```ts
trackByUserId(index: number, user: any): number {
  return user.id;
}
```

Now Angular uses user.id to track elements.

---

# 🔥 Real-World Scenario

Suppose API returns updated array:

Before:

```ts
[{ id: 1, name: "A" }, { id: 2, name: "B" }]
```

After:

```ts
[{ id: 1, name: "A Updated" }, { id: 2, name: "B" }]
```

Without trackBy:
- Both rows may re-render.

With trackBy:
- Only row with id 1 updates.

---

# 🧠 Performance Comparison

| Feature | Without trackBy | With trackBy |
|----------|-----------------|--------------|
| DOM recreation | High | Low |
| Performance in large lists | Poor | Optimized |
| Required unique identifier | ❌ No | ✅ Yes |

---

# 🚀 When Should You Use trackBy?

- Large lists
- Frequently updating data
- Real-time dashboards
- Tables with pagination
- Infinite scroll

---

# 🔥 trackBy with Immutable Data

When using OnPush strategy and immutability:

```ts
this.users = [...updatedUsers];
```

trackBy ensures minimal DOM updates.

---

# 🧠 Advanced Interview Concept

trackBy does NOT:

- Prevent change detection
- Improve logic performance

It only reduces DOM manipulation.

---

# 🚀 Example with Index (Not Recommended for Dynamic Lists)

```ts
trackByIndex(index: number): number {
  return index;
}
```

Using index works only when list order does not change.

Better to use unique ID.

---

# ❌ Common Mistakes

- Returning index in dynamic list
- Not using trackBy in large lists
- Using non-unique value
- Thinking trackBy prevents change detection

---

# 🎯 What Interviewer Is Testing

- Do you understand Angular DOM rendering?
- Do you know difference between reference and identity?
- When to use trackBy?
- Does trackBy improve change detection?
- How does it work with OnPush?

---

# 🏆 Perfect Interview Answer (1–2 Minutes)

> trackBy is used with *ngFor to improve performance by uniquely identifying list items using a custom function. It prevents unnecessary DOM re-rendering when data changes. Instead of recreating the entire list, Angular updates only the changed elements. It is especially useful in large or frequently updated lists.

---

# 💬 Common Follow-up Questions

1. Does trackBy stop change detection?
2. Can we use index in trackBy?
3. How does trackBy work with OnPush?
4. Why is unique ID important?
5. Is trackBy required in small lists?

---

## 🔙 Navigation

⬅️ Back to Intermediate Questions List
