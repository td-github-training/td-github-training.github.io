## What is a Tag?

A tag is a pointer that points to a specific commit. Git tags are of two variants, an _annotated tag_ and a _lightweight tag_. An annotated tag is an immutable object unlike a lightweight tag which is mutable. Let's practice a bit with tags.

Tags can be created locally with Git, or on GitHub. When creating a tag from the command line, it's recommended to create an "annotated" tag. The following example creates an annotated tag with the `-a` flag, names the tag `v1.0`, and connects it to whichever commit SHA is included.

- `git tag -a v1.0 <SHA>`

To see all tags, type `git tag --list`.

Another caveat with tags is that they are not automatically pushed up with commits. To push tags, type `git push --tags`.

 You can also set this as a default with configs using `git config push.followTags true` which will automatically push tags when their associated commits are pushed. [Read more about this config setting](https://git-scm.com/docs/git-config/2.4.1#git-config-pushfollowTags).