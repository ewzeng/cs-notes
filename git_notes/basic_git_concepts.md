git maintains two primary data structures in the .git file: object store and index

##### object store

object store: contains full history of repository

object store consists of key-value pairs: (SHA~1 of object, object). so if two objects have identical contents, only one object is stored

there are four types of objects:

- blobs: each version of a file is represented by a blob. blobs do not contain any metadata about the file, or even its name
- trees: stores directory structure. leaf nodes point to blobs, and contain metadata of that blob
- commit: holds metadata for each commit and points to the tree object that captures the state of repo during commit
- tag: assigns a name to any object, usually a commit

(when we say A points to object B, what really happens is that A stores the SHA~1 hash of object B)

![](figures\git_object_store.png)

note all the names are SHA~1 hashes

##### index

index captures a version of the project's overall structure. you execute git commands to stage changes in the index. the index records and retains those changes, keeping them safe until you are ready to commit them.
