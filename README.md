# Parent Repository

This repository contains two sub-projects:

1. **[HomeApp](https://github.com/asifshapnil/microfrontend-home)**
   - Description: HomeApp.
   - Link to GitHub: [HomeApp GitHub](https://github.com/asifshapnil/microfrontend-home)

2. **[HeaderApp](https://github.com/asifshapnil/microfrontend-header)**
   - Description: HeaderApp.
   - Link to GitHub: [HeaderApp GitHub](https://github.com/asifshapnil/microfrontend-header)
     
2. **[AuthApp]([https://github.com/asifshapnil/microfrontend-header](https://github.com/asifshapnil/microfrontend-auth))**
   - Description: AuthApp.
   - Link to GitHub: [https://github.com/asifshapnil/microfrontend-auth)

2. **[ProductApp](https://github.com/asifshapnil/microfrontend-product)**
   - Description: ProductApp.
   - Link to GitHub: [https://github.com/asifshapnil/microfrontend-product)

**Microfrontend Architecture**
there are four separate applications
- home
- header
- auth
- product

Home has shared components like conditional display, private routes, and a shared global redux store that are shared with all others.
The header uses the Display component, which is used to conditionally render imported content from home. It hides the navigation and profile in the nav bar while the user is not authenticated.
Header, Auth, and Product all use the global store to get states and dispatch data, such as user authentication states and usernames, dispatching login actions, and getting profiles.
Home uses routers to dynamically load path-based components which uses private.js to authorize the routes based on authentication.
