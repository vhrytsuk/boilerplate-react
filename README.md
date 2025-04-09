## Folder Structure Overview

- **/Components**  
  Contains all UI components. We break these down into several types:

  - **Pages:** Full-page components passed to the router. They may include business logic.
  - **Layouts:** Templates that arrange UI elements (e.g., header, footer, content), which can accept slots as props.
  - **Wrappers (HOCs):** Helper components that extend functionality (e.g., adding animations).
  - **Widgets:** Self-contained components with complete functionality, including business logic.
  - **Dummies:** Purely presentational components that receive data via props.
  - **UI:** Basic interface elements (buttons, inputs, etc.). May include local state or display logic.

  Each component has its own folder (named in **PascalCase**) and usually includes:

  - `MyComponent.tsx`: The main component file, with in-file type definitions.
  - `index.ts`: An entry point for simplified imports.
  - `Styles.module.scss`: Component-specific styles.
  - Optional: `types.ts`, `constants.ts`, or hooks like `useMyComponent.ts` if additional logic is needed.

- **/Models**  
  Centralizes type definitions for the entire application.

  - **Subfolders:** Common, Auth, Users, etc.
  - Each contains:
    - `api.ts`: Describes backend request/response structures.
    - `client.ts`: Contains client-side models.

- **/Api**  
  Contains functions for interacting with the server, organized by entity (e.g., `auth.ts`, `users.ts`, `products.ts`).

- **/App**  
  The application’s initialization layer. It imports global styles, providers, hooks, and the router.

  - Example file: `App.tsx`
  - Also includes a providers folder for wrapping the app with necessary contexts.

- **/Assets**  
  Holds media files (images, icons, audio, video). Organized into subdirectories by category (e.g., `/icons`, `/images`).

- **/Constants**  
  Contains all application-wide constants (e.g., permission rules, variable definitions).

- **/Hooks**  
  Stores custom hooks that are used across the app (e.g., `useWindowSize.ts`).

- **/Stores**  
  Contains state management stores (e.g., using zustand) such as `alertStore.ts`, `userStore.ts`, `uiStore.ts`.

- **/Styles**  
  Holds global and shared style files including layouts, mixins, and variables.

- **/Utils**  
  Contains utility functions (e.g., debounce, compose, localStorage management, validators).

## Import Rules

- **Neutral Components:**
  - **Layouts and Wrappers** have no restrictions on imports.
- **Hierarchical Components:** (from top to bottom)
  - **Pages → Widgets → Dummies → UI**  
    Components may only import from a lower or the same level. For example, a Widget can import UI components but a UI component should not import a Widget.

## Contributing

When adding new features, please follow these guidelines:

- Place reusable or shared elements in their respective directories.
- Maintain the clear hierarchy for component imports.
- Use the established folder structure and naming conventions.
