---
title: "ActiveSystems: Managing Groups of State Machines"
tags: ["xstate", "state-machines", "typescript", "architecture", "recursion"]
---

# ActiveSystems: Managing Groups of State Machines  

## Concept  
**ActiveSystems** are groups of state machines running together within a system. Each machine can be referenced by its **system ID**, allowing direct event sending, discovery, and subscription.

## Key Features  
- **Direct event dispatching**: Send events to any machine using its system ID.  
- **Machine discovery**: Locate any machine in the system and retrieve its current state.  
- **Global event listening**: Subscribe to events emitted by any machine in the system.  

## TypeScript Challenges  
### The Recursion Problem  
- Since all machines exist within the same system, their types become interconnected.  
- If one machine references another’s type, and vice versa, TypeScript struggles with recursion.  
- Overly complex recursive type definitions break type inference.  

### Solution: Predefined Type Interfaces  
- **Define types before creating state machines** to avoid circular dependencies.  
- Each machine should have a **separate type definition** for:  
  - **Context**: The internal data it manages.  
  - **Events**: The events it listens for.  
  - **Emitted Events**: The events it can send to other machines.  
  - **Children** (if applicable): Any nested machines.  

### Type Structure Example  

```ts
// Define the types first
interface AuthContext { user: string | null }
type AuthEvent = { type: "LOGIN"; user: string } | { type: "LOGOUT" };
type AuthEmitted = { type: "AUTH_CHANGED"; user: string | null };

// Define the machine separately, avoiding direct type recursion
const authMachine = createMachine<AuthContext, AuthEvent>({
  id: "auth",
  initial: "loggedOut",
  states: {
    loggedOut: { on: { LOGIN: { target: "loggedIn", actions: ["setUser"] } } },
    loggedIn: { on: { LOGOUT: { target: "loggedOut", actions: ["clearUser"] } } }
  }
});
```



By separating types from the machine, we prevent recursive type dependencies and keep the system maintainable.

Next Steps

[ ] Implement a registry to manage ActiveSystems efficiently.

[ ] Ensure TypeScript can infer machine interactions without causing recursion issues.

[ ] Test different strategies for handling event propagation and subscriptions.


Related Notes

[[XState Actor Systems]]

[[Type Safety in State Machines]]

[[Event-Driven Architectures]]