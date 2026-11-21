# SMC Editor Windows dependencies

This repository builds versioned vcpkg binary-cache packages for SMC Editor.
The package includes the full Windows static dependency graph and host tools,
not just Graphviz. Debug and Release libraries are both included.

Run the **Build dependencies** workflow with an immutable SMC Editor commit
and a new release tag. The workflow builds from that commit's manifest and
overlay port, checks cache-only restoration on a separate runner, builds the
editor and runs the Graphviz layout tests before publishing a release.

The archive contains `cache/` (vcpkg's ABI-keyed binary packages),
`licenses/` and `metadata.txt`. Its SHA-256 is published separately. Consumers
must pin both the release and the checksum in their own repository. The vcpkg
baseline, overlay, triplets and MSVC environment must match; regenerate and
re-pin the package when they change.
