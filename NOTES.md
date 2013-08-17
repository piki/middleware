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
