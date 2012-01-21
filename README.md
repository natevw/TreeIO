I'd like to have a simple C library that deals with generic tree structures.

In TreeIO each node would simply store opaque data plus links to children. Higher-level code would implement the building/walking logic for e.g. a BST or B-tree or R-tree or VP-tree... TreeIO takes care of storing and retreiving the nodes from disk in an append-only fashion, providing concurrency and reliability as a low-level service to more interesting (less generic) data structures.

The idea is to share foundational things like generic tree manipluation, serialization to disk, garbage collection (provided a list of active root nodes) so that if someone wanted to, say, build something like CouchDB in node.js or add an interesting tree structure to TouchDB — or whatever someone thinks up next! — they wouldn't have to re-reason through all the fundamentals of reliable disk usage. They could deal with filesystem access at a level above fopen/fseek, sharing the benefits of TreeIO's on-disk format.

You will note a conspicuous lack of code here at present. We need a general architecture outline (draft header files) and then a proof-of-concept implementation to get going. I'd love help.