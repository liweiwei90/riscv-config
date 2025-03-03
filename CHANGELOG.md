# Changelog

This project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [2.11.0] - 2021-10-15
### Fixed
  - canonical ordering requirement of `_Z` extensions fixed
### Added
  - adding support for Zmmul extension in ISA regex

## [2.10.2] - 2021-10-06
### Fixed
  - islegal function under the warl_interpreter class fixed. The based and bound values are not
     extracted correctly as either hex or decimal values. Also removed the logic to truncate values

## [2.10.1] - 2021-08-26
### Fixed
   - Changed the default value of 'accessible' to false so input yamls need not declare unsupported xlen
   
   
## [2.10.0] - 2021-07-30
### Added
   - added default-setters for misa's reset value to match the ISA extensions, to modify warl function of extensions under misa
   - added default setter for reset value of mstatus
### Fixed
   - changed default values of types for subfields in mstatus 
   - changed default values of types for mhpmevent*, mcountinhibit, mcounteren and mhpmcounter* to read only constant 0
   - changed default values of types for fflags, frm and fcsr to warl if F is present, else read-only constant 0
   - changed default values of types for mcycle[h], minstret[h] to  warl
   - changed default values of types and added checks for subfields of scause, satp, stvec, sie, sip and sstatus
   
## [2.9.1] - 2021-06-02
### Fixed
- removed an unadded feature in rv32i_platform.yaml
- removed debug_interrupts under mip in rv64i_isa.yaml

## [2.9.0] - 2021-05-24
### Fixed
- fixed issue #58 by adding extra checks for bitmask
- fixed issue #59 by removing custom cause from platform yaml
- resolved inconsistencies in the use of "xlen" and "supported_xlen" in schemaValidator
### Added
- added extra "shadow_type" fields in the csr schemas. These indicate the nature of shadow
  (read-only, read-write, etc).
- added parking_loop node in debug_schema to indicate the address of debug rom. Can be empty in
  implementations which do not have this feature

## [2.8.0] - 2021-03-02
### Added
- Added checks for K (sub)extension(s) 
- Updated docs with information on adding new extension, csrs or specs.
- Added github actions based CI

## [2.7.0] - 2021-02-25
### Added
- added new debug schema for debug based csrs and spec
- cli now takes debug spec as input as well along with isa-spec
- added support for defining custom exceptions and interrupts

## [2.6.3] - 2021-01-19
### Fixed
- added priv_mode field to sedeleg and sideleg csrs

## [2.6.2] - 2021-01-18
### Fixed
- Allow B extension in ISA schema

## [2.6.1] - 2021-01-13
### Fixed
- msb,lsb values of "SD" field in mstatus must be 63 in rv64 mode
- added checks for reset value of misa to adhere to the extensions enabled in the input yaml
- fixed dead-link in the docs.

## [2.6.0] - 2021-01-5
### Added
- Added support for custom csr yaml
- Added new nodes in isa_schema: pmp_granularity and physical_addr_sz
- Checks for pmp, counters and custom csrs
- medeleg, mideleg check for S or N extension
- updated the warl syntax slightly for easier parsing.

### Changed
- fixed warl parsing and islegal function to check reset values 

## [2.5.1] - 2020-11-6
### Changed
- modified sn_check and su_check
- scounteren checks to make it depend only on u
- medeleg, mideleg check for S or N extension


## [2.5.0] - 2020-11-6
### Added
- added all n extension csrs
- added missing supervisor csrs
- added default setters for subfields in sip, sie , uip and uie to make it depend as shadows on machine csrs

## [2.4.1] - 2020-10-22
### Changed
- default mpp value to 0
- adding defaults to sub-fields of mtvec

## [2.4.0] - 2020-10-19
### Added
- Added support for pmp csrs in the schema
- Added support for mcycleh and minstreth
- Added special checks for ensuring the shadows are implemented correctly.
- Added support for the following supervisor csrs in the schema: sstatus, sie, sip, stvec, sepc, stval, scause and satp
- Added support for user performance counters, frm, fcsr, time[h], cycle[h] and instret[h] csrs in
  the schema.
