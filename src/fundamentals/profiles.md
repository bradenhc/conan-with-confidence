# Conan Profiles

Profiles are just plain text files that group together related settings and
options. Typically profile files live under the `.conan2/profiles` directory.
Their primary objective is to enable users to apply a configuration set to
multiple builds without needing to list them explicitly from the command line or
in your recipe every time.

> **Location of Files Used by the Conan Client**  
> TODO

In addition to allowing you to specify settings and options, profiles also allow
you to set configuration for the tools you use and even specify some tooling
dependency if you choose to let Conan handle that for you as well.

## A Simple Profile

The following snippet shows a simple default profile:

```text
[settings]
arch=x86_64
build_type=Release
compiler=gcc
compiler.cppstd=gnu17
compiler.libcxx=libstdc++11
compiler.version=11
os=Linux
```
