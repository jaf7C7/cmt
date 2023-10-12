# cmt


An extensible POSIX shellscript for commenting text, written for use with `vi(1)`.


## Examples

Shell-style comments (the default)
```
$ echo 'foo bar' | cmt
# foo bar

$ printf '%s\n' foo bar | cmt
# foo
# bar
```

C-style comments
```
$ echo 'foo bar' | cmt -c
/* foo bar */

$ printf '%s\n' foo bar | cmt -C
/*
 * foo
 * bar
 */
```

Indentation is preserved when commenting indented blocks:

E.g. File contents:
```
main ()
{
	trap 'test -t 1 && printf \\n' EXIT
	if test $# -eq 0
	then
		encode_stream
		return
	fi
	while test $# -gt 0
	do
		if test -f "$1"
		then
			encode_stream <"$1"
		else
			encode_string "$1"
		fi
		shift
	done
}
```

Ex-command `:/while/;/done/!cmt`
```
main ()
{
	trap 'test -t 1 && printf \\n' EXIT
	if test $# -eq 0
	then
		encode_stream
		return
	fi
	# while test $# -gt 0
	# do
	# 	if test -f "$1"
	# 	then
	# 		encode_stream <"$1"
	# 	else
	# 		encode_string "$1"
	# 	fi
	# 	shift
	# done
}
```

`cmt` can also reformat comments with the `-f` option:

Sample code with a very long comment:
```
# Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.
def my_func(foo, bar):
    that = do.this(thing)
    return that
```

Ex-command `:/^# Lorem/!cmt -f`
```
# Lorem Ipsum is simply dummy text of the printing and typesetting
# industry. Lorem Ipsum has been the industry's standard dummy text ever since
# the 1500s, when an unknown printer took a galley of type and scrambled it
# to make a type specimen book.
def my_func(foo, bar):
    that = do.this(thing)
    return that
```

