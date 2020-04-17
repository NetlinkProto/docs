.. _route:

NETLINK_ROUTE
=============

Create socket
-------------

.. code-block:: python

    NETLINK_ROUTE = 0
    socket(AF_NETLINK, SOCK_DGRAM, NETLINK_ROUTE)

Receive notifications
---------------------

.. code-block:: python

    pid = os.getpid() + port
    s.bind((pid, groups))

`port` allows to create multiple independent netlink sockets within
on process. `groups` is an old way to tell the kernel which updates
the netlink client wants to receive:

.. code-block:: python

    #  RTnetlink multicast group flags (for use with bind())
    RTMGRP_NONE = 0x0
    RTMGRP_LINK = 0x1
    RTMGRP_NOTIFY = 0x2
    RTMGRP_NEIGH = 0x4
    RTMGRP_TC = 0x8
    RTMGRP_IPV4_IFADDR = 0x10
    RTMGRP_IPV4_MROUTE = 0x20
    RTMGRP_IPV4_ROUTE = 0x40
    RTMGRP_IPV4_RULE = 0x80
    RTMGRP_IPV6_IFADDR = 0x100
    RTMGRP_IPV6_MROUTE = 0x200
    RTMGRP_IPV6_ROUTE = 0x400
    RTMGRP_IPV6_IFINFO = 0x800
    RTMGRP_DECnet_IFADDR = 0x1000
    RTMGRP_NOP2 = 0x2000
    RTMGRP_DECnet_ROUTE = 0x4000
    RTMGRP_DECnet_RULE = 0x8000
    RTMGRP_NOP4 = 0x10000
    RTMGRP_IPV6_PREFIX = 0x20000
    RTMGRP_IPV6_RULE = 0x40000
    RTMGRP_MPLS_ROUTE = 0x4000000


Packet format
-------------

.. code-block::

    netlink header:
        uint32 length
        uint16 type
        uint16 flags
        uint32 sequence number
        uint32 pid
    packet data:
        ...
