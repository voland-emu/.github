# Voland

An open-source Nintendo Switch emulator that runs in the browser.

Voland is built on **Ballistic**, a custom ARM64 JIT recompiler that targets WebAssembly, x86_64, and ARM64. The combination — a JIT recompiler with a fast WASM backend, integrated with a Switch emulator runtime — makes browser-based Switch emulation possible without native installation.

Switch 1 is the initial target. Switch 2 support will come once the console is moddable.

## Projects

- **[Ballistic](https://github.com/pound-emu/ballistic)** — Custom ARM64 JIT recompiler. Targets WebAssembly (the primary backend for Voland), x86_64, and ARM64. Architecturally agnostic; useful to anyone building an emulator or dynamic recompiler for ARM64 code.
- **[Voland](https://github.com/voland-emu/voland)** — The Switch emulator runtime. Integrates Ballistic with HLE service implementations, kernel emulation, graphics translation, and the rest of the emulator stack. Built for the browser as the primary deployment target.

## Status

Pre-alpha. There are no playable games yet. Foundation work is in progress, Ballistic's IR layer, the WebAssembly backend, the runtime integration. Expect a long road before anything is end-user-usable.

If you're looking to play Switch games today, use [Ryujinx](https://ryujinx.org/), [Suyu](https://git.suyu.dev/suyu/suyu), or another mature Switch emulator. Voland's eventual value is browser deployment, not faster compatibility, that part takes time to build.

## Why follow this project

If you're interested in:

- JIT recompiler internals and ARM64-to-WASM translation
- WebAssembly as a serious target for performance-critical emulation
- The technical challenges of running console emulators in browsers (sandboxing, memory model, JIT compilation latency, audio/graphics integration)
- Compiler design (custom SSA-based IR, structured control flow, tiered compilation)
- Open-source emulator engineering with strict review standards

The technical work is documented thoroughly. Design docs and architectural decisions are visible in the repos.

## Contributing

Strict but specific review process. Read [CONTRIBUTING.md](https://github.com/pound-emu/ballistic/blob/main/CONTRIBUTING.md) before opening PRs. Atomic commits, sign-off required, no force-pushes to main.

## Community

- **Discussions** ([github.com/voland-emu/.github/discussions](https://github.com/voland-emu/.github/discussions)) — project-wide topics, governance, RFCs, and meta-questions
- **Issues** — bugs and feature requests go to the relevant repo's issue tracker
- 
## About the name

Voland is named for Völundr (also Wayland the Smith in Anglo-Saxon tradition) — the legendary craftsman of Germanic and Norse mythology, master of the forge. The metaphor fits a JIT compiler that builds native machine code from raw foreign instructions.

(Yes, also the Bulgakov reference. We're aware.)
