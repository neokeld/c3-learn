---
title: "For loops"
slug: "for"
aliases:
 - "/Basics/5"
weight: 5
---
C3 `for` loops are the same as in C.<br>
A `for` loop is made of 3 sections that are enclosed in parentheses and separated by semicolons:
 - the init section, which is is run once when the loop is first started and
   usually used to declare the counter (eg `int i = 0`).
 - the condition section, which is checked before the code in the loop body is
   executed each iteration of the loop. The loop will continue running until the
   condition is no longer true.
 - the next section, which is run each iteration after the code in the loop body
   runs, and is usually used to add to the counter.

Any of these sections can be empty, but the semicolons must always be included.
If the condition is empty it will loop forever.

After the closing parenthesis there can either be a block or single line of code
as the body. If a body is not needed a semicolon can be used instead.

{{<codeblock id="sections">}}
import std::io;
fn void main()
{
	const MAX_ITERATIONS = 5;
	for (int iteration = 0; iteration < MAX_ITERATIONS; iteration = iteration + 1)
	{
		io::printfn("Iteration %s", iteration);
	}
	// For loop with no body
	for (int iteration = 0; iteration < MAX_ITERATIONS; loop_next(&iteration));
}

fn void loop_next(int* iteration)
{
	io::printfn("in loop_next %s", *iteration);
	*iteration += 1;
}
{{</codeblock>}}

The `break` keyword can be used to exit out of a loop early, and the `continue`
keyword will skip the rest of the code in the body and continue at the next
iteration of the loop.
{{<codeblock id="break">}}
import std::io;
fn void main()
{
	const MAX_ITERATIONS = 10;
	for (int iteration = 0; iteration < MAX_ITERATIONS; iteration++)
	{
		if (iteration == 3)
		{
			io::printn("Continuing at 3");
			continue;
		}
		else if (iteration == 8)
		{
			io::printn("Breaking");
			break;
		}
		io::printfn("Iteration %s", iteration);
	}
}
{{</codeblock>}}
