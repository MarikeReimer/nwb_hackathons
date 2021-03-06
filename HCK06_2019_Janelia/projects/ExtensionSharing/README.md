[:rewind: Back to the projects list](../../README.md#ProjectsList)

<!-- For information on how to write GitHub .md files see https://guides.github.com/features/mastering-markdown/ -->

# Sharing NWB:N Extensions

## Key Investigators

- Oliver Ruebel
- Ryan Ly
- Andrew Tritt
- Ben Dichter
- Jean-Christophe Fillion-Robin

## Project Description

Develop methods for sharing NWB:N extensions.

## Objectives

- Evaluate plans for infrastructure for web-based sharing, deployment, and evaluation of extensions
- Begin implementation of the online archive for NWB:N extensions

## Approach and Plan

- Work with attendees to evaluate the current plan
- Implement draft template repo for extensions
- Implement draft template repo for extension recipes

## Progress and Next Steps

- Created GitHub organization to develop the NWB:N extensions catalog
- Created draft GitHub webpage for the extension catalog
- Created design documents for the extension catalog
- Created draft extension sharing and versioning guidelines
- Added continuous integration (using Azure-pipelines) to [NeurodataWithoutBorders/nwb-docutils](https://github.com/NeurodataWithoutBorders/nwb-docutils), [nwb-extensions/ndx-template](https://github.com/nwb-extensions/ndx-template) and  [NeurodataWithoutBorders/pynwb](https://github.com/NeurodataWithoutBorders/pynwb)
- Consolidated documentation of `ndx-template` with the one generated by `nwb-docutils`
- Reviewed conda-forge infrastructure and identified next step for enabling continuous-integration of [nwb-extensions/staged-extensions](https://github.com/nwb-extensions/staged-extensions)
- Discussed the flowchart for users creating and publishing their own extensions
  - Decided to simplify the initial creation of an extension using a web form
  - Decided that `version` needs to be required on YAML spec files, and now that [MatNWB cache spec issue](https://github.com/NeurodataWithoutBorders/matnwb/issues/42) has been fixed, `cache_spec` should default to True when writing an NWB file.
  - Users can download the YAML files and associated source code for an extension using `pip`, which can install from either PyPi or GitHub: e.g. `pip install git+https://github.com/org/project` (see https://pip.pypa.io/en/stable/reference/pip_install/#vcs-support). It would be nice to have also a utility function for downloading an extension, e.g. `pynwb-install-ext <extension_name>` and `matnwb_install_ext <extension_name>`, which would automatically look up the source for the extension on our catalog and download the YAML files and any associated source code from PyPi or GitHub into the local filesystem. 
  - When downloading an extension, decided against having the API modify the local environment with pointers to YAML spec files stored somewhere not obvious, like in a new hidden directory in the user's home directory.
- **Next steps**
  - Update `ndx-template` to include example of namespace file allowing the documentation to be successfully generated
  - Enable continuous integration for `staged-extensions` to support linting, style check, removal of staged extension and creating of extension repository.
  - Update pynwb to ensure extension schema is loaded after the extension is installed
  - Remaining discussion questions:
    - If a file was made with extension v1 and another file was made with extension v2, how can you load both specs at runtime, especially if they are incompatible? Only one spec of a given namespace can be loaded at any one time. For now, this is a rare use case, but in 5-10 years, this could present a serious problem.
    - What if a user has a custom, unpublished extension with the same namespace as an existing, published extension that has been cached in the file? API should throw an error and encourage the user to change the name of their extension. Not sure what happens now...

## Materials

- GitHub organization: [https://github.com/nwb-extensions](https://github.com/nwb-extensions)
- GitHub webpage for the NDX catalog: [https://nwb-extensions.github.io/](https://nwb-extensions.github.io/)


## Background and References

<!--Use this space for information that may help people better understand your project, like links to papers, source code, or data ,e.g:-->
<!-- - Source code: https://github.com/YourUser/YourRepository -->
<!-- - Documentation: https://link.to.docs -->
<!-- - Test data: https://link.to.test.data -->
