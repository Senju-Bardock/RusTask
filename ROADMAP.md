# RusTask Roadmap

Goal: a lightweight, faithful Rust recreation of the Windows 11 Task Manager.

Legend: `[ ]` planned, `[x]` done.

## Phase 0: Foundations

- [x] Repository, README, roadmap, license
- [ ] Decide the GUI approach (see "Open decisions")
- [ ] Set up CI (build, `cargo fmt --check`, `cargo clippy`)
- [ ] Project structure: separate the data layer (`core`) from the UI

## Phase 1: Data layer (no UI yet)

Read system data through the Win32 API (`windows` crate), exposed through a clean internal API.

- [ ] Total CPU usage (`GetSystemTimes`)
- [ ] Per-core CPU usage
- [ ] Memory: total, used, available, committed
- [ ] Process list: PID, name, parent, threads (`CreateToolhelp32Snapshot` / `NtQuerySystemInformation`)
- [ ] Per-process CPU and memory
- [ ] Disk activity (PDH counters)
- [ ] Network throughput
- [ ] Basic CLI output to validate the data against the real Task Manager

## Phase 2: Minimal GUI

- [ ] Main window with tab navigation
- [ ] **Processes** tab: sortable table with live refresh
- [ ] End task / end process tree
- [ ] Refresh rate setting

## Phase 3: Performance tab

- [ ] Real-time graphs: CPU, memory, disk, network
- [ ] Side panel with per-resource summary (like the original)
- [ ] Per-core CPU view
- [ ] Hardware info: CPU model, clock speed, core count, RAM size

## Phase 4: Parity with the original

- [ ] App history / Startup apps tab
- [ ] Users tab
- [ ] Details tab
- [ ] Services tab
- [ ] Dark and light themes following the system setting
- [ ] Efficiency mode for processes
- [ ] GPU usage

## Phase 5: Polish and release

- [ ] Keyboard shortcuts
- [ ] Settings persistence
- [ ] Installer / portable release on GitHub Releases
- [ ] Benchmarks: memory and CPU footprint compared with the built-in Task Manager

## Open decisions

| Topic | Options | Notes |
| --- | --- | --- |
| GUI | `egui` / `eframe` | Fastest to build, light, but an extra dependency |
| GUI | `windows` + Direct2D | Minimal weight and full control, much more work |
| GUI | Win32 + GDI | Zero extra dependencies, classic look |
| Data source | `NtQuerySystemInformation` vs documented APIs | Undocumented APIs are faster but can change between Windows versions |

## Non-goals (for now)

- Linux / macOS support
- Remote monitoring
- Replacing the system Task Manager's privileged features
