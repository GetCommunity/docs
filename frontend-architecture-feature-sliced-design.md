# [Feature Sliced Design](https://feature-sliced.design/docs)

## Table of Contents

- [Feature Sliced Design](#feature-sliced-design)
  - [Table of Contents](#table-of-contents)
  - [Scalable Frontend Architecture](#scalable-frontend-architecture)
  - [Feature Sliced Design Principles](#feature-sliced-design-principles)
  - [Feature Sliced Design in Practice](#feature-sliced-design-in-practice)
    - [Example Frontend Project Structure](#example-frontend-project-structure)

---

## Scalable Frontend Architecture

- `shared` — reusable functionality, detached from the specifics of the project/business. (e.g. UIKit, libs, API)
- `entities` — business entities. (e.g., User, Product, Order)
- `features` — user interactions, actions that bring business value to the user. (e.g. SendComment, AddToCart, UsersSearch)
- `widgets` — compositional layer to combine entities and features into meaningful blocks. (e.g. IssuesList, UserProfile)
- `pages` — compositional layer to construct full pages from entities, features and widgets.
- `routes` — routing layer to define navigation between pages.

## Feature Sliced Design Principles

`shared` > `entities` > `features` > `widgets` > `pages` > `routes`

```tsx
// (shared)         => (entities)  + (features)    => (pages)
<Card> + <Checkbox> => <TaskCard/> + <ToggleTask/> => <TaskPage/>
```

## Feature Sliced Design in Practice

### Example Frontend Project Structure

- **`routes`**
  - `/tasks`
- **`pages`**
  - `TasksListPage` - component
  - `TasksDetailsPage` - component
- **`widgets`**
  - `ToggleDarkMode` - component
- **`features`**
  - `ToggleTask` - component
  - `TasksFilters` - component
- **`entities`**
  - `TaskCard` - component
  - `getTasksListFx({ filters })` - effect
  - `getTaskByIdFx(taskId: number)` - effect
- **`shared`**
  - `Card` - component
  - `Checkbox` - component
  - `getTasksList({ filters })` - api
  - `getTaskById(taskId: number)` - api
