# 🟡 Intermediate Level

# 14️⃣ HTTP Interceptors in Angular – Detailed Guide

---

## ✅ Short Interview Answer

HTTP Interceptors in Angular are services that intercept and modify HTTP requests and responses globally. They are commonly used for adding authentication tokens, handling errors, logging, and transforming responses.

---

# 🟢 Simple Explanation

Imagine every HTTP request in your app passes through a security gate 🚪

Before going to the server:
- Add JWT token
- Add headers
- Log request

After receiving response:
- Handle errors
- Transform data
- Show loader

👉 Interceptor = Middleware for HTTP requests & responses.

---

# 🔹 Why Do We Need Interceptors?

Without Interceptors:

- Repeating token logic in every API call
- Repeating error handling everywhere
- Messy and duplicated code

With Interceptors:

- Centralized logic
- Clean services
- Better maintainability
- Enterprise-ready architecture

---

# 🟡 How Interceptors Work

Flow:

Component → HttpClient → Interceptor → Server  
Server → Interceptor → Component

---

# 💻 Basic Interceptor Example

## Step 1️⃣ Create Interceptor

```ts
import { Injectable } from '@angular/core';
import { HttpEvent, HttpHandler, HttpInterceptor, HttpRequest } from '@angular/common/http';
import { Observable } from 'rxjs';

@Injectable()
export class AuthInterceptor implements HttpInterceptor {

  intercept(req: HttpRequest<any>, next: HttpHandler): Observable<HttpEvent<any>> {

    const token = localStorage.getItem('token');

    const clonedReq = req.clone({
      setHeaders: {
        Authorization: `Bearer ${token}`
      }
    });

    return next.handle(clonedReq);
  }
}
```

---

## Step 2️⃣ Register Interceptor

```ts
providers: [
  {
    provide: HTTP_INTERCEPTORS,
    useClass: AuthInterceptor,
    multi: true
  }
]
```

---

# 🔥 Handling Errors in Interceptor

```ts
import { catchError } from 'rxjs/operators';
import { throwError } from 'rxjs';

intercept(req: HttpRequest<any>, next: HttpHandler) {
  return next.handle(req).pipe(
    catchError(error => {
      console.error("Error occurred:", error);
      return throwError(() => error);
    })
  );
}
```

---

# 🔥 Multiple Interceptors

Angular supports multiple interceptors.

Execution order:
- Request → Top to Bottom
- Response → Bottom to Top

Example:

```ts
providers: [
  { provide: HTTP_INTERCEPTORS, useClass: AuthInterceptor, multi: true },
  { provide: HTTP_INTERCEPTORS, useClass: LoggingInterceptor, multi: true }
]
```

---

# 🧠 Common Use Cases

- JWT Authentication
- Global Error Handling
- Loader / Spinner Handling
- Request Logging
- Response Transformation
- API Retry Logic

---

# 🚀 Loader Interceptor Example (Concept)

Before request:
- Show spinner

After response:
- Hide spinner

---

# 🔥 Cloning Requests

Important:

HttpRequest is immutable.

So we must use:

```ts
req.clone()
```

Direct modification is not allowed.

---

# 🧠 Advanced Concept: Conditional Interception

Skip some URLs:

```ts
if (req.url.includes('public')) {
  return next.handle(req);
}
```

---

# 🚀 Interceptor vs Service Difference

| Feature | Service | Interceptor |
|----------|----------|--------------|
| Used per API | Yes | Global |
| Modify request globally | ❌ No | ✅ Yes |
| Best for token handling | ❌ No | ✅ Yes |
| Centralized error handling | ❌ No | ✅ Yes |

---

# ❌ Common Mistakes

- Forgetting multi: true
- Not cloning request
- Infinite request loops
- Handling business logic inside interceptor

---

# 🎯 What Interviewer Is Testing

- Do you understand HttpClient pipeline?
- Can you add JWT token globally?
- Do you know immutability of HttpRequest?
- Can you explain execution order?
- Difference between interceptor and service?

---

# 🏆 Perfect Interview Answer (1–2 Minutes)

> HTTP Interceptors in Angular allow us to intercept and modify HTTP requests and responses globally. They are commonly used for attaching authentication tokens, handling global errors, logging, and showing loaders. Interceptors work as middleware and must clone the request since HttpRequest objects are immutable. Multiple interceptors can be chained and execute in order.

---

# 💬 Common Follow-up Questions

1. Why do we need multi: true?
2. What happens if we don't clone request?
3. How to skip certain requests?
4. Execution order of multiple interceptors?
5. Can interceptors modify responses?

---

## 🔙 Navigation

⬅️ Back to Intermediate Questions List
