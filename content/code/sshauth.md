+++
Categories = ["Development", "GoLang"]
Description = ""
Tags = ["Development", "golang"]
date = "2015-05-27T22:16:49+02:00"
menu = "code"
title = "sshauth"
repo = "sshauth"
norss = true


[[badges]]
	alt = "godoc"
	img = "https://godoc.org/github.com/otm/sshauth?status.png"
	url = "https://godoc.org/github.com/otm/sshauth"

[[badges]]
  alt = "fork me"
  img = "http://githubbadges.com/fork.svg?user=otm&repo=sshauth&style=default"
  url = "https://github.com/otm/sshauth/fork"

[[badges]]
  alt = "download"
  img = "https://img.shields.io/github/release/otm/sshauth.svg"
  url = "https://github.com/otm/sshauth/releases/latest"

+++

##### Mange ssh keys and access in S3.

## Build
go get github.com/otm/sshauth

## Configuration
* Create a S3 bucket. The path used will be `bucket/key/username`, and ssh public
keys should be added there. Note, that key is optional. **Important:** only trusted
persons should have write permission to the bucket, as that will grant ssh access.
* Crate a configuration file: `/etc/sshauth/sshauth.conf` with bucket and key information
```
-bucket bucket-containig-key-conf
-key prefix
```

* Add the following configuration to your `sshd.conf` file
```
AuthorizedKeysCommand /path/to/sshauth
AuthorizedKeysCommandUser username
```
