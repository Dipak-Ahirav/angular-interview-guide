# 🟡 Intermediate Level

# 08️⃣ Route Resolver in Angular – Detailed Guide

---

## ✅ Short Interview Answer

A Route Resolver in Angular is used to fetch data before a route is activated. It ensures that required data is available before the component loads, improving user experience and preventing empty or loading states.

---

# 🟢 Simple Explanation

Imagine you open a User Details page.

Without Resolver:
- Page opens first
- Then API call starts
- User sees loading spinner

With Resolver:
- API call happens first
- Page opens with data ready

👉 Resolver = Fetch data before route loads.

---

# 🔹 Why Do We Need Resolver?

Without Resolver:

- UI may flash empty content
- Complex loading logic inside component
- Poor user experience

With Resolver:

- Clean component logic
- Data ready before component loads
- Better performance perception
- Centralized data fetching

---

# 🟡 How Resolver Works

1️⃣ User navigates to route  
2️⃣ Angular calls Resolver  
3️⃣ Resolver fetches data (API call)  
4️⃣ If successful → Route activates  
5️⃣ Component receives resolved data  

---

# 💻 Basic Implementation Example

## Step 1️⃣ Create Resolver

```ts
import { Injectable } from '@angular/core';
import { Resolve } from '@angular/router';
import { Observable } from 'rxjs';
import { UserService } from './user.service';

@Injectable({ providedIn: 'root' })
export class UserResolver implements Resolve<any> {

  constructor(private userService: UserService) {}

  resolve(): Observable<any> {
    return this.userService.getUsers();
  }
}
```

---

## Step 2️⃣ Add Resolver to Route

```ts
{
  path: 'users',
  component: UsersComponent,
  resolve: { users: UserResolver }
}
```

---

## Step 3️⃣ Access Resolved Data in Component

```ts
import { ActivatedRoute } from '@angular/router';

constructor(private route: ActivatedRoute) {}

ngOnInit() {
  const users = this.route.snapshot.data['users'];
  console.log(users);
}
```

---

# 🔥 Return Types of Resolver

Resolver can return:

- Observable
- Promise
- Direct value

Most common: Observable

---

# 🧠 Real-World Example

Example: Product Details Page

```ts
{
  path: 'product/:id',
  component: ProductComponent,
  resolve: { product: ProductResolver }
}
```

Now component always loads with product data ready.

---

# 🚀 Resolver vs Guard

| Feature | Resolver | Guard |
|----------|----------|--------|
| Fetch data before route | ✅ Yes | ❌ No |
| Block navigation | ❌ No (unless error) | ✅ Yes |
| Used for authentication | ❌ No | ✅ Yes |
| Used for data loading | ✅ Yes | ❌ No |

---

# 🔥 Error Handling in Resolver

If API fails:

```ts
resolve(): Observable<any> {
  return this.userService.getUsers().pipe(
    catchError(() => {
      return EMPTY;
    })
  );
}
```

Or redirect inside resolver.

---

# 🧠 Advanced Concept

Resolvers run before route activation.

Multiple resolvers can be used:

```ts
resolve: {
  users: UserResolver,
  settings: SettingsResolver
}
```

---

# 🚀 Best Practices

- Keep resolver logic simple
- Move heavy logic to service
- Handle errors properly
- Use for important pre-required data
- Avoid overusing resolver unnecessarily

---

# 🎯 What Interviewer Is Testing

- Do you understand route lifecycle?
- Can you fetch data before component loads?
- Difference between guard and resolver?
- Can you handle errors properly?

---

# 🏆 Perfect Interview Answer (1–2 Minutes)

> A Route Resolver in Angular is used to fetch required data before activating a route. It ensures that the component loads only after the necessary data is available, improving user experience and simplifying component logic. Resolvers return Observables or Promises and are configured in route definitions using the resolve property.

---

# 💬 Common Follow-up Questions

1. Difference between Resolver and Guard?
2. Can Resolver block navigation?
3. How to handle resolver errors?
4. When should you avoid using Resolver?
5. Can we use multiple resolvers?

---

## 🔙 Navigation

⬅️ Back to Intermediate Questions List
