---
{"dg-publish":true,"permalink":"/angular-guards-implemented-with-api/","tags":["guards"]}
---

# Introduction

## What is it?

This is a code implemented to use a guard to manage two or more kind of user session

## Kind of guards

There are some types of guards that can be used to an specific purpose in the navigation.

1. `CanActivate`: This one controls if a route can be activated (or visited).

```ts
import { inject } from '@angular/core';
import { Router } from '@angular/router';
import { AuthService } from './auth.service';

export const authGuard = () => {
  const authService = inject(AuthService);
  const router = inject(Router);

  if (authService.isLoggedIn()) {
    return true;
  }
  
  router.navigate(['/login']);
  return false;
};
```

2. `CanDeactivate`: Controls if the user can exit from a route. (Useful to prevent losing data).

```ts
export interface CanComponentDeactivate {
  canDeactivate: () => boolean | Observable<boolean>;
}

export const unsavedChangesGuard = (component: CanComponentDeactivate) => {
  return component.canDeactivate ? 
    component.canDeactivate() : 
    true;
};
```

3. `CanActivateChild`: This protects child routes:

```ts
export const adminGuard = () => {
  const authService = inject(AuthService);
  return authService.hasAdminRole();
};
```

4. `Resolve`: Pre-charges data before to activate the route

```ts
export const userResolver = (route: ActivatedRouteSnapshot) => {
  const userService = inject(UserService);
  return userService.getUser(route.params['id']);
};
```

5. `CanMatch`: It decides if a route must matching in router (useful for conditional lazy loading).

# How to implement guards?

## Option 1

This is the modern form to implement guards from Angular 15+:

```ts
// auth.guard.ts
import { inject } from '@angular/core';
import { Router, CanActivateFn } from '@angular/router';

export const authGuard: CanActivateFn = (route, state) => {
  const authService = inject(AuthService);
  const router = inject(Router);

  if (authService.isAuthenticated()) {
    return true;
  }

  // Puedes guardar la URL a la que intentaba ir
  router.navigate(['/login'], { 
    queryParams: { returnUrl: state.url }
  });
  return false;
};
```

## Route Configuration

```ts
// app.routes.ts
import { Routes } from '@angular/router';
import { authGuard } from './guards/auth.guard';

export const routes: Routes = [
  {
    path: 'dashboard',
    component: DashboardComponent,
    canActivate: [authGuard]
  },
  {
    path: 'admin',
    canActivateChild: [adminGuard],
    children: [
      { path: 'users', component: UsersComponent },
      { path: 'settings', component: SettingsComponent }
    ]
  },
  {
    path: 'profile/:id',
    component: ProfileComponent,
    resolve: { user: userResolver }
  }
];
```

## Return Values

Can return the next type values:

- `boolean`: `true` => allows navigation, `false` => blocks
- `UrlTree`: Redirects to another route
- `Observable<boolean | UrlTree>`: To manage asynchronous operations
- `Promise<boolean | UrlTree>`: To manage asynchronous operations

### Example with observable

```ts
export const authGuard: CanActivateFn = () => {
  const authService = inject(AuthService);
  const router = inject(Router);

  return authService.checkAuth().pipe(
    map(isAuth => isAuth ? true : router.createUrlTree(['/login']))
  );
};
```

# 🌳 Structure recommended

```shell
src
├── app
│   ├── guards
│   │   └── auth.guard.ts
│   ├── pages
│   │   ├── login
│   │   └── register
│   ├── app.config.ts
│   ├── app.routes.ts
│   └── ...
```

>[!QUOTE] **References**