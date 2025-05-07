# Front End Search UI Test

Welcome! 👋🏻 You’re about to embark on a technical assessment that mirrors real-world challenges our engineering team tackles daily. This tech test should take you **about 1–2 hours** to complete.

In this exercise, you’ll work with Vue.js 3, pinia for state management, and the browser’s native fetch API to consume a production Salesfire endpoint. Good luck—and enjoy the process!

---

## 🎯 Background & Context

At Salesfire, we strive to deliver seamless, real-time product discovery experiences:

- **Search** powers our customers’ ability to find products instantly.  
- **Suggestions** adapt as users type, improving engagement and conversion.  
- **State Management** ensures that UI components remain in sync, even as multiple asynchronous calls occur.  

This test focuses on building a minimal search interface that demonstrates your ability to structure a Vue application, manage centralized state with pinia, and integrate with our live search API.

---

## 🎬 User Journey Example

1. **Landing**  
   - A visitor opens the search page.  
2. **Typing**  
   - As the user types “michael cor,”
3. **Fetching**  
   - The application dispatches a pinia action that calls the Salesfire search API.  
4. **Displaying**  
   - Once results arrive, pinia state is updated and the ResultsSet component renders product suggestions.  
5. **Cancelling**  
   - If the user types again before the previous request resolves, the in-flight request is aborted to prevent stale results.  

---

## 🛠️ What You’ll Build

### 1. Project Setup
- Create a new Git repository and push it to GitHub for review.  
- Scaffold a fresh Vue 3 project using the Vue CLI.  
- Install and configure pinia for centralized state.

### 2. Components
- **SearchBar**  
  - Emits the current input value on each keyup.    
- **ResultsSet**  
  - Subscribes to pinia state via getters.  

### 3. State Management
- **Store Structure**  
  - State: query, results, isLoading, error  
  - Actions: performSearch (calls the API, handles cancellation)  
  - Mutations: set query, toggle isLoading, store results and error  
  - Getters: access results and loading status

### 4. API Integration
Use browser-native fetch to call the Salesfire search endpoint at https://aix.salesfire.co.uk/api/searcha with the following query parameters:  
- client_id = 3f32397c-21c6-47e5-9ebd-e9865ea03470  
- query = user’s search term  
- limit = number of results to return  
- page = page number  

Ensure that any prior pending request is aborted before issuing a new one.

### 5. UX Considerations
- Show a loading indicator while searching.  
- Display user-friendly error messages on network failure.  
- Ensure the UI is responsive and accessible (ARIA attributes, keyboard navigation).

---

## 📦 Deliverables

- **README.md**  
  - Prerequisites and setup instructions  
  - npm install, npm run serve, and test commands  

- **Vue Application Code**  
  - Project scaffold (Vue CLI)  
  - src/components/SearchBar.vue  
  - src/components/ResultsSet.vue  
  - src/store/index.js (pinia store)

- **Commit History**  
  - Meaningful, atomic commits demonstrating your workflow.

---

## 🌟 Bonus Points

- Debounce/Throttle: Implement input debouncing to limit API calls.  
- Unit Tests: Add tests for components and store using your preferred testing library.  
- Pagination: Allow users to request additional pages of results.  
- Error Boundaries: Handle unexpected errors gracefully.  
- Accessibility: Ensure components are WCAG-compliant (e.g., ARIA roles, focus management).  
- TypeScript: Convert the store or components to TypeScript.  
- Styling: Add a clean, responsive design
- No results handling

---

Good luck, and we look forward to reviewing your solution!
