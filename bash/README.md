# Bash

- [1. Arrays](#1-arrays)
- [2. Associative Arrays](#2-associative-arrays)
- [3. Indenting Here-Documents](#3-indenting-here-documents)
- [4. Include Guards](#4-include-guards)
- [5. Footnotes](#5-footnotes)

## 1. Arrays

<!-- prettier-ignore-start -->

1.  Declare an Array

    ```bash
    dogs=(
    	Bailey
    	Duke
    	Milo
    )
    ```

1.  Loop an Array

	```bash
	for i in "${dogs[@]}"; do
		echo $i
	done
    ```

<!-- prettier-ignore-end -->

## 2. Associative Arrays

1. Declare an Associative Array

   ```bash
   declare -A months
   ```

1. Add Values

   ```bash
   months["january"]=1
   months["february"]=2
   months["march"]=3
   ...
   ```

1. Iterate keys

   ```bash
   for key in "${!months[@]}"; do echo $key; done
   ```

1. Iterate Values

   ```bash
   for val in "${months[@]}"; do echo $val; done
   ```

## 3. Indenting Here-Documents

### Problem

The here-document is great, but it’s messing up your shell script’s formatting. You want to be able to indent for readability[^1].

### Solution

Use `<<-` and then you can use tab characters (only!) at the beginning of lines to indent this portion of your shell script.

```bash
cat <<-EOF >/etc/profile.d/proxy.sh
	export HTTPS_PROXY=$HTTP_PROXY
	export HTTP_PROXY=$HTTP_PROXY
	export NO_PROXY=$NO_PROXY
	export http_proxy=$HTTP_PROXY
	export https_proxy=$HTTP_PROXY
	export no_proxy=$NO_PROXY
EOF
```

### Note

Before we start with tabs vs spaces debate... The only thing that matters is CONSISTENCY.

Tools like [shfmt](https://github.com/mvdan/sh) and [gofmt](https://pkg.go.dev/cmd/gofmt) use tabs by default and there is nothing wrong with it.

## 4. Include Guards

To prevent a file to be ~~included~~ sourced multiple times, you can add the following mechanism as an include guard:

lib/log.sh

```bash
#!/bin/bash

[[ -n $LIB_LOG ]] && return || readonly LIB_LOG=true

<your code here>
```

## 5. Footnotes

[^1]: bash Cookbook - Carl Albing, JP Vossen
