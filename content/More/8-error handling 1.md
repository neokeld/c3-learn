---
title: "Error Handling 1"
slug: "error handling 1"
weight: 8
---
{{<start>}}
- C3 has a peculiar sort of optional values. When an optional has a real value, it contains the value, otherwise it contains the reason the value was missing.
- An optional result type is created by taking a type and appending `!`.
- The simplest optional is `void!`. Because it has no value, it only carries a value in case of a failure, making it identical to an error code.
- It is possible to convert a `void!` to an `anyfault` using `@catch()`
{{<end21>}}

