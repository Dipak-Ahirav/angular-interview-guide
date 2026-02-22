# 🔵 Advanced Level

# 04️⃣ Angular SSR (Server-Side Rendering) – Complete Deep Dive

---

## ✅ Short Interview Answer

Angular SSR (Server-Side Rendering) allows Angular applications to render HTML on the server instead of the browser. This improves SEO, initial load performance, and perceived rendering speed. Angular Universal is the framework used to enable SSR in Angular applications.

---

# 🟢 Why Do We Need SSR?

Normally, Angular apps are:

👉 Client-Side Rendered (CSR)

Flow:

1. Browser loads empty HTML
2. JavaScript bundle downloads
3. Angular bootstraps
4. UI renders

Problems:

- Slow first paint
- Poor SEO
- Blank screen during loading

---

# 🔥 What SSR Solves

With SSR:

1. Server renders full HTML
2. Browser receives pre-rendered content
3. Angular hydrates on client
4. App becomes interactive

Benefits:

- Faster First Contentful Paint (FCP)
- Better SEO
- Better performance for slow networks
- Social media preview support

---

# 🧠 What is Angular Universal?

Angular Universal is Angular’s official SSR solution.

It enables:

- Server rendering
- Pre-rendering (Static generation)
- Hybrid rendering

---

# 🟡 CSR vs SSR Comparison

| Feature | CSR | SSR |
|----------|------|------|
| Initial load speed | Slower | Faster |
| SEO | Poor | Excellent |
| First paint | Delayed | Immediate |
| Server load | Low | Higher |
| Complexity | Simple | More complex |

---

# 💻 How to Enable SSR

Angular 17+:

```bash
ng add @angular/ssr
```

This:

- Adds server.ts
- Adds main.server.ts
- Configures build
- Updates angular.json

---

# 🔥 How SSR Works Internally

Flow:

1. User requests page
2. Node.js server runs Angular app
3. Server generates HTML
4. HTML sent to browser
5. Angular hydrates on client

---

# 🟢 What is Hydration?

Hydration means:

- Angular reuses server-rendered HTML
- Attaches event listeners
- Makes app interactive

Without hydration → re-render happens.

With hydration → smoother UX.

---

# 🧠 Types of Rendering in Angular

1️⃣ Client-Side Rendering (CSR)  
2️⃣ Server-Side Rendering (SSR)  
3️⃣ Static Site Generation (SSG / Pre-render)  
4️⃣ Hybrid Rendering  

---

# 🔥 Static Site Generation (SSG)

Pre-renders pages at build time.

Best for:

- Blogs
- Marketing sites
- Documentation

Command:

```bash
ng run app:prerender
```

---

# 🚀 SSR + API Calls

On server:

- API calls execute on server
- HTML includes data
- No loading spinner needed

But careful:

- Avoid browser-only APIs (window, document)

---

# 🧠 Platform Detection

Check if code runs on server:

```ts
import { isPlatformBrowser } from '@angular/common';

constructor(@Inject(PLATFORM_ID) private platformId: Object) {}

if (isPlatformBrowser(this.platformId)) {
  console.log('Running in browser');
}
```

---

# 🔥 Common SSR Issues

- Using window or document directly
- Third-party libraries depending on DOM
- Memory leaks on server
- Incorrect hydration

---

# 🧠 When Should You Use SSR?

Use SSR if:

- SEO is important
- Public-facing app
- Marketing website
- E-commerce site
- Blog

Not required if:

- Internal admin dashboard
- Auth-only enterprise tool

---

# 🚨 Performance Considerations

SSR increases:

- Server CPU usage
- Infrastructure complexity

Must handle:

- Caching
- CDN
- Load balancing

---

# 🎯 What Interviewer Is Testing

- Difference between CSR and SSR?
- What is Angular Universal?
- What is hydration?
- When should SSR be used?
- Performance trade-offs?

---

# 🏆 Perfect Interview Answer (2 Minutes)

> Angular SSR allows rendering Angular applications on the server before sending HTML to the browser. This improves SEO, first paint performance, and user experience. Angular Universal enables SSR by running Angular on a Node.js server. After the HTML is delivered, Angular hydrates the page on the client to make it interactive. SSR is ideal for public-facing applications like blogs and e-commerce platforms but may not be necessary for internal tools.

---

# 💬 Common Follow-up Questions

1. What is hydration?
2. Does SSR improve performance?
3. What are SSR drawbacks?
4. Difference between SSR and SSG?
5. Is Angular Universal production-ready?

---

## 🔙 Navigation

⬅️ Back to Advanced Questions List
