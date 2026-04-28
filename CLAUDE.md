# 👶 BabyApp (BabyTracker PWA) - CLAUDE.md

## 🚀 Common Commands
- **Start local server**: `npx serve .` (The app is a static web application without a complex build process).
- **Run tests**: `node tests/app-core.test.mjs` (Unit tests for core functions run using the built-in Node.js test runner - `node:test`).

## 🏗️ Architecture & Stack
- **Technologies**: Vanilla JavaScript (ES Modules), HTML5, CSS3, Firebase Firestore, PWA (Service Worker).
- **`app.js`**: The main file handling the UI (DOM Manipulation), event listeners, Firebase integration, and application state management.
- **`app-core.mjs`**: Contains "pure" functions for business logic, time calculations (like calculating age and sleep duration), data normalization, and schema management. This file is DOM-independent to facilitate easier testing.
- **`styles.css`**: Application styling. Based on CSS Custom Properties for built-in Dark/Light theme support and a mobile-first responsive design.
- **PWA System**: The project includes `service-worker.js` (using a Network First strategy for core files) and `manifest.webmanifest` to enable home screen installation and offline capabilities.

## 📝 Code Style & Guidelines
- **UI Language & Directionality**: The app is designed for an Israeli audience and is configured as RTL (Right-to-Left). Any new UI text must be written in Hebrew, while maintaining proper support for directional styling (e.g., using `margin-inline-start` instead of `margin-left` where appropriate).
- **Separation of Concerns**: Keep all computational and business logic strictly within `app-core.mjs`. The `app.js` file should focus solely on connecting this logic to the views and the database.
- **State Management & Rendering**: UI updates should be performed by calling the central `render()` function in `app.js` following any changes to the local State. Do not update DOM elements directly from within logic functions.
- **Offline-First Support**: The project relies on Firestore's built-in Persistent Local Cache mechanism. Ensure that all read and write operations function transparently, even without an active internet connection.
- **Testing**: Any addition of a helper function or modification of logic in `app-core.mjs` must be accompanied by appropriate unit tests in the `tests/app-core.test.mjs` file.
- **Mobile Optimization**: When designing new UI components (such as Bottom Sheets and Quick Actions), always account for touch target areas to ensure they are comfortable and accessible for one-handed mobile use.