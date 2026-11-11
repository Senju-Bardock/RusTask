# RusTask

A fast, lightweight, faithful recreation of the Windows 11 Task Manager, written in Rust.

> **Status:** early development. Nothing is usable yet. See the [roadmap](ROADMAP.md).

## Why?

- **Light on the system.** No garbage collector, predictable memory use and near-instant startup. A tool that monitors your hardware should not be a burden on it.
- **Faithful to the original.** Same layout, same tabs, same feel as the Windows 11 Task Manager, so there is nothing new to learn.
- **Minimal dependencies.** The only intended dependency is Microsoft's official [`windows`](https://crates.io/crates/windows) crate (Win32 bindings). The GUI approach is still to be decided (see the roadmap).
- **Learn by building.** Rust talks to the hardware and the OS directly, which makes this a good showcase of what the language can do.

## Platform

Windows 10/11 only (x86_64). Cross-platform support is explicitly out of scope for now.

## Planned features

- Processes tab: sortable table, end task, per-process CPU / memory / disk / network
- Performance tab: live graphs for CPU, memory, disk and network
- Startup apps, Services and Details tabs
- Dark and light themes following the system setting

## Building

```sh
cargo build --release
```

Requires a recent stable Rust toolchain (<https://rustup.rs>) targeting `x86_64-pc-windows-msvc`.

## Contributing

The project is in its very early days. Ideas and issues are welcome; see the [roadmap](ROADMAP.md) for what is planned.

## License

MIT, see [LICENSE](LICENSE).
