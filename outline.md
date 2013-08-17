* where we were
  * napster, gnutella, freenet
  * chord, can, pastry: self-organizing key/routing overlays
    * apply them to every problem!  key-value store, filesystems, multicast
* what my paper contributed
  * exact, conjunction keyword search for p2p overlays
  * a tidy use case for bloom filters: lossless (after re-visit) compression for transfer and caching
* what we've done since
  * several more keyword, query, and approximate search for overlays => !! name them
  * more distributed systems with bloom filters => !! cite them
* where we are now
  * search is still centralized
    * legal content: Google, Citeseer, every SOLR installation
      * Google is replicated, of course
  * other businesses still centralized
    * search, chat, A/V streaming (except Spotify), backup, what else???
  * why not on p2p?
    * scarcity of upload bandwidth
    * legal and customer-service murkiness of using users' resources
    * security, reliability
    * backbone bandwidth is really cheap
    * need for extra client software
    * utility computing makes app-scaling linear and pretty cheap
    * legal (wiretap = CALEA) pressures?
  * mostly illegal content: wikileaks, cr.yp.to (?!!), file lockers, bittorrent
  * some features cherry-picked from p2p for data center and cloud services
    * distributed, replicated, fungible, self-organizing
  * "Streisand effect" = informal p2p replication
  * BOINC and SETI@home
* where we should go
  * what's the use case for decentralized search?
  * I don't really buy arguments about p2p providing better scaling, better reliability/survivability/availability, or better proximity
    * Search companies, CDNs, and utility computing do this all very well
  * Subversive content -- political, erotic, copyrighted, patented
  * powerful entities -- copyright interests, national governments -- are
    getting better at snooping, blocking, filtering
  * lots of content blocking is bogus: repressive governments, bad dmca takedowns
  * darknets -- decentralized file distribution -- are a safety valve
    * search is key: you can't read what you can't find



Other notes
* what is p2p?
  * cooperative storage and serving: fault tolerance, load balance, and the ability to harness idle storage and network resources. [CFS]
  * Google?  many thousands of computers, in many states and countries, self-organizing, fault-tolerant = centralized
  * Skype?  centralized login server, self-organizing supernodes up until 2012
    [http://www.zdnet.com/forget-the-conspiracy-theories-skypes-supernodes-belong-in-the-cloud-7000001720/]
  * BitTorrent?  centralized search, usually centralized tracker, distributed storage+bandwidth load
    * many downloads have publisher-provided seeds
    * some clients mooch
      * sometimes intentionally
      * many (especially legit) downloads have far more upload capacity than download
  * CoralCDN (on PlanetLab)?
    * Trusted infrastructure nodes
    * Designed for p2p, but security -- content integrity -- was a sticking point
      * Firecoral introduced a decidedly not-p2p signing service to ensure content integrity
  * Spotify?
    * http://en.wikipedia.org/wiki/Spotify#Technical_information
  * wikipedia: "'peers' act as both suppliers and consumers of resources"
    * except when mooching.  or when not needed -- only a small fraction
      of Skype nodes need to route

* applications
  * Skype, formerly
  * IM/chat??
  * justin.tv??
  * !! [keep reading the wikipedia page]
  * there are some search sites...
    * YaCy (incl. ScienceNet) and FAROO
    * how p2p is SOLR??

* axes: legality?  single point of administrative failure?  spof?  user-contributed resources?

* it's mostly about central point of (administrative) failure
  * if one C&D can shut down the system
  * if one subpoena can retrieve all the data
    * maybe not.  Mozilla sync, lavabit, Mega all use client-keyed encryption

* examples of networks using DHTs:
  * http://en.wikipedia.org/wiki/Peer-to-peer#Structured_networks

* modern applications using it
  * Cassandra??
  * not memcached

* graphs:
  * p2p traffic over time
  * "p2p is dead" news stories over time
  * Google's list/map of takedown requests by nation
