
> Which services actually end up being added to `event_loop`? Are there any services that internally just start a separate thread?

Currently `event_loop` (a tokio_core `Reactor`, soon to be a tokio `Runtime`) is a minor player in the scheme of things and is primarily used peripherally. Its usage is often paired with a `CpuPool` (again soon to be replaced). Unfortunately the current situation is a mess, with several parity components creating their own reactors, runtimes, etc. Most of this will be cleaned up soon.

A huge number of services do start their own threads for all kinds of reasons. Although in a few cases this makes sense, for the most part the situation appears to be extremely disorganized.

Looking forward, the usage of a tokio event-loop/runtime will be growing as more systems become modeled as futures, streams, and sinks. A great many of Parity's systems would be much more clearly expressed (and more efficiently implemented) in this way.

> Is the "updater service" for updating Parity itself if there's a new version… or some internal kinds of updates (like "update the blockchain status")? Because I thought the former was already done in `main.rs`?

As far as I know, the updater service is capable of updating while Parity is running whereas main only checks for updates upon startup. There may be some additional differences as well.

> Where is the `Engine` implementation instantiated? Is that here? https://github.com/paritytech/parity-ethereum/blob/403c07c305524d7ec6272d936596b8fb99d13b13/parity/run.rs#L366

Yes, engines are initially instantiated by a [`Spec`](ethcore/src/spec/spec.rs) which takes it's initial configuration from a json spec file, and are then additionally configured and cajoled by several other systems during the startup process.

> Everything's in `Arc`s… which services here have references to which other services and how do they communicate?
>
> What are `sync_provider`, `manage_network` and `chain_notify`? If I remember correctly, `modules::sync` initializes all three of them as different fat pointers (for different traits) to the same `EthSync` object?
Hmm… that's all kind of vague. I guess in general my question is just: "How does it work?"… (edited)

These are huge questions. We'll break these down and discuss them further on Monday.
