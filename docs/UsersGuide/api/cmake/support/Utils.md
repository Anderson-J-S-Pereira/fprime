**Note:** auto-generated from comments in: ./support/Utils.cmake

## Utils.cmake:

Defines needed utility functions that are (or should be) independent of any autocoding calls to
be made. Those files should go in *AC_Utils.cmake*.


## Function `get_nearest_build_root`:

Finds the nearest build root from ${FPRIME_BUILD_LOCATIONS} that is a parent of DIRECTORY_PATH.

- **DIRECTORY_PATH:** path to detect nearest build root
Return: nearest parent from ${FPRIME_BUILD_LOCATIONS}


## Function `get_module_name`:

Takes a path, or something path-like and returns the module's name. This breaks down as the
following:

 1. If passed a path, the module name is the '_'ed variant of the relative path from BUILD_ROOT
 2. If passes something which does not exist on the file system, it is just '_'ed

i.e. ${BUILD_ROOT}/Svc/ActiveLogger becomes Svc_ActiveLogger
     Svc/ActiveLogger also becomes Svc_ActiveLogger

- **DIRECTORY_PATH:** path to infer MODULE_NAME from
- **Return: MODULE_NAME** (set in parent scope)


## Function `add_generated_sources`:

Add generated file as sources for the given target. This function specifically adds
these sources as generated, so that regardless of where they appear (source or build tree)
they will be known as generated

- **CPP_SOURCE:** source .cpp file to add
- **HPP_SOURCE:** source .hpp file to add
- **MODULE_NAME:** (inherited from parent) name of the module to add generated sources too


## Function `fprime_ai_info`:

A function used to detect all the needed information for an Ai.xml file. This looks for the following items:
 1. Type of object defined inside: Component, Port, Enum, Serializable, TopologyApp
 2. All fprime module dependencies that may be auto-detected
 3. All file dependencies

- **XML_PATH:** full path to the XML used for sources.
- **MODULE_NAME:** name of the module soliciting new dependencies


## Function `split_source_files`:

Split SOURCE_FILE_INPUTS into the autocoder and source variants, supplied to the calling function.

- **SOURCE_FILE_INPUTS**: input file list to be split up.
- **Return: AUTOCODER_INPUT_FILES** (set in parent scope)
- **Return: SOURCE_FILES** (set in parent scope)


## Function `split_dependencies`:

Split DEPS_INPUT into the module and link variants, supplied to the calling function.

- **DEPS_INPUT**: dependencies list to be split up.
- **Return: LINK_DEPS** (set in parent scope)
- **Return: MOD_DEPS** (set in parent scope)


## Function `set_hash_flag`:

Adds a -DASSERT_FILE_ID=(First 8 digits of MD5) to each source file, and records the output in
hashes.txt. This allows for asserts on file ID not string.


## Function `print_dependencies`:

Prints the dependency list of the module supplied as well as the include directories.

- **MODULE_NAME**: module name to print dependencies
