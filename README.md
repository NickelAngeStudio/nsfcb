# nsrb
Nifty Simple Ring Buffer (aka circular buffer) is a no_std library that provides 2 macros to easily create fixed circular buffer on the stack.

See crate documentation for more informations.

# Example
```rust
#[macro_use] extern crate nsrb;
 
#[derive(Clone, Copy, Debug)]
pub struct LogEntry {
    pub time_date : usize,
    pub entry : [char;256]
}
 
impl Default for LogEntry {
    fn default() -> Self { LogEntry { time_date : 0, entry : [' ';256] } }
 }

// Create a Ring buffer for LogEntry
nsrb::ring!(#[derive(Debug)] pub(crate) LogChecked[LogEntry; 10]);
 
fn main() {
    let log = LogChecked::new();
}
 
```



