# peek-buffer [![Crates.io Version](https://img.shields.io/crates/v/peek-buffer)](https://crates.io/crates/peek-buffer) [![docs.rs](https://img.shields.io/docsrs/peek-buffer)](https://docs.rs/peek-buffer/)
-----
Essential for parsing.

```rs
let mut buffer = PeekBuffer::from("Hello, World!");

// peek without consuming
while let Some(&c) = buffer.peek() {
    println!("{}", c);

    // advance to the next item (char in this situation)
    buffer.advance_char();
    // generally you should use buffer.advance() to move to the next element
    // but if you're parsing a string, you should use buffer.advance_char()
    // since it keeps track of the line and the column the cursor is at.
}

// peek with consuming
buffer.rewind_to_beginning();
while let Some(&c) = buffer.eat() {
    println!("{}", c);
    buffer.advance_char();
}

println!("{}", buffer.len());
```
