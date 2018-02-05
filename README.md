# Welcome!

This GitHub organization has been created as a staging location for a version of [Riak KV](http://basho.com/products/riak-kv/) that:

* Builds and runs on [OTP-20](http://www.erlang.org) and later
* Builds using [Rebar3](https://github.com/erlang/rebar3) and [Relx](https://github.com/erlware/relx)

Prior releases of OTP are _NOT_ supported, nor is the older reltool-based packaging.

### Status

Just starting to populate the repositories.

## About

### History

At the time of Basho's demise, work was under way to create the version of Riak described above.
That work is the starting point for this project.

### Why OTP-20?

While OTP-18 and -19 provide the "modern" modules and interfaces that allow us to avoid most compatibility code, OTP-20 adds a few things that make life a lot easier:

* [Distributed Erlang over TLS](http://erlang.org/doc/apps/ssl/ssl_distribution.html) can be configured with ***all*** TLS options - this makes `inet_tls_dist` viable in real-world production scenarios.
* OS signals are handled reasonably, so applications have a chance to shut down cleanly.
* NIFs can perform [whereis](http://erlang.org/doc/man/erl_nif.html#enif_whereis_pid) queries, allowing them to find and send messages to registered applications. Logging to [lager](https://github.com/erlang-lager/lager) is the most obvious use case for this functionality, but there are many more.
* The new and improved [string](http://erlang.org/doc/man/string.html) module is, well, new and improved _(a lot!)_.
* Dirty schedulers are finally official, crypto supports OpenSSL 1.1.x, and so much more ...

> Some individual packages that don't benefit from any of the new features in OTP-20 will likely remain compatible with at least some prior releases.

### Targets

1. Update the [R3R Rebar Plugin](https://github.com/rebar3riak/r3r_rebar_plugin) (forked from [Basho Rebar Tools](https://github.com/basho/basho_rebar_tools)) to not be specific to Basho development.
2. [Riak Core](https://github.com/basho/riak_core) _2.current-ish_ building and passing unit tests on OTP-20 with Rebar3. This work was mostly completed while Basho was still around.
3. Strip out compatibility code supporting versions of OTP prior to 20. The initial work at Basho maintained backward compatibility with Erlang/OTP R16 and later; a mistake that added undue complexity.
4. Work up the stack to a top-level bare-bones [Riak KV](https://github.com/basho/riak) package, to be assembled with Relx.
5. Convert [Riak Test](https://github.com/basho/riak_test) to live in this brave new world, with basic tests passing.

The above is deliberately vague and incomplete, and there's much, much more to do once it's been achieved.

### Who's Involved

Initially, a very small group of ex-Basho engineers while we get things off the ground.

### Can You Help?

Soon, very soon ...

## License

Most repositories in this project are subject to the [Apache License 2.0](LICENSE).
Some repositories and/or modules _may_ use more permissive licenses.
It is a firm project goal not to require _any_ repositories or modules governed by less-permissive licenses.

> _Some closed-source products may be supported for certain use-cases (such as [Quviq QuickCheck](http://www.quviq.com/products/erlang-quickcheck/) for testing), but are not necessary to use or contribute to this project._
