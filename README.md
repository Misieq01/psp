# Power State Plugin (PSP)
Rust Cross-platform Power State Plugin (PSP).

Using an MPSC channel for emitting events when screen-locked, unlocked, sleep, wake up.

## Support Platform
- [x] macOS
- [x] Windows
- [x] Unix (with D-Bus only)

## Events

#### ScreenLocked
When you logout the session or close your laptop lid

#### ScreenUnlocked
When you login the session or open the laptop lid

#### Resume
Resume from sleep mode

#### Suspend
Turn your computer into sleep mode

## Examples

### With [Tao](https://github.com/tauri-apps/tao)
```
cargo run --example tao
```

### Minimal Example
```rs
let power_monitor = PowerMonitor::new();

// get the event channel receiver
let power_event_channel = power_monitor.event_receiver();

// start listening power state change events
power_monitor.start_listening();

if let Ok(event) = power_event_channel.try_recv() {
  println!("{event:?}");
}
```
