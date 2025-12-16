---
title: "Constants"
slug: "constants"
aliases:
 - "/Basics/3"
weight: 3
---
{{<start>}}
In C3, a constant is a compile-time value declared with the `const` keyword.
The name of a constant can only contain uppercase letters, numbers, and underscores.<br>
Constants can be both explicitly typed and untyped when the type can be inferred.

Unlike in C, there is no way to create a runtime value that cannot be modified.
{{<defcod>}}
import std::io;
import std::math;

const TWO = 2; // Untyped
const double HALF = 0.5; // Typed

fn void main()
{
	io::printfn("2*PI = %f", math::PI * TWO);
	io::printfn("PI/2 = %f", math::PI * HALF);
}

{{</defcod>}}
{{<end>}}

