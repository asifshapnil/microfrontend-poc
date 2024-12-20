
# Parent Repository

This repository hosts four sub-projects that form a microfrontend architecture:

## Sub-Projects

1. **[HomeApp](https://github.com/asifshapnil/microfrontend-home)**
   - Description: Manages the shared components, global state, and routing for the entire system.
   - GitHub: [HomeApp GitHub](https://github.com/asifshapnil/microfrontend-home)
   - **Live Version**: [HomeApp Live](https://microfrontend-home-two.vercel.app)

2. **[HeaderApp](https://github.com/asifshapnil/microfrontend-header)**
   - Description: Displays the navigation header and uses shared components from HomeApp.
   - GitHub: [HeaderApp GitHub](https://github.com/asifshapnil/microfrontend-header)

3. **[AuthApp](https://github.com/asifshapnil/microfrontend-auth)**
   - Description: Manages user authentication and login/logout functionalities.
   - GitHub: [AuthApp GitHub](https://github.com/asifshapnil/microfrontend-auth)

4. **[ProductApp](https://github.com/asifshapnil/microfrontend-product)**
   - Description: Handles product-related views and logic.
   - GitHub: [ProductApp GitHub](https://github.com/asifshapnil/microfrontend-product)

---

## Microfrontend Architecture Overview

The system is built using a microfrontend architecture with four independent applications: **HomeApp**, **HeaderApp**, **AuthApp**, and **ProductApp**. Each application is interconnected using **Webpack Module Federation**, allowing them to share components and state dynamically.

### Shared Components and Remote Configuration

1. **HomeApp**:
   - Exposes key components and state to other applications:
     ```javascript
     exposes: {
         './store': './src/store', 
         './Display': './src/shared/Display', 
     },
     remotes: {
         "HeaderApp": "HeaderApp@http://localhost:3001/remoteEntry.js",
         "AuthApp": "AuthApp@http://localhost:3003/remoteEntry.js",
         "ProductApp": "ProductApp@http://localhost:3004/remoteEntry.js",
     }
     ```
   - The `./store` module provides a global Redux store shared across all applications.
   - The `./Display` component enables conditional rendering of shared content, such as hiding navigation or profile sections for unauthenticated users.

2. **HeaderApp**, **AuthApp**, and **ProductApp**:
   - Import shared components and state from **HomeApp**:
     ```javascript
     remotes: {
         HomeApp: 'HomeApp@http://localhost:3000/remoteEntry.js',
     }
     ```
   - By consuming the `store` from **HomeApp**, these applications dispatch and retrieve actions such as user authentication status, profile details, and other shared data.

---

## Deployment and CI/CD

All projects are deployed to **Vercel** and utilize automatic Continuous Integration and Deployment (CI/CD) for efficient production updates:
- **Target Branch**: The `master` branch is reserved for production-ready code.
  - In the `master` branch, remote host URLs point to the live Vercel URLs of each deployed application.
  - Any updates pushed to the `master` branch trigger an automatic rebuild and redeployment in Vercel, ensuring seamless publishing to the live environment.
- **Development Branch**: The `dev` branch is used for local development and testing.
  - In `dev`, remote host URLs point to local environments to facilitate efficient testing during development.

---

### Live Deployment

The live version of the **HomeApp** is accessible at:  
**[https://microfrontend-home-two.vercel.app](https://microfrontend-home-two.vercel.app)**
**Credentials**
username: admin
password: admin

### Summary of URL Configuration:
- In production (`master` branch):
  - Host URLs point to the live Vercel deployment for each application.
- In development (`dev` branch):
  - Host URLs point to the local environment (e.g., `http://localhost`).

This setup ensures smooth collaboration and deployment processes, with clearly defined workflows for both development and production environments.
