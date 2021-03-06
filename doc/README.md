

# Trooper #

Copyright (c) 2016-2021 Altenwald Solutions, S.L.

__Authors:__ "Manuel Rubio ([`manuel@altenwald.com`](mailto:manuel@altenwald.com)).

[![Build Status](https://img.shields.io/travis/army-cat/trooper/master.svg)](https://travis-ci.org/army-cat/trooper)
[![Codecov](https://img.shields.io/codecov/c/github/army-cat/trooper.svg)](https://codecov.io/gh/army-cat/trooper)
[![License: LGPL 2.1](https://img.shields.io/github/license/army-cat/trooper.svg)](https://raw.githubusercontent.com/army-cat/trooper/master/COPYING)
[![Hex](https://img.shields.io/hexpm/v/trooper.svg)](https://hex.pm/packages/trooper)

Trooper is a soldier in charge to go to other machines (via SSH) and follow your commands.


### <a name="Requirements">Requirements</a> ###

Trooper requires to be run over an Erlang/OTP 19+.

> :warning: **Don't use DSA for OTP 23+**, we found very difficult to put this working. But if you achieve it, please let us know how!

| Erlang Version | Support | Notes |
|:---|:---:|:---|
| 23.2 | :heavy_check_mark: | Recommended if you use OTP 23 |
| 23.1 | :heavy_check_mark: | |
| 23.0 | :heavy_check_mark: | |
| 22.3 | :heavy_check_mark: | Recommended if you use OTP 22 |
| 22.2 | :heavy_check_mark: | |
| 22.1 | :heavy_check_mark: | |
| 22.0 | :heavy_check_mark: | |
| 21.3 | :heavy_check_mark: | Recommended if you use OTP 21 |
| 21.2 | :heavy_check_mark: | |
| 21.1 | :heavy_check_mark: | |
| 21.0 | :heavy_check_mark: | |
| 20.3 | :heavy_check_mark: | Recommended if you use OTP 20 |
| 20.2 | :heavy_check_mark: | |
| 20.1 | :heavy_check_mark: | |
| 20.0 | :heavy_check_mark: | |
| 19.3 | :heavy_check_mark: | Recommended if you use OTP 19 |
| 19.2 | :heavy_check_mark: | |
| 19.1 | :heavy_check_mark: | |
| 19.0 | :heavy_check_mark: | |


### <a name="Example">Example</a> ###

```erlang
1> {ok, File} = file:read_file("/home/trooper/.ssh/id_rsa").
{ok,<<"-----BEGIN RSA PRIVATE KEY-----\nMIIE"...>>}
2> {ok,Trooper} = trooper_ssh:start([{host, "trooper.com"},
                                     {user, "trooper"},
                                     {id_rsa, File}]), ok.
ok
3> trooper_ssh:exec(Trooper, "ls -lha").
{ok,0,
    <<"total 128K\ndrwxr-xr-x 10 trooper trooper 4.0K Mar  8 16:54"...>>}
4> trooper_ssh:exec(Trooper, "ls not_found").
{ok,2,
    <<"ls: cannot access not_found: No such file or directory\n">>}
5> trooper_ssh:stop(Trooper).
ok
```

You can use for the options whatever from [ssh:connect/3](http://erlang.org/doc/man/ssh.md#connect-3) options.

Enjoy!


## Modules ##


<table width="100%" border="0" summary="list of modules">
<tr><td><a href="trooper_app.md" class="module">trooper_app</a></td></tr>
<tr><td><a href="trooper_keys.md" class="module">trooper_keys</a></td></tr>
<tr><td><a href="trooper_proxy.md" class="module">trooper_proxy</a></td></tr>
<tr><td><a href="trooper_proxy_chain.md" class="module">trooper_proxy_chain</a></td></tr>
<tr><td><a href="trooper_proxy_sup.md" class="module">trooper_proxy_sup</a></td></tr>
<tr><td><a href="trooper_scp.md" class="module">trooper_scp</a></td></tr>
<tr><td><a href="trooper_ssh.md" class="module">trooper_ssh</a></td></tr></table>

