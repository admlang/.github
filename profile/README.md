<p align="center">
  <a href="https://adm-lang.dev"><img src="./bot.png" alt="The ADM bot" width="180"></a>
</p>

<h1 align="center">ADM</h1>

<p align="center">
  <b>One language for apps, services and interfaces.</b><br>
  Statically typed, compiled to native binaries.
</p>

<p align="center">
  <a href="https://adm-lang.dev">Website</a> ·
  <a href="https://adm-lang.dev/docs.html">Language</a> ·
  <a href="https://adm-lang.dev/modules.html">Standard library</a> ·
  <a href="https://adm-lang.dev/examples.html">Examples</a> ·
  <a href="https://adm-lang.dev/libraries.html">Libraries</a> ·
  <a href="https://github.com/admlang/adm/releases/latest">Download</a>
</p>

---

ADM is a programming language where the things a program usually glues together are part of the
language: contracts and transactions, services and their permissions, UI components, units of
measure, GPU code, and calls into other language ecosystems.

```adm
application Hello {
	def greet(name string) !string {
		fail "nobody to greet" when name == ""
		return "hello, {name}"
	}

	def new(args string[]) int {
		let line = greet("world") onerror (err error) {
			println(err.message)
			return 1
		}
		println(line)
		return 0
	}
}
```

## Install

```sh
curl -fsSL https://raw.githubusercontent.com/admlang/adm/main/install.sh | sh
```

It installs into `~/.adm` for the current user, with the compiler, the standard library and a
bundled C toolchain; `adm update` fetches new releases. Linux (amd64) is the platform released
today; macOS and Windows packages are coming.

```sh
adm run            # build and run the application in this folder
adm test           # run its check suites
adm get admlang:adm.network.redis
```

## What is here

| Repository | What it holds |
|---|---|
| [adm](https://github.com/admlang/adm) | The compiler, the standard library, the language specification, and the releases |
| [registry](https://github.com/admlang/registry) | The public index of ADM libraries that `adm search` and `adm get` read |
| [database](https://github.com/admlang/database) | Official database libraries: PostgreSQL, MySQL, SQLite, and an embedded store |
| [network](https://github.com/admlang/network) | Official clients for infrastructure services: Redis, S3 |
| [interop](https://github.com/admlang/interop) | Other languages inside an ADM program: JavaScript, Python, Lua, Java, .NET, WebAssembly |
| [examples](https://github.com/admlang/examples) | Programs to read and run |
| [adm-lang.dev](https://github.com/admlang/adm-lang.dev) | The sources of the website |

## Official libraries

```sh
adm search                                # everything in the registry
adm get admlang:adm.database.postgres     # add one to your project
```

| Library | For |
|---|---|
| `adm.database.postgres`, `adm.database.mysql`, `adm.database.sqlite` | SQL databases through `std.data.db` |
| `adm.database.store` | An embedded single-file database |
| `adm.network.redis` | Redis and Valkey |
| `adm.network.s3` | Amazon S3 and compatible stores |
| `adm.interop.js`, `adm.interop.python`, `adm.interop.lua` | Script engines compiled into your program |
| `adm.interop.java`, `adm.interop.dotnet`, `adm.interop.wasm` | The Java VM, the .NET runtime, WebAssembly modules |

Libraries are signed by their publisher. `adm get` verifies the signature and asks before it
grants the permissions a library's code reaches; `adm get --dry-run` reports them and installs
nothing.

## Status

ADM is young. The language and the compiler are usable, the standard library still has gaps,
and things change between releases. Bug reports and questions are welcome in the
[issues of the main repository](https://github.com/admlang/adm/issues).

Licensed under [Apache 2.0](https://github.com/admlang/adm/blob/main/LICENSE).
