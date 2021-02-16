![License: CC-BY](https://img.shields.io/badge/licence-CC--BY-green.svg)
[![Open Source Love](https://badges.frapsoft.com/os/v1/open-source.svg?v=103)](https://github.com/ellerbrock/open-source-badges/)

# tfc-campa-epigraphy
DHARMA project Task Force C, Campa epigraphic corpus. Some files have be reused from the [Corpus of the Inscriptions of Campā](https://isaw.nyu.edu/publications/inscriptions/campa/index.html).
For more information, see the [website description](https://dharma.hypotheses.org/task-forces).

## Help and Guides
* A Guide for Git is provided in the [project documentation repository](https://github.com/erc-dharma/project-documentation) at [DHARMA_Git_guide_v01.md](https://github.com/erc-dharma/project-documentation/blob/master/guides/git/DHARMA_git_guide_v01.md)
* DHARMA encoding guide is available under [encoding-diplomatic](https://github.com/erc-dharma/project-documentation/tree/master/guides/encoding-diplomatic), but we recommend you to use the [google doc version](https://docs.google.com/document/d/1hjWrrwRZQp4hmEqw4jBhhqoXdwJvRlw3EWboJteOPw0/edit?usp=sharing) to access the latest edits.
* Encoding templates are also provided under [templates](https://github.com/erc-dharma/project-documentation/tree/master/templates)
* Feel free to use issues to ask questions to other members of the project. To Get started with issue, see the  [guide](https://github.com/erc-dharma/project-documentation/tree/master/guides/github-issuetracker).

## Validation
All DHARMA XML are validated against Epidoc schema in its latest version as well as against DHARMA ones.
You can declare those schemas in the processing instructions of every XML files. To use it with Oxygen, you might need to change the default configuration.
In the toolbar, go to the `Options > Preferences`, a window will open, select `XML > XML Parser > RelaxNG`. The check box for "Add default attributes values" must be unchecked. Click on Apply. You might need to restart Oxygen for it to be taken into account.

* DHARMA validation schemas
  - a RelaxNG with embedded Schematron code is available [here](https://github.com/erc-dharma/project-documentation/blob/master/schema/latest/DHARMA_Schema.rng).
  - a Schematron with embedded Schematron Quick Fixes to complete the first schema is available [here](https://github.com/erc-dharma/project-documentation/blob/master/schema/latest/DHARMA_Schema.rng)

*Note that both schemas are needed to a complete validation of DHARMA encoding rules*

If you use an online validation processing, the processing instructions should be as followed
```
<?xml-model href="http://www.stoa.org/epidoc/schema/latest/tei-epidoc.rng" schematypens="http://relaxng.org/ns/structure/1.0"?>
<?xml-model href="http://www.stoa.org/epidoc/schema/latest/tei-epidoc.rng" schematypens="http://purl.oclc.org/dsdl/schematron"?>
<?xml-model href="https://raw.githubusercontent.com/erc-dharma/project-documentation/master/schema/latest/DHARMA_Schema.rng" type="application/xml" schematypens="http://relaxng.org/ns/structure/1.0"?>
<?xml-model href="https://raw.githubusercontent.com/erc-dharma/project-documentation/master/schema/latest/DHARMA_Schema.rng" type="application/xml" schematypens="http://purl.oclc.org/dsdl/schematron"?>
<?xml-model href="https://raw.githubusercontent.com/erc-dharma/project-documentation/master/schema/latest/DHARMA_SQF.sch" type="application/xml" schematypens="http://purl.oclc.org/dsdl/schematron"?>

```
However, if you need to do it locally, you can access all DHARMA RelexNG and Schematron in their latest version in the projection-documentation repository under [schema/latest](https://github.com/erc-dharma/project-documentation/tree/master/schema/latest). In this case, you will need to update the `@href` and provide the path between you current file and the schema itself (either as a standalone file or either as a part of the project-documentation repository if you have cloned it)

## Workflow
- Before working with this repository, make sure you always the latest version through a `git pull`
- Create a XML file or edit an existing one.
- Once, you are done use git to add, commit and push it on the repository.
- Once you have done your `git push`, the XML files are validated against the Epidoc and Dharma RelaxNG with a CI service called Travis. This process is made possible with the existing `.travis.yml` file. **Do not delete not modify this file on your own.** You can access the resulting log [here](https://travis-ci.com/github/erc-dharma/tfc-campa-epigraphy)
- On the `git push`, we are also using github Actions service to transforme automatically the XML into a HTML version. We are using Ant in a java environment to do this batch transformation. The steps are declare in the `build.xml file`, while the automated scenario is provided under `.github/workflows/editorial.yml` **Do not delete not modify those files on your own.**
  - Step 1: it will editorially edit all the XMLs in the repository.
  - Step 2: from those edited XMLs, it will create a HTML output and retrieve Zotero data as well.
  - Step 3: it will push those files in the repository under `editedxml` and `htmloutput` folders.
  - Step 4: to access those newly created files, make a `git pull`

  *Please note that this process can break easily and requires high quality data*. The content log of the pipeline are available under [Actions tab](https://github.com/erc-dharma/tfc-campa-epigraphy/actions) of the repository, if you need to find the reason behind an error.

![DHARMA XML workflow](https://github.com/erc-dharma/project-documentation/blob/master/guides/images/DHARMA_XMLWorkflow_v01.png)

## License & Attribution
All the edited XML files of this repository are available under the [Creative Commons CC-BY 4.0 License](https://creativecommons.org/licenses/by/4.0/), meaning you are free to use it for any purpose, commercial or non-commercial! However, we ask you to mention the project name, funder as well as the members involved in the XML edition of the inscriptions. Feel free to contact the project for more infos at `ercdharma@gmail.com`.

## Contributing to this repository
**Thanks for your interest in contributing!** Currently only members of the project are allowed to contribute to this repository. Contact the researchers in charge of this corpus if you are interested in working with them.
