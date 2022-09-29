# Nodes, Workers, and Services

An Ockam node is any running application that can communicate with other applications using various Ockam protocols like [Routing](broken-reference), [Secure Channels](secure-channels.md), [Forwarding](relays-and-portals.md) etc.

We can create Ockam nodes using this command line or using various Ockam programming libraries like our Rust and Elixir libraries.











An Ockam Node is an asynchronous execution environment that can run very lightweight, concurrent, stateful [actors](https://en.wikipedia.org/wiki/Actor\_model) called [Ockam Workers](broken-reference). A node can deliver messages from one worker to another worker. Nodes can also route messages to workers on other remote nodes.

### Create a node

#### Create a node without a name:

```bash
> ockam node create

Node:
  Name: c7a747a6
  Status: UP
  Services:
    Service:
      Type: TCP Listener
      Address: /ip4/127.0.0.1/tcp/52824
    Service:
      Type: Secure Channel Listener
      Address: /service/api
      Route: /ip4/127.0.0.1/tcp/52824/service/api
      Identity: P2a9237c4301398a522a0de6b4c6717f0b166d062050c395f30fc9af88f90ad0b
      Authorized Identities:
        - P2a9237c4301398a522a0de6b4c6717f0b166d062050c395f30fc9af88f90ad0b
    Service:
      Type: Uppercase
      Address: /service/uppercase
    Service:
      Type: Echo
      Address: /service/echo
  Secure Channel Listener Address: /service/api
```

#### Create a node with a name:

In this case, the name that we chose for our node is 'relay'.

```bash
> ockam node create relay

Node:
  Name: relay
  Status: UP
  Services:
    Service:
      Type: TCP Listener
      Address: /ip4/127.0.0.1/tcp/52768
    Service:
      Type: Secure Channel Listener
      Address: /service/api
      Route: /ip4/127.0.0.1/tcp/52768/service/api
      Identity: P2a9237c4301398a522a0de6b4c6717f0b166d062050c395f30fc9af88f90ad0b
      Authorized Identities:
        - P2a9237c4301398a522a0de6b4c6717f0b166d062050c395f30fc9af88f90ad0b
    Service:
      Type: Uppercase
      Address: /service/uppercase
    Service:
      Type: Echo
      Address: /service/echo
  Secure Channel Listener Address: /service/api
```

Take a look at the Messages section to see how to send messages from one node to another.





```
An Ockam node is any running application that can communicate with other applications
using various Ockam protocols like Routing, Secure Channels, Forwarding etc.

We can create Ockam nodes using this command line or using various Ockam programming
libraries like our Rust and Elixir libraries.

Workers
------

Ockam nodes run very lightweight, concurrent, stateful actors called Ockam Workers.
Workers have addresses and a node can deliver messages to workers on the same node or
on a different node using the Ockam Routing Protocol and its Transports.


Routing
------

The Ockam Routing Protocol is a very simple application layer protocol that allows
the sender of a message to describe the `onward_route` and `return_route` of message.

The routing layer in a node can then be used route these messages between workers within
a node or across nodes using transports. Messages can be sent over multiple hops, within
one node or across many nodes.


Transports
------

Transports are plugins to the Ockam Routing layer that allow Ockam Routing messages
to travel across nodes over transport layer protocols like TCP, UDP, BLUETOOTH etc.


Services
------

One or more Ockam Workers can work as a team to offer a Service. Services have
addressed represented by /service/{ADDRESS}. Services can be attached to identities and
authorization policies to enforce attribute based access control rules.

Nodes created using `ockam` command usually start a pre-defined set of default services.

This includes:
    - A uppercase service at /service/uppercase
    - A secure channel listener at /service/api
    - A tcp listener listening at some TCP port
```

EXAMPLES: # Create two nodes $ ockam node create n1 $ ockam node create n2

```
# Send a message to the uppercase service on node 2
$ ockam message send hello --to /node/n2/service/uppercase
HELLO

# A more verbose version of the above would be,
# assuming n2 started its tcp listener on port 4000.
$ ockam message send hello --to /ip4/127.0.0.1/tcp/4000/service/uppercase
HELLO

# Send a message to the uppercase service on node n2 from node n1
$ ockam message send hello --from /node/n1 --to /node/n2/service/uppercase
HELLO

# Create a secure channel from node n1 to the api service on node n2
# The /service/api is a secure channel listener that is started on every node
# Send a message through this encrypted channel to the uppercase service
$ ockam secure-channel create --from /node/n1 --to /node/n2/service/api \
    | ockam message send hello --from /node/n1 --to -/service/uppercase
HELLO

# Create a node, with a specified tcp listener address
$ ockam node create n1 --tcp-listener-address 127.0.0.1:6001

# Create a node, and run it in the foreground with verbose traces
$ ockam node create n1 --foreground -vvv

# Show information about a specific node
$ ockam node show n1

# List all created nodes
$ ockam node list

# Delete the node
$ ockam node delete n1

# Delete all nodes
$ ockam node delete --all

# Delete all nodes and force cleanup
$ ockam node delete --all --force
```



<pre><code><strong>Ockam nodes run very lightweight, concurrent, stateful actors called Ockam Workers.
</strong>Workers have addresses and a node can deliver messages to workers on the same node or
on a different node using the Ockam Routing Protocol and its Transports.</code></pre>

Ockam Workers are lightweight, concurrent, stateful actors.

Workers:

* Run in an Ockam Node.
* Have an application-defined address (like a postal mail or email address).
* Can maintain internal state.
* Can start other new workers.
* Can handle messages from other workers running on the same or a different node.
* Can send messages to other workers running on the same or a different node.

```
One or more Ockam Workers can work as a team to offer a Service. Services have
addressed represented by /service/{ADDRESS}. Services can be attached to identities and
authorization policies to enforce attribute based access control rules.

Nodes created using `ockam` command usually start a pre-defined set of default services.

This includes:
    - A uppercase service at /service/uppercase
    - A secure channel listener at /service/api
    - A tcp listener listening at some TCP port
```