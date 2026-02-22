# 🔵 Advanced Level

# 10️⃣ Tree Shaking in Angular – Deep Technical Breakdown

---

## ✅ Short Interview Answer

Tree Shaking is a build optimization technique that removes unused code from the final JavaScript bundle. In Angular, it works during production builds by leveraging ES Modules (ESM) and static imports to eliminate dead code, reducing bundle size and improving performance.

---

# 🟢 Why Tree Shaking Is Important

Modern Angular apps use:

- Multiple libraries
- Utility functions
- Shared modules
- UI frameworks

Without tree shaking:

❌ Entire libraries get bundled  
❌ Bundle size increases  
❌ Slow load times  
❌ Poor mobile performance  

Tree shaking ensures only **used code** is included.

---

# 🧠 How Tree Shaking Works

Tree shaking works because:

1️⃣ ES Modules use static imports  
2️⃣ The compiler knows what is used  
3️⃣ Unused exports are removed  
4️⃣ Dead code is eliminated during production build  

Angular CLI uses:

- Webpack
- Terser
- Build Optimizer

---

# 🔥 Example Without Tree Shaking

```ts
import * as _ from 'lodash';
```

This imports the entire lodash library.

---

# ✅ Example With Tree Shaking

```ts
import debounce from 'lodash/debounce';
```

Only the required function is included.

---

# 🟡 Tree Shaking + Angular Production Build

Always use:

```bash
ng build --configuration production
```

Production build enables:

- AOT compilation
- Build optimizer
- Dead code elimination
- Minification
- Tree shaking

---

# 🧠 ES Modules Requirement

Tree shaking only works with:

```ts
import { something } from 'library';
```

It does NOT work well with:

```ts
require('library');
```

CommonJS reduces tree shaking effectiveness.

---

# 🔥 Side Effects & Tree Shaking

If a package has:

```json
"sideEffects": false
```

Webpack can safely remove unused exports.

If side effects exist → removal may break app.

---

# 🟢 Angular-Specific Tree Shaking Features

- ProvidedIn: 'root' services
- Standalone components
- Lazy loaded modules
- Functional providers

Example:

```ts
@Injectable({ providedIn: 'root' })
```

If service is unused → removed from bundle.

---

# 🚀 Standalone Components Improve Tree Shaking

Angular 15+:

Standalone components allow:

- More granular imports
- Reduced module dependencies
- Better code splitting

---

# 🧠 Detecting Tree Shaking Results

Run:

```bash
ng build --stats-json
```

Then analyze:

```bash
webpack-bundle-analyzer dist/stats.json
```

You can see:

- Removed modules
- Large dependencies
- Optimization impact

---

# 🔥 Tree Shaking vs Lazy Loading

| Feature | Tree Shaking | Lazy Loading |
|----------|--------------|--------------|
| Removes unused code | ✅ Yes | ❌ No |
| Splits code into chunks | ❌ No | ✅ Yes |
| Reduces initial bundle | ✅ Yes | ✅ Yes |
| Runtime loading | ❌ No | ✅ Yes |

Both should be used together.

---

# 🟡 Common Tree Shaking Problems

- Using CommonJS libraries
- Importing entire UI frameworks
- Barrel file overuse
- Including polyfills unnecessarily
- Side-effect-heavy libraries

---

# 🧠 Enterprise Best Practices

- Prefer ES Module libraries
- Avoid large monolithic imports
- Use standalone APIs
- Remove unused dependencies
- Monitor bundle size regularly

---

# 🚨 Real-World Example

Before optimization:

- 2.2MB bundle

After tree shaking + lazy loading:

- 850KB initial bundle

Improved:

- FCP
- TTI
- Lighthouse score

---

# 🎯 What Interviewer Is Testing

- What is tree shaking?
- How does Angular support it?
- Why ES modules matter?
- Difference between tree shaking and lazy loading?
- What prevents tree shaking?

---

# 🏆 Perfect Interview Answer (2 Minutes)

> Tree shaking is a build optimization technique that removes unused code from the final JavaScript bundle. Angular supports tree shaking through ES Modules, AOT compilation, and build optimization during production builds. It works best when using static imports and ES module-compatible libraries. Tree shaking reduces bundle size and improves performance but should be combined with lazy loading for maximum optimization.

---

# 💬 Common Follow-up Questions

1. Does tree shaking work in development build?
2. Why ES modules are required?
3. What breaks tree shaking?
4. Difference between tree shaking and code splitting?
5. How to verify tree shaking is working?

---

## 🔙 Navigation

⬅️ Back to Advanced Questions List
