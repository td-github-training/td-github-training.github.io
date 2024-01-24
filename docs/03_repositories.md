## About repositories

A repository is the most basic element of {% data variables.product.prodname_dotcom %}. It's a place where you can store your code, your files, and each file's revision history. Repositories can have multiple collaborators and can be either public{% ifversion ghes or ghec %}, internal,{% endif %} or private.

To create a new repository, go to [https://github.com/new](https://github.com/new). For instructions, see "[AUTOTITLE](/repositories/creating-and-managing-repositories/quickstart-for-repositories)."

## Repository terminology

Before getting started with repositories, learn these important terms.

{% rowheaders %}

Term | Definition |
---- | ---------- |
Branch | A parallel version of your code that is contained within the repository, but does not affect the primary or main branch.
Clone | To download a full copy of a repository's data from {% data variables.location.product_location %}, including all versions of every file and folder.
Fork | A new repository that shares code and visibility settings with the original "upstream" repository.
Merge | To take the changes from one branch and apply them to another.
Pull request | A request to merge changes from one branch into another.
Remote | A repository stored on {% data variables.product.product_name %}, not on your computer.
Upstream | The branch on an original repository that has been forked or cloned. The corresponding branch on the cloned or forked branch is called the "downstream."

{% endrowheaders %}
