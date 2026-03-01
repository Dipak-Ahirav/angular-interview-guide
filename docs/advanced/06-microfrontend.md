# 🔵 Advanced Level

# 06️⃣ Micro Frontends in Angular – Enterprise Architecture Deep Dive

---

## ✅ Short Interview Answer

Micro Frontend architecture splits a large frontend application into smaller, independently deployable frontend applications. In Angular, this is commonly implemented using Module Federation, Webpack, or Single-SPA to allow multiple Angular apps to work together in a single shell.

---

# 🟢 Why Micro Frontends?

In large enterprise apps:

- Multiple teams work simultaneously
- Codebase becomes huge
- Deployment becomes risky
- Releases are tightly coupled

Micro Frontends solve this by:

- Splitting app into smaller pieces
- Independent deployment
- Team-level ownership
- Better scalability

---

# 🧠 What is Micro Frontend?

Instead of one monolithic Angular app:

👉 We build multiple small Angular apps  
👉 Each app handles a feature  
👉 A Shell app loads them dynamically

Example:

- Shell App
- Orders App
- Payments App
- Dashboard App

---

# 🔥 Micro Frontend vs Monolith

| Feature        | Monolith     | Micro Frontend   |
| -------------- | ------------ | ---------------- |
| Deployment     | Single build | Independent      |
| Team ownership | Shared       | Distributed      |
| Scalability    | Limited      | High             |
| Complexity     | Low          | High             |
| Performance    | Good         | Depends on setup |

---

# 🟡 How Micro Frontend Works in Angular

Common approaches:

1️⃣ Webpack Module Federation  
2️⃣ Single-SPA  
3️⃣ iframe-based integration  
4️⃣ Custom dynamic loading

Most modern Angular apps use:

👉 Webpack Module Federation

---

# 💻 Webpack Module Federation Concept

Module Federation allows:

- Loading remote modules at runtime
- Sharing dependencies
- Avoiding duplicate Angular versions

Architecture:

Shell → Loads Remote Apps

---

# 🟢 Basic Architecture

Shell (Host)

- Manages routing
- Loads remote modules

Remote App

- Independently built
- Exposes modules

---

# 🔥 Example Configuration (Simplified)

Remote App:

```js
exposes: {
  './Module': './src/app/feature/feature.module.ts',
}
```

Shell App:

```js
remotes: {
  "featureApp": "featureApp@http://localhost:4201/remoteEntry.js"
}
```

---

# 🧠 Shared Dependencies

Important:

```js
shared: {
  '@angular/core': { singleton: true },
  '@angular/common': { singleton: true },
}
```

Prevents loading Angular multiple times.

---

# 🚀 Real Enterprise Benefits

Micro Frontends provide:

- Independent CI/CD
- Smaller bundle sizes per app
- Parallel team development
- Technology flexibility
- Faster releases

---

# 🚨 Challenges

- Version conflicts
- Shared state complexity
- Performance tuning
- Debugging difficulty
- Infrastructure setup

---

# 🧠 Communication Between Micro Frontends

Options:

- Shared service via host
- Custom event bus
- Window events
- RxJS-based global store

Best practice:

Keep micro frontends loosely coupled.

---

# 🔥 When Should You Use Micro Frontends?

Recommended if:

- Large enterprise app
- 5+ frontend teams
- Independent release cycles
- Complex business domains

Not recommended for:

- Small or medium apps
- Single-team projects
- Simple dashboards

---

# 🟡 Performance Considerations

- Proper caching required
- Shared dependency optimization
- Lazy loading important
- Avoid duplicate Angular runtime

---

# 🎯 What Interviewer Is Testing

- Why Micro Frontends?
- How does Module Federation work?
- How to avoid Angular duplication?
- Communication strategies?
- Trade-offs vs Monolith?

---

# 🏆 Perfect Interview Answer (2 Minutes)

> Micro Frontends divide a large frontend application into smaller, independently deployable applications. In Angular, this is commonly implemented using Webpack Module Federation, where a shell application dynamically loads remote feature modules. This architecture enables independent team ownership, faster deployments, and scalability but introduces complexity in dependency management and communication. It is best suited for large enterprise applications with multiple teams.

---

# 💬 Common Follow-up Questions

1. What is Module Federation?
2. How to share dependencies?
3. Can different Angular versions coexist?
4. How do micro frontends communicate?
5. When should you avoid micro frontends?

---

## 🔙 Navigation

[⬅️ Back to Advanced Questions List](../../README.md)
