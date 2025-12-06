---
title: "{{ replace .Name "-" " " | title }}"
slug: "{{ .Name }}"
date: {{ .Date }}
weight: "changeme"
draft: true
---
{{<start>}}

{{<end>}}

{{<defcod>}}
module example;
import std::io;

fn void main()
{
	io::printn("Hello, World!");
}
{{</defcod>}}
