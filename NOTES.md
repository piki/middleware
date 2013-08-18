Inverted index => so called because a "forward index" is doc => {word,
word, word...}

Horizontal partition: each keyword's list is partitioned across all nodes,
e.g., according to portions of the document space.  Like Google and Apache
Solr.

Vertical partition: each keyword is on one node.  Inserting or updating a
document touches up to _k_ nodes for _k_ keywords.  This works best with a
small number of keywords per document: manual tagging, ID3, EXIF, etc.
Best also for filesystems and archives, where files change rarely.  Not
really for full-text / web.

Three techniques:
 - Bloom filters
   - constant-factor improvement by sending F(A) to S_B
 - Caching
   - constant-factor improvement by saving any need to send A or F(A)
 - Incremental results
   - do work proportional to result-set size


YaCy exists, tries to index the whole public web, doesn't return very good results.
DHT backed.  Appears to be keyed on keywords, not documents.  Also appears
to just fetch full doc lists from each peer.
Not clear how many people are running the software.  Hundreds?
From Apr 2005.
Fraud (are the pages my peers returned valid results?) detection consists
only of fetching the page from the origin to see if it has the desired keywords.

FAROO works better.  Claims 2.5 million peers.  C#, not open source.
Claims to have indexed 2 billion pages.
Appears to use a DHT with some variant of keyed by keyword.
Ranking is apparently by how frequently the pages are viewed by users.
Launched Sep 2007.

InfoBeacons = "beacons" provide meta-search for deep-web search services
("sources").  Gradually learns which sources are best for which sorts of
queries.  Uses a p2p network of beacons.  User sends a query to one
beacon, which exhausts its sources trying to provide enough results before
forwarding the query to randomly selected other beacons in the (presumably
unstructured) p2p network.

OverCite = Jeremy Stribling's MIT MS thesis.
DHT-based version of Citeseer, with 4x replication.
Search functionality:
Each document is in exactly one partition.  Partitions map into the DHT.

Planetp = file sharing with an index
Globally replicated directory, containing for-each-node a Bloom filter of
the keywords found in documents on that node.

PIER = relational query engine built atop a DHT and scalable to thousands
of nodes.  Lots of database jargon that I don't really understand.
However, joins tend to touch all nodes (because tuples are randomly
distributed according to <namespace,primary_key>) and create one temporary
table for each relation involved in the join.  Bloom joins don't change
either of these facts, although they do prevent the need to transfer every
tuple in every input relation.  This seems like a far less efficient (if
more general) way to implement keyword search.

PIER is a little snarky (as the DB community often is) about dismissing
p2p keyword search as simply "a workload-specific re- lational query
engine, focusing on Bloom-Filter-based inter- sections of inverted index
posting lists."
