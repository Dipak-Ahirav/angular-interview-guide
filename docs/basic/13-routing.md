# 1️⃣3️⃣ What is Routing in Angular?

---

## ✅ Short Interview Answer

Routing in Angular is a mechanism that enables navigation between different views (components) in a Single Page Application (SPA) without reloading the entire page.

---

# 🟢 Simple Explanation (For Freshers)

Imagine a website with multiple pages:

- Home
- About
- Contact
- Dashboard

In traditional websites:
Each click reloads the entire page.

In Angular:
The page loads once, and only the view changes dynamically.

👉 Routing allows switching between components without full page reload.

---

# 🔹 Why Do We Need Routing?

Without routing:
- No navigation between pages.
- Everything would be in a single component.
- Application becomes unmanageable.

With routing:
- Clean navigation
- Better user experience
- Bookmarkable URLs
- Modular application structure

---

# 🟡 Technical Explanation (For Experienced Developers)

Angular Router:

- Maps URL paths to components
- Enables lazy loading
- Supports route guards
- Handles navigation events
- Works with browser history API

Routing is configured using `RouterModule`.

---

# 🔥 Basic Routing Setup

## Step 1: Define Routes

```ts
import { NgModule } from '@angular/core';
import { RouterModule, Routes } from '@angular/router';
import { HomeComponent } from './home/home.component';
import { AboutComponent } from './about/about.component';

const routes: Routes = [
  { path: '', component: HomeComponent },
  { path: 'about', component: AboutComponent }
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule {}
```

---

## Step 2: Add Router Outlet

```html
<router-outlet></router-outlet>
```

This is where routed components are displayed.

---

## Step 3: Navigation Links

```html
<a routerLink="/">Home</a>
<a routerLink="/about">About</a>
```

---

# 🧠 Important Routing Concepts

## 🔹 routerLink vs href

- `routerLink` → Angular navigation (no page reload)
- `href` → Full page reload

---

## 🔹 Route Parameters

Used to pass dynamic values.

```ts
{ path: 'user/:id', component: UserComponent }
```

Access parameter:

```ts
this.route.snapshot.paramMap.get('id');
```

---

## 🔹 Lazy Loading (Performance Optimization)

Instead of loading all modules at once:

```ts
{
  path: 'admin',
  loadChildren: () =>
    import('./admin/admin.module').then(m => m.AdminModule)
}
```

Improves initial load performance.

---

## 🔹 Route Guards

Used to protect routes.

Common guards:

- CanActivate
- CanDeactivate
- CanLoad
- Resolve

Example:

```ts
canActivate(): boolean {
  return this.authService.isLoggedIn();
}
```

---

# 💻 Practical Example

Component navigation:

```ts
constructor(private router: Router) {}

goToDashboard() {
  this.router.navigate(['/dashboard']);
}
```

---

# 🚀 Advanced Interview Concept

## 🔹 Child Routes

```ts
{
  path: 'dashboard',
  component: DashboardComponent,
  children: [
    { path: 'stats', component: StatsComponent }
  ]
}
```

---

## 🔹 Wildcard Route

```ts
{ path: '**', component: NotFoundComponent }
```

Used for 404 pages.

---

# 🎯 What Interviewer Is Testing

- Do you understand SPA navigation?
- Can you configure routes?
- Do you know lazy loading?
- Do you understand route guards?
- Can you explain router-outlet?

---

# 🏆 Perfect Interview Answer (1 Minute Version)

> Routing in Angular enables navigation between different components in a Single Page Application without reloading the page. It uses RouterModule to map URL paths to components and supports features like route parameters, lazy loading, and route guards for secure and optimized navigation.

---

# 💬 Common Follow-up Questions

1. What is router-outlet?
2. Difference between forRoot and forChild?
3. What is lazy loading?
4. What are route guards?
5. How do you pass data between routes?

---

## 🔙 Navigation

⬅️ Back to Basic Questions List
