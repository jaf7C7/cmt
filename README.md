# `cmt`

A simple filter which toggles various types of comments. Easily extensible and
written in POSIX sh.

## Motivation

I wanted an easier way to write comments, both for formatting and debugging
purposes. I didn't want to have to deal with plugins and, this approach is
inherently compatible with all versions of `vi` and `vim` without the need to
install any plugin or plugin manager.

## Goals

* As small and simple as possible
* Minimum hassle to install/configure
* Compatible/portable

## Example usage

Block comments:
![cmt C-style block comment example](./media/cmt_ex-1.gif)

Debugging:
![cmt debugging example](./media/cmt_ex-2.gif)
