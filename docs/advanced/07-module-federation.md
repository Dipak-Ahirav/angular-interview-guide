# 🔵 Advanced Level

# 07️⃣ Webpack Module Federation in Angular – Complete Deep Dive

---

## ✅ Short Interview Answer

Module Federation is a Webpack 5 feature that enables multiple independent applications to share code and load modules dynamically at runtime. In Angular, it is commonly used to implement Micro Frontend architecture by allowing a Shell (Host) app to load Remote feature apps.

---

# 🟢 Why Module Federation?

In large enterprise Angular applications:

- Multiple teams work independently
- Features are deployed separately
- Codebase grows large
- Releases become tightly coupled

Module Federation solves this by:

- Allowing independent builds
- Loading remote modules at runtime
- Sharing dependencies safely
- Enabling micro frontend architecture

---

# 🧠 Core Concept

Instead of bundling everything together:

👉 A Host (Shell) app dynamically loads  
👉 Remote applications expose modules  

No need for rebuilding the entire system.

---

# 🟡 Basic Architecture

- Shell Application (Host)
- One or more Remote Applications
- Shared Dependencies
- Runtime Module Loading

---

# 🔥 How It Works Internally

1️⃣ Host loads remoteEntry.js  
2️⃣ Remote exposes modules  
3️⃣ Host imports exposed modules dynamically  
4️⃣ Shared libraries are reused (Angular core, common, etc.)  

---

# 💻 Remote App Configuration (Simplified)

```js
new ModuleFederationPlugin({
  name: "ordersApp",
  filename: "remoteEntry.js",
  exposes: {
    "./OrdersModule": "./src/app/orders/orders.module.ts",
  },
  shared: {
    "@angular/core": { singleton: true },
    "@angular/common": { singleton: true },
  }
});
```

---

# 💻 Host (Shell) Configuration

```js
new ModuleFederationPlugin({
  remotes: {
    "ordersApp": "ordersApp@http://localhost:4201/remoteEntry.js"
  },
  shared: {
    "@angular/core": { singleton: true },
    "@angular/common": { singleton: true },
  }
});
```

---

# 🧠 Important Concept: Shared Dependencies

If Angular is not shared properly:

❌ Multiple Angular instances load  
❌ Runtime errors occur  
❌ Dependency conflicts happen  

Correct setup:

```js
shared: {
  "@angular/core": { singleton: true, strictVersion: true },
  "@angular/common": { singleton: true, strictVersion: true },
}
```

---

# 🔥 Runtime Module Loading Example

In Host routing:

```ts
{
  path: 'orders',
  loadChildren: () =>
    loadRemoteModule({
      type: 'module',
      remoteEntry: 'http://localhost:4201/remoteEntry.js',
      exposedModule: './OrdersModule'
    }).then(m => m.OrdersModule)
}
```

---

# 🧠 Benefits of Module Federation

- Independent deployments
- Smaller builds per team
- Faster feature releases
- Shared UI libraries
- Scalable architecture

---

# 🚨 Challenges

- Version management complexity
- Shared state management issues
- Deployment orchestration
- Debugging distributed apps
- Increased configuration complexity

---

# 🟡 Module Federation vs Lazy Loading

| Feature | Lazy Loading | Module Federation |
|----------|---------------|------------------|
| Same build | ✅ Yes | ❌ No |
| Independent deployment | ❌ No | ✅ Yes |
| Micro frontend ready | ❌ No | ✅ Yes |
| Complexity | Low | High |

---

# 🧠 Enterprise Use Case

Example:

- Shell App (Main container)
- Payments App (Remote)
- Orders App (Remote)
- Analytics App (Remote)

Each deployed independently.

---

# 🚀 When Should You Use Module Federation?

Recommended for:

- Large enterprise systems
- Multi-team environments
- Independent release cycles
- Micro frontend architecture

Not recommended for:

- Small apps
- Single-team projects
- Simple dashboards

---

# 🎯 What Interviewer Is Testing

- What is Module Federation?
- Difference from Lazy Loading?
- How to share Angular dependencies?
- How runtime loading works?
- Trade-offs?

---

# 🏆 Perfect Interview Answer (2 Minutes)

> Module Federation is a Webpack 5 feature that allows independent Angular applications to share and load modules at runtime. It enables micro frontend architecture by allowing a host application to dynamically load remote feature modules. Shared dependencies like Angular core must be configured as singletons to prevent multiple framework instances. Module Federation is best suited for large enterprise applications with multiple teams and independent deployment requirements.

---

# 💬 Common Follow-up Questions

1. How do you prevent multiple Angular versions?
2. Can remotes be deployed independently?
3. Difference between Lazy Loading and Module Federation?
4. How do remotes communicate?
5. What are performance considerations?

---

## 🔙 Navigation

⬅️ Back to Advanced Questions List
