# Sketchly

> An open-source, extensible infinite canvas engine for building whiteboards, diagramming tools, visual editors, and collaborative experiences.

Sketchly is a modern infinite-canvas whiteboard designed for brainstorming, diagramming, note-taking, and visual collaboration.

Built around a framework-independent core, Sketchly provides the foundation for creating high-performance visual editing experiences across web and native platforms. It includes support for freehand drawing, shapes, text, images, selection, transformations, history management, and export capabilities.

## Features

### Infinite Canvas

Navigate an unlimited workspace with smooth pan and zoom interactions, designed to support everything from quick sketches to large visual diagrams.

### Drawing

Create expressive freehand drawings with support for:

* Pressure-sensitive strokes
* Velocity-based stroke rendering
* Smooth pointer interactions
* Flexible drawing tools

### Shapes and Diagramming

Build diagrams and structured visual layouts using:

* Rectangles
* Circles
* Triangles
* Diamonds
* Stars
* Lines
* Arrows

### Text and Notes

Add contextual information directly to the canvas with:

* Text elements
* Labels
* Annotations
* Sticky notes

### Image Support

Bring external content into your workspace through:

* File uploads
* Clipboard paste
* Drag and drop

### Selection and Transformations

Manipulate canvas elements with support for:

* Selection
* Moving
* Resizing
* Rotation
* Duplication
* Layer ordering

### Presentation Tools

Use a laser pointer to guide attention and highlight ideas during presentations or collaborative sessions.

### History Management

Built-in undo and redo support enables efficient editing workflows and reliable state management.

### Themes and Backgrounds

Customize the canvas environment with:

* Light and dark themes
* Configurable backgrounds
* Grid support

### Export

Export the complete canvas or selected elements as PNG images.

### Responsive Interface

Sketchly is designed with responsive layouts and adaptive controls to provide a consistent experience across different screen sizes.

### Keyboard Shortcuts

Improve productivity with keyboard shortcuts for common tools and editing operations.

---

## Architecture

Sketchly is designed around a framework-independent core.

```text id="jfxqgm"
┌─────────────────────────────────────┐
│         Application Layer           │
│                                     │
│   React · React Native · Custom UI  │
└──────────────────┬──────────────────┘
                   │
                   ▼
┌─────────────────────────────────────┐
│           Sketchly Bindings         │
│                                     │
│   Components · Hooks · Adapters     │
└──────────────────┬──────────────────┘
                   │
                   ▼
┌─────────────────────────────────────┐
│            Sketchly Core            │
│                                     │
│ Canvas · Elements · Geometry        │
│ Selection · History · Diffs         │
└─────────────────────────────────────┘
```

The core package is responsible for the document model, canvas operations, geometry, selection, history, and change tracking. Platform-specific packages provide integrations for React and React Native.

This architecture allows the rendering layer and application UI to evolve independently from the underlying canvas engine.

---

## Packages

```text id="occkpu"
packages/
├── core/           # Framework-independent whiteboard engine
├── react/          # React components and hooks
└── react-native/   # React Native integration

examples/
├── vanilla/        # Vanilla JavaScript example
└── react-demo/     # React example application
```

### `@sketchly/core`

The framework-independent core responsible for the whiteboard document model and canvas operations.

### `@sketchly/react`

React bindings, components, and hooks for building Sketchly-powered applications.

### `@sketchly/react-native`

React Native integration for bringing Sketchly's core functionality to native applications.

---

## Getting Started

### Prerequisites

* Node.js 18 or later
* npm, pnpm, or Yarn

### Installation

Clone the repository:

```bash id="uimxpo"
git clone <repository-url>
cd sketchly
```

Install dependencies:

```bash id="mdujkm"
npm install
```

### Development

Start the development environment:

```bash id="exbsrk"
npm run dev
```

### Testing

Run the test suite:

```bash id="i5vzwy"
npm test
```

### Build

Build all packages:

```bash id="yiknft"
npm run build
```

### Type Checking

Run TypeScript validation:

```bash id="g7fokz"
npm run typecheck
```

---

## Data Model

Sketchly represents document changes using a lightweight, JSON-safe diff structure.

```ts id="f0bwhh"
interface DocumentDiff {
  added: Record<string, unknown>;
  removed: Record<string, unknown>;
  updated: Record<string, unknown>;
}
```

Example:

```ts id="7jvr1x"
{
  added: {
    "element-1": {
      type: "rectangle"
    }
  },

  removed: {},

  updated: {
    "element-2": {
      x: 120,
      y: 80
    }
  }
}
```

This model provides a predictable foundation for state management and enables features such as:

* Undo and redo
* Local persistence
* Change history
* Auditing
* Network synchronization
* Real-time collaboration

Because the document format is JSON-safe, changes can be serialized and transmitted between clients without requiring framework-specific state.

---

## Design Principles

Sketchly is built around a few core principles.

### Framework Independence

The core engine should not depend on React, React Native, or a specific rendering environment.

### Composability

Applications should be able to use individual parts of the system without adopting an entire application framework.

### Predictable State

Canvas changes should be explicit, serializable, and easy to inspect.

### Extensibility

The architecture should support future additions such as custom elements, plugins, alternative renderers, and collaboration providers.

### Performance

The canvas should remain responsive as documents grow in size and complexity.

---

## Use Cases

Sketchly can serve as a foundation for:

* Digital whiteboards
* Diagram editors
* Flowchart tools
* Visual note-taking applications
* Collaborative workspaces
* Infinite canvas applications
* System architecture tools
* Educational software
* Design and ideation tools

---

## Roadmap

Planned and potential improvements include:

* [ ] Real-time collaboration
* [ ] Multiplayer cursors
* [ ] Presence indicators
* [ ] SVG export
* [ ] PDF export
* [ ] Custom elements
* [ ] Plugin API
* [ ] Templates
* [ ] Cloud persistence
* [ ] Version history
* [ ] Presentation mode improvements
* [ ] Additional rendering backends

---

## Contributing

Contributions are welcome.

If you would like to contribute:

1. Fork the repository.
2. Create a feature branch.
3. Make your changes.
4. Add or update tests where appropriate.
5. Ensure the project builds and passes type checking.
6. Submit a pull request with a clear description of the changes.

Before opening a large feature or architectural change, consider opening an issue first to discuss the proposed approach.

---

## Development

The project is organized as a monorepo, allowing the core engine and platform bindings to be developed and released independently.

Typical development workflow:

```bash id="u8bpo2"
npm install
npm run dev
npm test
npm run typecheck
npm run build
```

---

## License

Sketchly is released under the [MIT License](./LICENSE).

---

## Philosophy

Sketchly is built to be more than a whiteboard application.

The goal is to provide a flexible, well-structured foundation for building visual software — from simple sketching tools to collaborative diagram editors and complex infinite-canvas applications.

**Build ideas visually. Extend without limits.**
