# Routing

Angular has Built-in Routing Support

<hr>

Client-Side Routing

Angular watches and manipulates the URL and renders different components for different URLs

IMPORTANT: It is all happening in the browser! There is no server-side routing involved

<hr>

## Enabling Routing

To enable routing in your app, need to define routes in main.ts file

```
bootstrapApplication(AppComponent, {
  providers: [provideRouter(routes)],
}).catch((err) => console.error(err));
```

```
export const routes: Routes = [
  {
    path: 'tasks', //<domain>/tasks
    component: TasksComponent,
  },
];
```

## Rendering Routes

We need to place a markup and use special directive `<router-outlet />` to render component

Child routes need a separate router outlet in the parent component

<br>

**Use routerLink in anchor tag instead of href** `<a routerLink="/tasks">`

<hr>

2 notations:

`<a [routerLink]="'/users/' + user().id" routerLinkActive="selected">`

or

`<a [routerLink]="['/users', user().id]" routerLinkActive="selected">`

<hr>

To access param values from child routes, we have to use withRouterConfig in main.ts with paramsInheritanceStrategy: 'always' function executed

```
bootstrapApplication(AppComponent, {
  providers: [
    provideRouter(
      routes,
      withComponentInputBinding(),
      withRouterConfig({
        paramsInheritanceStrategy: 'always',
      })
    ),
  ],
}).catch((err) => console.error(err));
```
