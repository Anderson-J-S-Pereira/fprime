**Note:** auto-generated from comments in: ./module-CMakeLists.txt.template

## Module 'CMakeLists.txt':

fprime modules setup source files, non-standard module dependencies, unit test source files, unit test module
dependencies, and call one of the following functions from the F prime API:

First define needed variables:

- `SOURCE_FILES:` combined list of source and autocoding files. Used by `register_fprime_module` and
  `register_fprime_executable` to provide source files.
- `MOD_DEPS:` (optional) module dependencies that cannot be auto-detected. Used by  `register_fprime_module` and
   `register_fprime_executable`.
- `EXECUTABLE_NAME`: (optional) override default executable name. Used by `register_fprime_executable`
- `UT_SOURCE_FILES`: (optional) specify sources for unit tests used with `register_fprime_ut`
- `UT_MOD_DEPS`: (optional) specify modules for unit tests used with `register_fprime_ut`

Once set, register fprime modules using:
- `register_fprime_module`: register a typical module/library
- `register_fprime_executable`: register an executable/deployment binary
- `register_fprime_ut`: register a unit test


See: [API](./API.md)

**Example:**
```
# Setup source files
set(SOURCE_FILES
  "${CMAKE_CURRENT_LIST_DIR}/CommandDispatcherComponentAi.xml"
  "${CMAKE_CURRENT_LIST_DIR}/CommandDispatcherImpl.cpp"
)

# Register the fprime module using above sources
register_fprime_module()

# Setup unit test source files
set(UT_SOURCE_FILES
  "${FPRIME_FRAMEWORK_PATH}/Svc/CmdDispatcher/CommandDispatcherComponentAi.xml"
  "${CMAKE_CURRENT_LIST_DIR}/test/ut/CommandDispatcherTester.cpp"
  "${CMAKE_CURRENT_LIST_DIR}/test/ut/CommandDispatcherImplTester.cpp"
)
# Register a unit test with above sources
register_fprime_ut()
```
