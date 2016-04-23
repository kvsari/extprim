extprim
=======

[![Build status](https://travis-ci.org/kennytm/extprim.svg?branch=master)](https://travis-ci.org/kennytm/extprim)
[![Coverage Status](https://coveralls.io/repos/github/kennytm/extprim/badge.svg?branch=master)](https://coveralls.io/github/kennytm/extprim?branch=master)

Extra primitive types. Currently includes:

* u128 (unsigned 128-bit integers)
* i128 (signed 128-bit integers)

[Documentation](https://kennytm.github.io/extprim/extprim/index.html)

Usage
-----

```toml
# Cargo.toml
[dependencies]
extprim = "1.0.0"
```

If you want to use the `u128!()` and `i128!()` macros, please include the `syntex_literals` plugin. Details are explained in the [documentation](https://kennytm.github.io/extprim/extprim_literals/index.html).

Example
-------

```rust
extern crate extprim;

use std::str::FromStr;
use extprim::i128::i128;

fn main() {
    let a = i128::from_str("100000000000000000000000000000000000000").unwrap();
            // convert string to u128 or i128
    let b = i128::new(10).pow(38);
            // 64-bit integers can be directly new'ed
    assert_eq!(a, b);
    let c = i128::from_parts(5421010862427522170, 687399551400673280);
            // represent using the higher- and lower-64-bit parts
    let d = c - a;
            // standard operators like +, -, *, /, %, etc. work as expected.
    assert_eq!(d, i128::zero());
}
```
