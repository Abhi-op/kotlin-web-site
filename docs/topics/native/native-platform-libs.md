[//]: # (title: Platform libraries)

To provide access to user's native operating system services,
Kotlin/Native distribution includes a set of prebuilt libraries specific to
each target. We call them **Platform Libraries**.

### POSIX bindings

For all Unix- or Windows-based targets (including Android and
iOS targets) we provide the `POSIX` platform lib. It contains bindings
to platform's implementation of the [POSIX standard](https://en.wikipedia.org/wiki/POSIX).

To use the library, just import it: 

```kotlin
import platform.posix.*
```

The only target for which it is not available is [WebAssembly](https://en.wikipedia.org/wiki/WebAssembly).

Note that the content of `platform.posix` is NOT identical on
different platforms, in the same way as different `POSIX` implementations
are a little different.

### Popular native libraries

There are many more platform libraries available for host and
cross-compilation targets.  Kotlin/Native distribution provides access to
OpenGL, zlib and other popular native libraries on
applicable platforms.

On Apple platforms, `objc` library is provided for interoperability with [Objective-C](https://en.wikipedia.org/wiki/Objective-C).

Inspect the contents of `dist/klib/platform/$target` of the distribution for the details.

## Availability by default

The packages from platform libraries are available by default. No
special link flags need to be specified to use them. Kotlin/Native
compiler automatically detects which of the platform libraries have
been accessed and automatically links the needed libraries.

On the other hand, the platform libs in the distribution are merely
just wrappers and bindings to the native libraries.  That means the
native libraries themselves (`.so`, `.a`, `.dylib`, `.dll` etc)
should be installed on the machine.
