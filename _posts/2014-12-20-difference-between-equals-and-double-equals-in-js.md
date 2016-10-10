---
layout: post
title: Difference between == and === in Javascript
---

The `==` (or `!=`) operator performs an automatic type conversion if needed. 

In the otherhand, the `===` (or `!==`) operator will not perform any conversion. It compares both the value and type, which could be considered faster than `==`.

### Few Examples

| Code            | Result
| `[10] === 10`   | `false`
| `[10]  == 10`   | `true`
| `'10' == 10`    | `true`
| `'10' === 10`   | `false`
| `[]   == 0`     | `true`
| `[] ===  0`     | `false`
| `'' == false`   | `true `
| `'' === false`  | `false`
| `true == "a"`   | `false`
