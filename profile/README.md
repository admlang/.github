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
| [database](https://github.com/admlang/database) | Official database libraries: PostgreSQL, MySQL, SQLite, MongoDB, Elasticsearch, an ORM, and an embedded store |
| [network](https://github.com/admlang/network) | Official clients for infrastructure services: Redis, RabbitMQ (AMQP), Kafka, memcached, etcd, S3 |
| [cloud](https://github.com/admlang/cloud) | Official cloud provider libraries: AWS, Google Cloud, Azure, Cloudflare |
| [ai](https://github.com/admlang/ai) | Official clients for hosted model APIs: OpenAI and compatible servers, Anthropic, Gemini, Ollama |
| [auth](https://github.com/admlang/auth) | Official sign-in libraries: Google, GitHub, Microsoft, Apple |
| [dev](https://github.com/admlang/dev) | Official developer platform libraries: Git, Docker, Kubernetes, GitHub, GitLab |
| [notify](https://github.com/admlang/notify) | Official notification libraries: Slack, Discord, Telegram, Twilio, SendGrid, Postmark |
| [payment](https://github.com/admlang/payment) | Official payment libraries: Stripe, PayPal |
| [telemetry](https://github.com/admlang/telemetry) | Official telemetry exporters: Datadog, Sentry |
| [interop](https://github.com/admlang/interop) | Other languages inside an ADM program: JavaScript, Python, Lua, Java, .NET, WebAssembly |
| [plugins](https://github.com/admlang/plugins) | Editor support: the IntelliJ and VS Code plugins |
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
| `adm.database.mongodb`, `adm.database.elasticsearch` | MongoDB; Elasticsearch and OpenSearch |
| `adm.database.orm` | Typed repositories, queries and migrations over the SQL drivers |
| `adm.network.redis` | Redis and Valkey |
| `adm.network.amqp`, `adm.network.kafka` | RabbitMQ and AMQP 0-9-1 brokers; Kafka and compatible services |
| `adm.network.memcached`, `adm.network.etcd` | memcached; etcd |
| `adm.network.s3` | Amazon S3 and compatible stores |
| `adm.cloud.aws`, `adm.cloud.gcp`, `adm.cloud.azure`, `adm.cloud.cloudflare` | One library per cloud provider |
| `adm.ai.openai`, `adm.ai.anthropic`, `adm.ai.gemini`, `adm.ai.ollama` | Hosted model APIs, behind `std.ai.llm` |
| `adm.auth.google`, `adm.auth.github`, `adm.auth.microsoft`, `adm.auth.apple` | Signing users in with an identity provider |
| `adm.dev.git`, `adm.dev.docker`, `adm.dev.kubernetes` | Git repositories, container engines, Kubernetes clusters |
| `adm.dev.github`, `adm.dev.gitlab` | The GitHub and GitLab APIs and webhooks |
| `adm.notify.slack`, `adm.notify.discord`, `adm.notify.telegram` | Chat platforms |
| `adm.notify.twilio`, `adm.notify.sendgrid`, `adm.notify.postmark` | SMS, voice and transactional mail |
| `adm.payment.stripe`, `adm.payment.paypal` | Payments, subscriptions and webhooks |
| `adm.telemetry.datadog`, `adm.telemetry.sentry` | Exporters for the `Telemetry` service |
| `adm.interop.js`, `adm.interop.python`, `adm.interop.lua` | Script engines compiled into your program |
| `adm.interop.java`, `adm.interop.dotnet`, `adm.interop.wasm` | The Java VM, the .NET runtime, WebAssembly modules |

Libraries are signed by their publisher. `adm get` verifies the signature and asks before it
grants the permissions a library's code reaches; `adm get --dry-run` reports them and installs
nothing.

## Status

Bug reports and questions are welcome in the
[issues of the main repository](https://github.com/admlang/adm/issues).

Licensed under [Apache 2.0](https://github.com/admlang/adm/blob/main/LICENSE).
