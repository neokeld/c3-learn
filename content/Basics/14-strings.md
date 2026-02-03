---
title: "Strings"
slug: "strings"
aliases:
 - "/Basics/14"
weight: 14
---
{{<start>}}
ZString -> String (view, no copy)
```c3 {norun=true}
import std::io;

fn void demo_z_to_s() {
    ZString z = "Hello";
    assert(z[z.len()] == '\0'); // The ZString ends in '\0'
    String  s = z.str_view();

    // s.len is the length (without the '\0')
    io::printfn("len = %d", s.len);
}
```
String -> ZString
```c3 {norun=true}
import libc;

fn void demo_s_to_z() {
    String s  = "Hello";
    ZString z = s.zstr_copy(mem);    // '\0' will be here

    // C call which needs char*
    libc::puts(z);
}
```
DString -> String
```c3 {norun=true}
import std::io;
 
fn void demo_ds_to_s() {
    DString ds = dstring::new(mem, "C3");
    String  v  = ds.str_view();      // view (no copy)
    String  c  = ds.copy_str(mem);   // independent copy

    io::printfn(c);
}
```
String -> DString
```c3 {norun=true}
fn void demo_s_to_ds() {
    String s  = "C3 rocks";
    DString ds = dstring::new(mem, s);
    ds.append_string("!"); // example of dstring append method
}
```
Using char**
```c3 {norun=true}
import libc;

// Example of a function that takes a char**
fn void print_params(char** params, int count) {
    for (int i = 0; i < count; i += 1) {
        libc::puts((ZString) params[i]);
    }
}

fn int main(String[] args)
{
  ZString zs = "test".zstr_copy(mem);

  // In C3, unlike in C, a fixed array does not
  // become a pointer when passed as an argument.
  // Either a slice (which is implicitly
  // convertible to a pointer) must be created,
  // or an explicit pointer of the correct type
  // must be provided.

  // So if we have
  // char *[1] params;
  // params[0] = 'test';
  // and we pass params to a function that expects
  // a char** we will get the error "You cannot
  // cast 'char*[1]' to 'char**'".

  // Instead we will do
  char*[] params = { zs }; // slice of 1 element

  print_params(params, params.len);

  return 0;
}
```
{{<endstr>}}

