ocp-find
========

Bridge between ocp-build and ocamlfind

### ocp-findlib

    ocp-finlib lwt > lwt.ocp

This will builds `lwt.ocp`, which contains enough information to
build a project using the `lwt` library (which should have been
previously installed by ocamlfind)

The script takes only 1 paramater, which should be exactly the name of
the ocamlfind package.

To use `lwt.ocp`, just include the file in your project and scan the
working directory of your project with `ocp-build -scan. You can then
use `"lwt"` in the `requires` field of any `.ocp` files in your project.

### ocp-findpp

    ocp-findpp my_pp lwt.syntax cow.syntax > pp.ocp

This will build `pp.ocp`, which contains enough information to
preprocess a file using the syntax extensions defined in the package
`lwt` and `cow`.

The script takes as parameters:

* the name of the pre-processor (you will use that name the `.ocp`
  files in your project)
* the list of syntax extensions to take into account

To use `pp.ocp`, just include the file in your project and scan the
working directory of your project using `ocp-build -scan`. You can
then write `use "my_pp"` in the scope of one of your libraries to use
the preprocessor to compile the library.

### ocp-findppo, ocp-findppr

Same behavior as ocp-findpp, we it uses `camlp4o` (or `camlp4r)
instead of `camlp4` as base pre-processor.

