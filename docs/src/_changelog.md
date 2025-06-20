```@meta
CurrentModule = ZMQ
```

# Changelog

This documents notable changes in ZMQ.jl. The format is based on [Keep a
Changelog](https://keepachangelog.com).

## [v1.4.1] - 2025-06-13

### Changed
- Implemented `Base.show()` methods for [`Socket`](@ref) and [`Context`](@ref)
  for pretty-printing ([#255]).

### Fixed
- The precompilation workload now hardcodes the use of IP address `127.0.0.1`
  instead of resolving `localhost`, which fixes precompilation on machines that
  may have `localhost` resolve to a different node ([#257]).

## [v1.4.0] - 2024-11-30

### Added
- Implemented [`send_multipart()`](@ref) and [`recv_multipart()`](@ref) for
  working with multipart messages ([#253]).

## [v1.3.0] - 2024-08-03

### Added
- Support for creating [`Message`](@ref)'s from the new `Memory` type in Julia
  1.11 ([#244]).
- Full [Bindings](@ref) to libzmq ([#232]).

### Deprecated
- The `Base.convert(IOStream, ::Message)` method has been deprecated due to
  buggy behaviour, use `IOBuffer(msg)` instead ([#247]).

### Fixed
- Fixed [`isfreed()`](@ref), which would previously return the wrong values
  ([#245]).

## [v1.2.6] - 2024-06-13

### Added

- [`lib_version()`](@ref) to get the libzmq version ([#240]).

### Fixed

- Fixed a precompilation bug that would cause creating a sysimage with
  PackageCompiler.jl on Julia 1.6 to fail ([#242]).

## [v1.2.5] - 2024-05-28

### Fixed

- Fixed support for Julia 1.3 in the precompilation workload ([#237]).

## [v1.2.4] - 2024-05-27

### Changed

- Refactored the internals to use the public `FileWatching.FDWatcher` instead of
  `FileWatching._FDWatcher` ([#215]).

### Fixed

- Docstrings to inner constructors are now assigned properly ([#227]).
- [`Socket`](@ref) now holds a reference to its [`Context`](@ref) to prevent it from
  being garbage collected accidentally ([#229]).
- Changed the precompilation workload to use any available port to avoid port
  conflicts ([#234]).

## [v1.2.3] - 2024-05-12

### Added

- Support for setting `ZMQ_IMMEDIATE` and `ZMQ_CONFLATE` on sockets ([#209],
  [#222]).
- Overloads for [`Message`](@ref) to allow deserializing them with MsgPack.jl
  ([#214]).
- A precompilation workload to improve TTFX ([#224]).
