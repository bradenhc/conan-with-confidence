# Conan Fundamentals

It's important to cover a few high-level concepts before we dive too deep into
using Conan. Experience has taught me that understanding these fundamental
principles helps flatten the learning curve and makes applying Conan properly a
more enjoyable experience.

In this chapter, we'll cover three topics: [Profiles](./profiles.md),
[Recipes](./recipes.md), and [Generators](./generators.md). Before we get to
these important topics, though, we'll spend time in this section talking more
about how each of these concepts relate to each other. Once we have a good
understanding of the high-level relationships, we'll dig deeper into the
specifics of each concept.

## Describing C/C++ Binaries

Remember from [Chapter 2](TODO) that one of the challenges with binary package
management is finding an effective way to describe how the package was built.
Conan approaches this by breaking down the types of information we need to
ensure binary compatability into three categories: settings, options, and
requirements.

### Settings Describe the System

Both the system and environment play an important role in binary package
creation. The system involves things like the operating system and the
architecture of the host machine (or even the target machine when
cross-compiling). The environment involves things like which compiler we're
using (e.g. Clang vs. GCC), whether we are building for debug or release, and
the C++ standard we are targetting (e.g. C++11 vs C++23).

### Options Describe the Features

Oftentimes we want the ability to build our C/C++ project with different sets of
features. For example, if we are building a library, we can provide both a
static and dynamic version of our library so end users can control linkage
themselves. We can use an option in Conan to control how we deliver our
artifacts in our packages.

We can also use options to control various sets of features we might include in
our library or application. For example, let's assume we are building a library
that provides a HTTP server. In a production context, we want to provide
encryption capabilities with our HTTP server. However, sometimes the extra
security can get in the way of early prototype development, so to help out this
subset of users, we could offer a version of our library that does not include
the encryption feature. We can use options in Conan to control our configuration
at this level.

### Requirements Describe the Dependencies

It's a rare thing to work on a project that is completely self-contained with no
dependencies on other libraries, external or internal to an organization.
Sometimes these dependencies are header-only libraries that are compiled
directly into our binary artifacts. Sometimes they are static or dynamic
libraries that will eventually be linked to a runnable application. Regardless
of the dependency format, the existance of the dependency itself is a key
component to uniquely identifying a package containing binary artifacts.

## Using Settings, Options, and Requirements

Conan takes settings, options, and requirements for a project and creates a hash
of the information to uniquely identify package configurations.

## Up Next: Profiles

Now that we know how settings, options, and requirements assist with uniquely
identifying Conan packages, let's take a look at a Conan feature that brings
these things together to create reusable configurations in the form of profiles.
