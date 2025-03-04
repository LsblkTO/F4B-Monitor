# F4B Health Check : 

This microservice is designed to handle the health check of the conversion funnel. The project uses a monorepo structure with Yarn workspaces, containing two main components:

- **Front End:** The user interface.
- **Back End:** The microservice using Puppeteer for conversion funnel monitoring.

---

## Project Configuration

The root `package.json` is configured as follows:

```json
{
  "name": "F4B_health_check",
  "private": true,
  "workspaces": [
    "front",
    "back"
  ],
  "version": "1.0.0",
  "description": "a microservice to handle health check of the convertion funnel",
  "main": "index.js",
  "author": "TOLSBLK",
  "license": "MIT",
  "scripts": {
    "dev": "concurrently \"yarn workspace back run start:dev\" \"yarn workspace front dev\""
  },
  "devDependencies": {
    "concurrently": "^7.0.0"
  },
  "dependencies": {
    "pm2": "^5.4.3"
  }
```
Workspaces
----------

### Front End

*   Contains the application’s user interface.
*   Typically includes a floating action button (FAB) to trigger the monitoring of the conversion funnel.

### Back End

*   Houses the microservice logic.
*   Implements a Puppeteer script for automating browser actions and checking the conversion funnel.
*   Exposes API endpoints (e.g., `/api/monitor`) for triggering the funnel check.

* * *

Running the Project
-------------------

### Local Development

To run both the frontend and backend concurrently, execute the following command from the root directory:

bash

Copier

`yarn dev`

This command utilizes the `concurrently` package to run:
*   The backend development server with `yarn workspace back run start:dev`
*   The frontend development server with `yarn workspace front dev`

### Integration with Azure DevOps

When setting up your build or release pipeline in Azure DevOps, consider these steps:
1.  **Install Dependencies:**  
    Run `yarn install` at the root level to ensure all workspaces are properly linked.
    
2.  **Build and Test:**  
    Include tasks to build each workspace and run tests as necessary.
    
3.  **Deployment:**  
    Configure your deployment scripts to use PM2 for process management in production (for the backend), and deploy the frontend as required.
    
4.  **Environment Variables:**  
    Make sure to configure environment variables that your application may depend on for both development and production environments.
    

* * *

Additional Information
----------------------

*   **Conversion Funnel Monitoring with Puppeteer:**  
    Customize your Puppeteer script in the `/back` workspace to accurately capture and monitor funnel metrics.
    
*   **Process Management with PM2:**  
    The project uses PM2 to manage the backend process in production environments. Ensure PM2 is properly configured if you plan to deploy.
    
*   **Troubleshooting Tips:**
    *   If you encounter dependency issues, try running `yarn install --force`.
    *   Verify that the ports used by the front end and back end do not conflict with other running services.
For further details or to contribute to this project, please refer to the project documentation or contact TOLSBLK.

arduino

Copier

`This markdown file is tailored for an Azure DevOps Wiki and provides clear guidance on the projec`
