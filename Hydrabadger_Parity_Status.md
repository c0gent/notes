
* Why Hydrabadger is needed
    * Can't combine two unknowns:

        If I were a Parity expert, I could implement the Honey Badger (HB)
        application logic directly within Parity. If there were an existing,
        fully functioning, peer-to-peer HB client, I could glean enough from
        the existing code to adapt it into Parity. Because I am not a Parity
        expert nor does a functioning HB client exist, it's critical to first
        implement the middleware in an isolated environment (Hydrabadger).

        Attempting to combine the two unknowns at the same time would be
        constantly slowed by increased up-front design complexity, far more
        bugs, and all kinds of other unforeseeable problems. It would take
        considerably longer and be much messier.


    * HBBFT is a complicated algorithm and likewise requires very complex
      application logic to support it.

        * Peer management and messaging
        * Transaction Queues
        * Blockchain management
        * Keeping an extremely close eye on potential security vulnerabilities
