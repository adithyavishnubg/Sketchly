# Sketchly

Sketchly is an open-source infinite-canvas whiteboard designed for brainstorming, diagramming, note-taking, and visual collaboration.

Create ideas freely on an unlimited canvas with drawing tools, shapes, text, images, and presentation features in a lightweight and responsive interface.

## Features

- **Infinite Canvas** — Pan, zoom, and navigate large boards smoothly
- **Drawing Tools** — Freehand pen with pressure and velocity-based strokes
- **Shapes & Diagrams** — Rectangles, circles, triangles, diamonds, stars, arrows, and lines
- **Text & Notes** — Add text, labels, and sticky notes directly to the canvas
- **Image Support** — Paste, upload, and drag images onto your board
- **Selection Tools** — Move, resize, rotate, duplicate, and reorder elements
- **Laser Pointer** — Highlight ideas while presenting
- **Undo & Redo** — Gesture-based editing history
- **Themes & Grids** — Light and dark themes with customizable canvas backgrounds
- **PNG Export** — Export the entire canvas or selected content
- **Responsive Interface** — Adaptive toolbar for different screen sizes
- **Keyboard Shortcuts** — Quickly access common tools and actions
- **Sync-Ready Data Model** — Canvas changes are represented as JSON-safe diffs for persistence and synchronization
- **Cross-Platform** — Core engine with React and React Native support

## Tech Stack

**Frontend:** React, React Native, JavaScript, TypeScript  
**Build:** Vite, ESM  
**Architecture:** Framework-independent core engine with React bindings

## Project Structure

packages/
├── core          # Core whiteboard engine
├── react         # React components and hooks
└── react-native  # React Native integration

examples/
├── vanilla       # Plain JavaScript example
└── react-demo    # React playground

## Getting Started

### Installation

npm install

### Development

npm run dev

### Testing

npm test

### Build

npm run build

### Type Checking

npm run typecheck

## Data Model

Sketchly uses a lightweight document model where canvas changes are represented as structured diffs:

{
  added: {},
  removed: {},
  updated: {}
}

This model supports local persistence, history management, auditing, and real-time synchronization.

## License

MIT
