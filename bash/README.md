# Bash

## Arrays

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

## Here-Documents

### Problem

The here-document is great, but it’s messing up your shell script’s formatting. You want to be able to indent for readability.

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

### References

1. bash Cookbook - Carl Albing, JP Vossen, Cameron Newham
