<!-- markdownlint-disable MD024 -->
# Changelog

## 3.2.1 (2023-04-10)

### Changed

- [#198](https://github.com/Masterminds/semver/issues/198):
  Improved testing around pre-release names
- [#200](https://github.com/Masterminds/semver/issues/200):
  Improved code scanning with addition of CodeQL
- [#201](https://github.com/Masterminds/semver/issues/201):
  Testing now includes Go 1.20. Go 1.17 has been dropped
- [#202](https://github.com/Masterminds/semver/issues/202):
  Migrated Fuzz testing to Go built-in Fuzzing. CI runs daily
- [#203](https://github.com/Masterminds/semver/issues/203):
  Docs updated for security details

### Fixed

- [#199](https://github.com/Masterminds/semver/issues/199):
  Fixed issue with range transformations

## 3.2.0 (2022-11-28)

### Added

- [#190](https://github.com/Masterminds/semver/issues/190):
  Added text marshaling and unmarshaling
- [#167](https://github.com/Masterminds/semver/issues/167):
  Added JSON marshalling for constraints (thanks @SimonTheLeg)
- [#173](https://github.com/Masterminds/semver/issues/173):
  Implement encoding.TextMarshaler
  and encoding.TextUnmarshaler on Version (thanks @MarkRosemaker)
- [#179](https://github.com/Masterminds/semver/issues/179):
  Added New() version constructor (thanks @kazhuravlev)

### Changed

- [#182](https://github.com/Masterminds/semver/issues/182)/
  [#183](https://github.com/Masterminds/semver/issues/183):
  Updated CI testing setup

### Fixed

- [#186](https://github.com/Masterminds/semver/issues/186):
  Fixing issue where validation of constraint section gave false positives
- [#176](https://github.com/Masterminds/semver/issues/176):
  Fix constraints check with *-0 (thanks @mtt0)
- [#181](https://github.com/Masterminds/semver/issues/181):
  Fixed Caret operator (^) gives unexpected results
  when the minor version in constraint is 0 (thanks @arshchimni)
- [#161](https://github.com/Masterminds/semver/issues/161):
  Fixed godoc (thanks @afirth)

## 3.1.1 (2020-11-23)

### Fixed

- [#158](https://github.com/Masterminds/semver/issues/158):
  Fixed issue with generated regex operation order that could cause problem

## 3.1.0 (2020-04-15)

### Added

- [#131](https://github.com/Masterminds/semver/issues/131):
  Add support for serializing/deserializing SQL (thanks @ryancurrah)

### Changed

- [#148](https://github.com/Masterminds/semver/issues/148):
  More accurate validation messages on constraints

## 3.0.3 (2019-12-13)

### Fixed

- [#141](https://github.com/Masterminds/semver/issues/141):
  Fixed issue with <= comparison

## 3.0.2 (2019-11-14)

### Fixed

- [#134](https://github.com/Masterminds/semver/issues/134):
  Fixed broken constraint checking with ^0.0 (thanks @krmichelos)

## 3.0.1 (2019-09-13)

### Fixed

- [#125](https://github.com/Masterminds/semver/issues/125):
  Fixes issue with module path for v3

## 3.0.0 (2019-09-12)

This is a major release of the semver package which includes API changes. The Go
API is compatible with ^1. The Go API was not changed because many people are using
`go get` without Go modules for their applications and API breaking changes cause
errors which we have or would need to support.

The changes in this release are the handling based on the data passed into the
functions. These are described in the added and changed sections below.

### Added

- StrictNewVersion function. This is similar to NewVersion but will return an
  error if the version passed in is not a strict semantic version. For example,
  1.2.3 would pass but v1.2.3 or 1.2 would fail because they are not strictly
  speaking semantic versions. This function is faster, performs fewer operations,
  and uses fewer allocations than NewVersion.
- Fuzzing has been performed on NewVersion, StrictNewVersion, and NewConstraint.
  The Makefile contains the operations used. For more information on you can start
  on Wikipedia at <https://en.wikipedia.org/wiki/Fuzzing>
- Now using Go modules

### Changed

- NewVersion has proper prerelease and metadata validation with error messages
  to signal an issue with either of them
- ^ now operates using a similar set of rules to npm/js and Rust/Cargo. If the
  version is >=1 the ^ ranges works the same as v1. For major versions of 0 the
  rules have changed. The minor version is treated as the stable version unless
  a patch is specified and then it is equivalent to =. One difference from npm/js
  is that prereleases there are only to a specific version (e.g. 1.2.3).
  Prereleases here look over multiple versions and follow semantic version
  ordering rules. This pattern now follows along with the expected and requested
  handling of this packaged by numerous users.

## 1.5.0 (2019-09-11)

### Added

- [#103](https://github.com/Masterminds/semver/issues/103):
  Add basic fuzzing for `NewVersion()` (thanks @jesse-c)

### Changed

- [#82](https://github.com/Masterminds/semver/issues/82):
  Clarify wildcard meaning in range constraints and update tests for it (thanks @greysteil)
- [#83](https://github.com/Masterminds/semver/issues/83):
  Clarify caret operator range for pre-1.0.0 dependencies (thanks @greysteil)
- [#72](https://github.com/Masterminds/semver/issues/72):
  Adding docs comment pointing to vert for a cli
- [#71](https://github.com/Masterminds/semver/issues/71):
  Update the docs on pre-release comparator handling
- [#89](https://github.com/Masterminds/semver/issues/89):
  Test with new go versions (thanks @thedevsaddam)
- [#87](https://github.com/Masterminds/semver/issues/87):
  Added $ to ValidPrerelease for better validation (thanks @jeremycarroll)

### Fixed

- [#78](https://github.com/Masterminds/semver/issues/78):
  Fix unchecked error in example code (thanks @ravron)
- [#70](https://github.com/Masterminds/semver/issues/70):
  Fix the handling of pre-releases and the 0.0.0 release edge case
- [#97](https://github.com/Masterminds/semver/issues/97):
  Fixed copyright file for proper display on GitHub
- [#107](https://github.com/Masterminds/semver/issues/107):
  Fix handling prerelease when sorting alphanum and num
- [#109](https://github.com/Masterminds/semver/issues/109):
  Fixed where Validate sometimes returns wrong message on error

## 1.4.2 (2018-04-10)

### Changed

- [#72](https://github.com/Masterminds/semver/issues/72):
  Updated the docs to point to vert for a console appliaction
- [#71](https://github.com/Masterminds/semver/issues/71):
  Update the docs on pre-release comparator handling

### Fixed

- [#70](https://github.com/Masterminds/semver/issues/70):
  Fix the handling of pre-releases and the 0.0.0 release edge case

## 1.4.1 (2018-04-02)

### Fixed

- Fixed [#64](https://github.com/Masterminds/semver/issues/64):
  Fix pre-release precedence issue (thanks @uudashr)

## 1.4.0 (2017-10-04)

### Changed

- [#61](https://github.com/Masterminds/semver/issues/61):
  Update NewVersion to parse ints with a 64bit int size (thanks @zknill)

## 1.3.1 (2017-07-10)

### Fixed

- Fixed [#57](https://github.com/Masterminds/semver/issues/57):
  number comparisons in prerelease sometimes inaccurate

## 1.3.0 (2017-05-02)

### Added

- [#45](https://github.com/Masterminds/semver/issues/45):
  Added json (un)marshaling support (thanks @mh-cbon)
- Stability marker. See <https://wfscheper.github.io/stability/>

### Fixed

- [#51](https://github.com/Masterminds/semver/issues/51):
  Fix handling of single digit tilde constraint (thanks @dgodd)

### Changed

- [#55](https://github.com/Masterminds/semver/issues/55):
  The godoc icon moved from png to svg

## 1.2.3 (2017-04-03)

### Fixed

- [#46](https://github.com/Masterminds/semver/issues/46):
  Fixed 0.x.x and 0.0.x in constraints being treated as *

## Release 1.2.2 (2016-12-13)

### Fixed

- [#34](https://github.com/Masterminds/semver/issues/34):
  Fixed issue where hyphen range was not working with pre-release parsing.

## Release 1.2.1 (2016-11-28)

### Fixed

- [#24](https://github.com/Masterminds/semver/issues/24):
  Fixed edge case issue where constraint "> 0" does not handle "0.0.1-alpha" properly.

## Release 1.2.0 (2016-11-04)

### Added

- [#20](https://github.com/Masterminds/semver/issues/20):
  Added MustParse function for versions (thanks @adamreese)
- [#15](https://github.com/Masterminds/semver/issues/15):
  Added increment methods on versions (thanks @mh-cbon)

### Fixed

- Issue [#21](https://github.com/Masterminds/semver/issues/21):
  Per the SemVer spec (section 9) a pre-release is unstable and
  might not satisfy the intended compatibility. The change here ignores pre-releases
  on constraint checks (e.g., ~ or ^) when a pre-release is not part of the
  constraint. For example, `^1.2.3` will ignore pre-releases while
  `^1.2.3-alpha` will include them.

## Release 1.1.1 (2016-06-30)

### Changed

- Issue [#9](https://github.com/Masterminds/semver/issues/9):
  Speed up version comparison performance (thanks @sdboyer)
- Issue [#8](https://github.com/Masterminds/semver/issues/8):
  Added benchmarks (thanks @sdboyer)
- Updated Go Report Card URL to new location
- Updated Readme to add code snippet formatting (thanks @mh-cbon)
- Updating tagging to v[SemVer] structure for compatibility with other tools.

## Release 1.1.0 (2016-03-11)

- Issue [#2](https://github.com/Masterminds/semver/issues/2):
  Implemented validation to provide reasons a versions failed a
  constraint.

## Release 1.0.1 (2015-12-31)

- Fixed [#1](https://github.com/Masterminds/semver/issues/1):
  - constraint failing on valid versions.

## Release 1.0.0 (2015-10-20)

- Initial release
