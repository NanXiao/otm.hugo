+++
Categories = ["Development", "GoLang"]
Description = ""
Tags = ["Development", "golang"]
date = "2015-05-26T20:42:14+02:00"
menu = "code"
title = "Dynaconf"
repo = "dynaconf"
norss = true

[[badges]]
	alt = "godoc"
	img = "https://godoc.org/github.com/otm/dynaconf?status.png"
	url = "https://godoc.org/github.com/otm/dynaconf"

[[badges]]
  alt = "fork me"
  img = "http://githubbadges.com/fork.svg?user=otm&repo=dynaconf&style=default"
  url = "https://github.com/otm/dynaconf/fork"

[[badges]]
  alt = "download"
  img = "https://img.shields.io/github/release/otm/dynaconf.svg"
  url = "https://github.com/otm/dynaconf/releases/latest"

+++

##### Dynaconf generates configuration files from templates.

Dynaconf templates are expressed in the Go template format. See http://golang.org/pkg/text/template/ for more information.

### Installation

go get github.com/otm/dynaconf

### Build/Install

go install github.com/otm/dynaconf

### Usage

dynaconf [options] -template template:outfile\[:actions]

#### Actions

Actions can be one of the following:

*	validate=json - validates output as JSON
*	exec=command - run command after the configuration is created

#### Options

All options are optionally except for **template**

*	dry-run=false: Output result to stdout instead of files
*	log-files=false: Log files written to disk
*	param=[]: Parameters to use when generating configuration
*	template=[]: The template definition to use
*	version=false: Show version and exit

### Examples

#### Render a template

```
dynaconf -template ./examples/cfg.template:/tmp/cfg.json -param name=john
```

#### Render a template with additional environment variables

```
varsion="1.2.3" dynaconf -template ./examples/cfg.template:/tmp/cfg.json -param name=john
```

#### Render a template and validate output

```
dynaconf -template ./examples/cfg.template:/tmp/cfg.json:validate=json -param name=john
```

#### Render a template and run a command after

```
dynaconf -template ./examples/cfg.template:/tmp/cfg.json:exec="cat /tmp/cfg.json" -param name=john
```

#### Render multiple templates at the same time

```
dynaconf -template ./examples/cfg.template:/tmp/cfg.json \
-template ./examples/cfg2.template:/tmp/cfg2.json \
-param name=john -param year=2015
```
