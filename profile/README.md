# Voland

An open-source Nintendo Switch emulator that runs in the browser.

Voland is a C11 core compiled to WebAssembly, rendering through WebGPU, with thin native platform layers on top. Its web JIT is its own ARM64→WebAssembly translator, `wasm_jit`, built specifically for the browser. The combination — a Switch emulator runtime designed for the browser from day one, with a recompiler that emits WebAssembly — makes browser-based Switch emulation possible without native installation.

Switch 1 is the initial target. Switch 2 support will come once the console is moddable.

## Projects

- **[Voland](https://github.com/voland-emu/Voland)** — The Switch emulator: HLE service implementations, kernel emulation, the softmmu, graphics translation, and the rest of the emulator stack, plus the `wasm_jit` ARM64→WebAssembly translator. Built for the browser as the primary deployment target.
- **[Ballistic](https://github.com/pound-emu/ballistic)** — ARM64 JIT recompiler, used by Voland as an optional, unmodified x86 backend for desktop builds. Not part of the web build.

## Status

Pre-alpha. There are no playable games yet, and Voland does not execute guest code yet. Phase 1 (loading and memory) is nearly done: the softmmu, decrypted-NCA and NSO loading with process bootstrap, thread-local storage, the memory SVCs, and minimal IPC with an `sm:` stub have landed, with CI building and testing every PR natively (GCC, Clang, MSVC) and under Emscripten. Next come the wasm32 memory model and input, then the Phase 2 interpreter. `wasm_jit` is fully specified and lands in Phase 5. Expect a long road before anything is end-user-usable.

If you're looking to play Switch games today, use an actively maintained Switch emulator. Voland's eventual value is browser deployment, not faster compatibility, that part takes time to build.

## Why follow this project

If you're interested in:

- JIT recompiler internals and ARM64-to-WASM translation
- WebAssembly as a serious target for performance-critical emulation
- The technical challenges of running console emulators in browsers (sandboxing, memory model, JIT compilation latency, audio/graphics integration)
- Compiler design without a separate IR: one generated A64 decoder whose predecoded records drive both the interpreter and the JIT, with hot regions compiled to single WebAssembly functions
- Open-source emulator engineering with strict review standards

The full architecture is documented in [DESIGN.md](https://github.com/voland-emu/Voland/blob/main/docs/DESIGN.md), 28 sections covering the C core, the platform layers, the threading model, storage decisions, the JIT, and a realistic phase plan, and the JIT itself in [WASM_JIT.md](https://github.com/voland-emu/Voland/blob/main/docs/WASM_JIT.md). Read those before deciding whether the project is worth your time.

## Contributing

Strict but specific review process. Read [CONTRIBUTING.md](https://github.com/voland-emu/Voland/blob/main/CONTRIBUTING.md) before opening PRs. One task per branch, conventional commits, interface headers reviewed before implementation, and nothing counts as done until CI proves it.

## Community

- **Discussions** ([github.com/voland-emu/.github/discussions](https://github.com/voland-emu/.github/discussions)) — project-wide topics, governance, RFCs, and meta-questions
- **Issues** — bugs and feature requests go to the relevant repo's issue tracker

## About the name

Voland is named for Völundr (also Wayland the Smith in Anglo-Saxon tradition) — the legendary craftsman of Germanic and Norse mythology, master of the forge. The metaphor fits a JIT compiler that builds native machine code from raw foreign instructions.

(Yes, also the Bulgakov reference. We're aware.)
