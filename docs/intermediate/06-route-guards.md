# 🟡 Intermediate Level

# 06️⃣ Route Guards in Angular – Detailed Guide

---

## ✅ Short Interview Answer

Route Guards in Angular are interfaces that control navigation to and from routes. They are used to protect routes based on conditions like authentication, authorization, or unsaved changes.

---

# 🟢 Simple Explanation

Imagine your application has:

- 🔐 Admin Dashboard
- 👤 User Profile
- 📄 Login Page

You don’t want unauthorized users to access the Admin Dashboard.

👉 Route Guards act like security checkpoints before entering a route.

---

# 🔹 Why Do We Need Route Guards?

Without Guards:

- Anyone can access protected routes
- Security issues may arise
- Poor user experience

With Guards:

- Restrict access to authenticated users
- Prevent navigation with unsaved changes
- Control role-based access
- Improve application security

---

# 🟡 Types of Route Guards

Angular provides 5 types of Route Guards:

1️⃣ CanActivate  
2️⃣ CanActivateChild  
3️⃣ CanDeactivate  
4️⃣ CanLoad  
5️⃣ CanMatch (Angular 15+)

---

# 1️⃣ CanActivate

Controls whether a route can be activated.

### Example:

```ts
import { Injectable } from "@angular/core";
import { CanActivate, Router } from "@angular/router";

@Injectable({ providedIn: "root" })
export class AuthGuard implements CanActivate {
  constructor(private router: Router) {}

  canActivate(): boolean {
    const isLoggedIn = !!localStorage.getItem("token");

    if (!isLoggedIn) {
      this.router.navigate(["/login"]);
      return false;
    }

    return true;
  }
}
```

### Apply Guard to Route:

```ts
{
  path: 'admin',
  component: AdminComponent,
  canActivate: [AuthGuard]
}
```

---

# 2️⃣ CanActivateChild

Controls access to child routes.

```ts
{
  path: 'admin',
  canActivateChild: [AuthGuard],
  children: [
    { path: 'dashboard', component: DashboardComponent }
  ]
}
```

---

# 3️⃣ CanDeactivate

Prevents navigation away from a route.

Used for:

- Unsaved form changes
- Confirmation dialogs

Example:

```ts
import { CanDeactivate } from "@angular/router";

export interface CanComponentDeactivate {
  canDeactivate: () => boolean;
}
```

Guard:

```ts
canDeactivate(component: CanComponentDeactivate): boolean {
  return component.canDeactivate();
}
```

---

# 4️⃣ CanLoad

Prevents lazy-loaded module from loading.

```ts
{
  path: 'admin',
  loadChildren: () => import('./admin/admin.module').then(m => m.AdminModule),
  canLoad: [AuthGuard]
}
```

Important for performance and security.

---

# 5️⃣ CanMatch (Angular 15+)

Replaces CanLoad in modern Angular versions.

Controls whether route should match or not.

---

# 🔥 Return Types of Guards

Guards can return:

- boolean
- UrlTree
- Observable<boolean>
- Promise<boolean>

Example using Observable:

```ts
canActivate(): Observable<boolean> {
  return this.authService.isAuthenticated$;
}
```

---

# 🧠 Real-World Example: Role-Based Access

```ts
canActivate(): boolean {
  const role = localStorage.getItem('role');
  return role === 'admin';
}
```

---

# 🚀 Best Practices

- Keep guard logic simple
- Move business logic to service
- Use Observables when async validation required
- Combine guards if needed
- Use CanMatch instead of CanLoad in Angular 15+

---

# 🧠 Interview Deep Concept

## Difference Between CanActivate and CanLoad

| Feature                 | CanActivate | CanLoad |
| ----------------------- | ----------- | ------- |
| Prevents navigation     | ✅ Yes      | ✅ Yes  |
| Prevents module loading | ❌ No       | ✅ Yes  |
| Used in lazy modules    | ⚠️ Limited  | ✅ Yes  |

---

# 🎯 What Interviewer Is Testing

- Do you understand route protection?
- Can you implement authentication guard?
- Do you know lazy loading security?
- Can you differentiate CanActivate vs CanLoad?
- Do you know return types?

---

# 🏆 Perfect Interview Answer (1–2 Minutes)

> Route Guards in Angular control navigation to routes based on conditions like authentication and authorization. Angular provides CanActivate, CanActivateChild, CanDeactivate, CanLoad, and CanMatch. Guards can return boolean, UrlTree, Observable, or Promise. They are commonly used to protect routes, prevent unauthorized access, and handle unsaved changes in forms.

---

# 💬 Common Follow-up Questions

1. What is difference between CanActivate and CanLoad?
2. When to use CanDeactivate?
3. What is CanMatch?
4. Can guards return Observable?
5. How to implement role-based access?

---

## 🔙 Navigation

[⬅️ Back to Intermediate Questions List](../../README.md)
