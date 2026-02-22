# 🟡 Intermediate Level

# 19️⃣ Global Error Handling in Angular – Detailed Guide

---

## ✅ Short Interview Answer

Global Error Handling in Angular is implemented using a custom ErrorHandler class. It allows us to catch and handle application-wide errors in a centralized place instead of handling them in every component.

---

# 🟢 Simple Explanation

Normally, if an error occurs in a component:

```ts
throw new Error("Something went wrong");
```

The app may crash or show a console error.

Instead of handling errors everywhere,

👉 We create one global error handler that captures all errors in the app.

---

# 🔥 Why Do We Need Global Error Handling?

Without global handling:

- Duplicate try/catch everywhere
- Hard to maintain
- No centralized logging
- Difficult production monitoring

With global handling:

- Centralized error logging
- Send errors to server
- Show user-friendly messages
- Production monitoring ready

---

# 🟡 How Angular Handles Errors Internally

Angular provides:

```ts
ErrorHandler
```

We can override it with our own implementation.

---

# 💻 Step 1: Create Custom Error Handler

```ts
import { ErrorHandler, Injectable } from '@angular/core';

@Injectable()
export class GlobalErrorHandler implements ErrorHandler {

  handleError(error: any): void {
    console.error("Global Error Caught:", error);

    // Example: Send error to server
    // this.http.post('/log-error', error).subscribe();

    alert("Something went wrong. Please try again.");
  }
}
```

---

# 💻 Step 2: Register It in App Module

```ts
providers: [
  {
    provide: ErrorHandler,
    useClass: GlobalErrorHandler
  }
]
```

Now Angular uses our handler globally.

---

# 🔥 What Errors Does It Catch?

- Template errors
- Component errors
- Lifecycle hook errors
- Runtime exceptions
- Change detection errors

---

# 🧠 Real-World Production Example

In enterprise apps:

Instead of console.log:

```ts
handleError(error: any) {
  this.loggingService.sendToServer({
    message: error.message,
    stack: error.stack,
    url: window.location.href
  });
}
```

This helps in monitoring tools like:

- Sentry
- Datadog
- New Relic

---

# 🚀 Global Error Handling + HTTP Errors

Global ErrorHandler does NOT automatically catch HTTP errors.

For HTTP errors:

👉 Use HTTP Interceptor.

Example:

```ts
catchError(error => {
  if (error.status === 401) {
    // Redirect to login
  }
  return throwError(() => error);
});
```

---

# 🟡 Difference: ErrorHandler vs HTTP Interceptor

| Feature | ErrorHandler | HTTP Interceptor |
|----------|--------------|-----------------|
| Handles runtime errors | ✅ Yes | ❌ No |
| Handles HTTP errors | ❌ No | ✅ Yes |
| Global logging | ✅ Yes | ⚠️ Limited |
| Centralized handling | ✅ Yes | ✅ Yes |

---

# 🧠 Advanced Concept: Zone.js

Angular uses Zone.js to detect async errors.

Global ErrorHandler captures errors triggered inside Angular zone.

---

# 🚨 Common Mistakes

- Forgetting to register custom ErrorHandler
- Showing raw error message to users
- Handling HTTP errors only in ErrorHandler
- Not logging errors in production

---

# 🎯 What Interviewer Is Testing

- Do you know Angular provides ErrorHandler?
- Can you implement custom global error handling?
- Difference between ErrorHandler and Interceptor?
- Production error monitoring strategy?

---

# 🏆 Perfect Interview Answer (2 Minutes)

> Angular provides a built-in ErrorHandler class that can be overridden to implement global error handling. By creating a custom class that implements ErrorHandler, we can catch and log application-wide runtime errors in a centralized place. This improves maintainability, allows production monitoring, and ensures better user experience. HTTP errors are usually handled using HTTP Interceptors.

---

# 💬 Common Follow-up Questions

1. Does ErrorHandler catch HTTP errors?
2. How to log errors in production?
3. Can we show custom UI from ErrorHandler?
4. What is difference between try/catch and ErrorHandler?
5. Does it work for async errors?

---

## 🔙 Navigation

⬅️ Back to Intermediate Questions List