### Changed
- all fields are now subsumed under a hartid. This allows specifying multiple harts in the same
  yaml
- logging mechanism improved.
- isa spec is now validated independently of the platform spec
- privilege and unprivilege version checks are no longer required. This satisfied via the
  "allowed" field now.
- improved the 'implemented/accessible' checks for s, u and n extensions
- the "fields" node is now populated by subfields in the increasing order of the placement in the
  csr.
- using aliases to reduce the code size

## [2.3.1] - 2020-10-6
### Changed
- Added Zihintpause to ISA string (for PAUSE Hint instruction extension)..

## [2.3.0] - 2020-07-27
### Changed
- Size of the isa schema has been reduced significantly.
- Using anchors in the schema.
- Provided a command line argument to disable anchors in the checked yaml dump.
- adding mycycle, minstret, pmpcfgs and pmpaddrs
- added support for defining multiple harts

## [2.2.2] - 2020-06-09
### Changed
- Changed quickstart 'riscv_config' to 'riscv-config'
- Changed checker.py to add check_reset_fill_fields() description

## [2.2.1] - 2020-05-18
### Changed
- Changed minimum python version requirement to 3.6.0 which is typically easy to install on all
  major distributions
- Updated readme with better installation instructions

## [2.2.0] - 2020-04-07
### Changed
- Renamed the 'implemented' field  in rv32 and rv64 nodes to 'accessible'.
- Modified appropriate definitions for fields dependent on specific extensions like NSU.

## [2.1.1] - 2020-03-29
## [Fixed
- doc issue for mtimecmp
- mimpid is now part of the default setters list

## [2.1.0] - 2020-03-29
## [Fixed
- Moved machine timer nodes to platform yaml.
## [Added
- `--version` option to arguments to print version and exit when specified.
- Print help and exit when no options/arguments are specified.

## [2.0.2] - 2020-03-28
### Fixed
- Redundant reset-val check for mtvec and misa registers.

## [2.0.1] - 2020-03-25
### Fixed
- typos in quickstart doc
- disabled deployment to repository until authentication issue is fixed.

## [2.0.0] - 2020-03-25
### Added
- adding support for warl fields and support
- documentation for the warl fields added
- reset-value checks added
### Changed
- using a new common template for defining all csrs
- updated docs with new template
- using special function within conf.py to extract comments from yaml file as docs.
### Fixed
- closed issues #10, #11, #12, #13

## [1.0.2] - 2019-08-09
### Changed
- Log is generated only if specified(for API calls to checker.check_specs).
### Fixed
- link in readme now points to github instead of gitlab.

## [1.0.0] - 2019-07-30
### Changed
- Work directory isnt deleted if the directory exists, although the files of the same name will be overwritten.
### Fixed
- Checked yaml passes validation too.

## [0.1.0] - 2019-07-29
### Added
- Added work_dir as arg and always outputs to that dir.
- Added reset vector and nmi vector to platform.yaml
- Vendor description fields in schema.
- An xlen field added for internal use.
### Fixed
- In ISA field in isa_specs subsequent 'Z' extensions should be prefixed by an underscore '_'
- Fixed `cerberus.validator.DocumentError: document is missing` error when platform specs is empty. 
- mtvec:mode max value is set to 1.
- privilege-spec and user-spec are taken as strings instead of float.
### Changed
- The representation of the int fields is preserved in the checked-yaml.
- mepc is a required field.
- check_specs function now returns the paths to the dumped normalized files.
- No other entries in node where implemented is False.
- Readonly fields are purged by default.
- Multiple values/entries for the same node is not allowed.
### Removed
- remove *_checked.yaml files from Examples.
- changed templates_platform.yaml to template_platform.yaml in docs.

## [0.0.3] - 2019-07-19
### Fixed
- doc update

## [0.0.2] - 2019-07-19
### Fixed
- pdf documentation
- ci-cd to host pdf as well

## [0.0.1] - 2019-07-18
### Added
- Documentation to install and use pyenv 

## [0.0.0] - 2019-07-18
### Added
- Initial schemas for M mode and S mode csrs with constraints as specified in the spec.
