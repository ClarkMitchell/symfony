Symfony Contracts
=================

A set of abstractions extracted out of the Symfony components.

Can be used to build on semantics that the Symfony components proved useful - and
that already have battle tested implementations.

Design Principles
-----------------

 * contracts are split by domain, each into their own sub-namespaces;
 * contracts are small and consistent sets of PHP interfaces, traits, normative
   docblocks and reference test suites when applicable, etc.;
 * all contracts must have a proven implementation to enter this repository;
 * they must be backward compatible with existing Symfony components.

FAQ
---

### How to use this package?

The abstractions in this package are useful to achieve loose coupling and
interoperability. By using the provided interfaces as type hints, you are able
to reuse any implementation that matches their contracts. It could be a Symfony
component, or another one provided by the PHP community at large.

Depending on their semantics, some interfaces can be combined with autowiring to
seamlessly inject a service in your classes.

Others might be useful as labeling interfaces, to hint about a specific behavior
that could be enabled when using autoconfiguration or manual service tagging (or
any other means provided by your framework.)

### How is this different from PHP-FIG's PSRs?

When applicable, the provided contracts are built on top of PHP-FIG's PSRs. We
encourage relying on them and won't duplicate the effort. Still, the FIG has
different goals and different processes. Here, we don't need to seek universal
standards. Instead, we're providing abstractions that are compatible with the
implementations provided by Symfony. This should actually also contribute
positively to the PHP-FIG (of which Symfony is a member), by hinting the group
at some abstractions the PHP world might like to take inspiration from.

### Why isn't this package split into several packages?

Putting all interfaces in one package eases discoverability and dependency
management. Instead of dealing with a myriad of small packages and the
corresponding matrix of versions, you just need to deal with one package and one
version. Also when using IDE autocompletion or just reading the source code, it
makes it easier to figure out which contracts are provided.

There are two downsides to this approach: you may have unused files in your
`vendor/` directory, and in the future, it will be impossible to use two
different sub-namespaces in different major versions of the package. For the
"unused files" downside, it has no practical consequences: their file sizes are
very small, and there is no performance overhead at all since they are never
loaded. For major versions, this package follows the Symfony BC + deprecation
policies, with an additional restriction to never remove deprecated interfaces.

Resources
---------

  * [Documentation](https://symfony.com/doc/current/components/contracts.html)
  * [Contributing](https://symfony.com/doc/current/contributing/index.html)
  * [Report issues](https://github.com/symfony/symfony/issues) and
    [send Pull Requests](https://github.com/symfony/symfony/pulls)
    in the [main Symfony repository](https://github.com/symfony/symfony)
