# 2018-12-05 Self Help Meeting Notes

A few topics which came up and my thoughts:

* How is a system transaction (or transaction using SYSTEM_ADDRESS) different
  from a normal one?

	*My impression is that these are simply 'read-only' contract call
	transactions executed by the evm and there isn't much more to them.*

* How many ways are there to deploy contracts and which should be used in
  which situation?

	*There is the usual way of deploying via a transaction then there are
	apparently two ways to do this via the json spec. Perhaps Jake could
	elaborate on the latter two methods and possibly provide some simple
	instructions on how to actually deploy a contract that way. (Like where
	exactly does the contract binary go when using a contract address as the
	parameter to the engine.)*

* Where do indica nodes (launched using the `indica-node` script) get thier
  addresses, etc.

    *They are currently randomly generated but we will need to figure exactly
    out how the whole bootstrapping process will work.*

* Upcoming, 'elected' validators need to share their URLS for direct connections.

	*This is a complicated one because there are so many ways to do it. The
	first thing that came to my head was that immediately upon being 'elected'
	and beginning the keygen process, nodes attempt to connect via Hydrabadger
	to the existing nodes and transmit their information to them for exchange
	over the existing Hydrabadger network. This would require that newly
	elected nodes had some secure way to receive incumbent validator's IPs.
	I'm not sure we'll have to discuss this more.*


Other open stuff:

* When is `finalizeChange` called exactly?

* How do we transition the PublicKey, potentially without requiring every node
  to run SyncKeyGen (and is that requirement worth bothering about).