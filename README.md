# Vexora

Vexora is a Minecraft launcher built with Tauri, React, and TypeScript. It is currently under active development and not yet ready for general use.

## Status

This is a work in progress. Core systems are functional; several major features are not implemented yet.

Working:
- Offline profile creation and multi-account switching
- Persistent settings (RAM allocation, game directory, Java path)
- Basic instance creation and management
- Custom window chrome and UI

Not yet implemented:
- Microsoft/Xbox authentication (pending API access approval)
- Minecraft version downloading (client, libraries, assets)
- Java detection and management
- Actually launching the game
- Download queue and logging

## Tech stack

- [Tauri 2](https://tauri.app/) — desktop shell and native backend (Rust)
- React 19 + TypeScript
- Tailwind CSS v4
- Zustand for state management
- Framer Motion for UI animation

## Project structure

```
src/
  components/   UI components, grouped by feature area
  pages/        Route-level views (display only, no business logic)
  services/     Business logic — auth, Minecraft, storage
  store/        Zustand stores
  types/        Shared TypeScript types
  utils/        Pure helper functions

src-tauri/      Rust backend
```

The project follows one rule throughout: pages render state, they don't compute it. Anything involving the filesystem, authentication, or Minecraft-specific logic lives in `services/`.

## Development

Requirements: Node.js, Rust, and the Tauri CLI prerequisites for your platform (see the [Tauri docs](https://tauri.app/start/prerequisites/)).

```bash
npm install
npm run tauri dev
```

To build:

```bash
npm run tauri build
```

## Notes on Microsoft authentication

Vexora requests the `XboxLive.signin` scope, which requires Microsoft's review and approval before it works against a live account. Until that approval comes through, Microsoft sign-in will not function — offline profiles work in the meantime.

## License

Not yet decided.
