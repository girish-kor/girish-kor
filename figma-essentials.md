# UI/UX Design Essentials with Figma

## 1. UI vs UX Basics
- **UI (User Interface)**: Visual design of buttons, icons, layouts, and interactions.
- **UX (User Experience)**: Focus on usability, accessibility, and user satisfaction.
- **Key Principle**: "UI is how it looks, UX is how it works."

## 2. Figma Interface Essentials
- **Workspace Components**:
  - **Canvas**: Design area.
  - **Layers Panel**: Manage objects.
  - **Properties Panel**: Adjust alignment, spacing, effects.
  - **Assets**: Store components/styles.
  - **Plugins**: Extend functionality.

## 3. Core Design Tools
- **Frames**: Containers for designs (use `F` key).
  ```markdown
  - Set frame sizes for devices (Mobile: 360x640, Desktop: 1440x1024).
  ```
- **Shapes & Text**:
  - Rectangle (`R`), Ellipse (`O`), Line (`L`), Text (`T`).
- **Pen Tool**: Create custom vectors (`P`).

## 4. Components & Variants
- **Components**: Reusable elements (e.g., buttons, icons).
  ```markdown
  1. Design element → Right-click → "Create component".
  2. Use `Assets` panel to drag instances.
  ```
- **Variants**: Manage states (e.g., default/hover/active buttons).

## 5. Auto Layout
- **Purpose**: Create responsive layouts that adjust to content.
  ```markdown
  1. Select elements → Right-click → "Add Auto Layout".
  2. Adjust padding, spacing, and alignment in properties.
  ```

## 6. Constraints
- Define how elements resize within frames.
  ```markdown
  - Example: Set button to "Left & Top" constraints to fix position.
  ```

## 7. Prototyping Basics
- **Create Interactions**:
  1. Select element → `Prototype` tab.
  2. Drag connector to target frame.
  3. Set trigger (e.g., "On Click") and action (e.g., "Navigate To").
- **Preview**: `Play` button (top-right) to test flows.

## 8. Design Systems
- **Consistency**:
  - **Color Styles**: Define primary/secondary palettes.
  - **Text Styles**: Save headings/body text formats.
  - **Grids**: Use 8px/12px grids for alignment.

## 9. Collaboration Features
- **Share Prototypes**: 
  1. `Share` button → Copy link → Set permissions (view/edit).
- **Comments**: `C` key to add context-specific feedback.

## 10. Key Shortcuts
- `Ctrl/Cmd + D`: Duplicate
- `Ctrl/Cmd + G`: Group elements
- `Shift + A`: Add auto layout
- `Ctrl/Cmd + Alt + C`: Copy as CSS/SVG code

## 11. UI Best Practices
- **Hierarchy**: Use size/color contrast for emphasis.
- **Spacing**: Follow 8px grid system.
- **Accessibility**: Ensure color contrast ratio ≥ 4.5:1.

## 12. Handoff to Developers
- **Export Assets**: Select layer → `Export` tab → Choose format (SVG/PNG).
- **Inspect Mode**: Developers extract CSS/React code from layers.

## 13. Plugins for Efficiency
- **Must-Haves**:
  - **Unsplash**: Add stock images.
  - **Iconify**: Access 100k+ icons.
  - **Contrast Checker**: Test accessibility.
  - **Autoflow**: Diagram user flows.

## 14. Practice Projects
- **20% Tasks for 80% Skills**:
  1. Design a mobile login screen.
  2. Create a reusable button component with variants.
  3. Prototype a 3-step onboarding flow.
  4. Build a color/text style library.
