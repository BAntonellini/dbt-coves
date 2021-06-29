
dbt-coves
*********

|Maintenance| |PyPI version fury.io| |Code Style| |Checked with mypy| |Imports: isort| |Imports: python| |Build| |pre-commit.ci status| |codecov| |Maintainability| |Downloads|

.. |Maintenance| image:: https://img.shields.io/badge/Maintained%3F-yes-green.svg
   :target: https://github.com/datacoves/dbt-coves/graphs/commit-activity

.. |PyPI version fury.io| image:: https://badge.fury.io/py/dbt-coves.svg
   :target: https://pypi.python.org/pypi/dbt-coves/

.. |Code Style| image:: https://img.shields.io/badge/code%20style-black-000000.svg
   :target: https://github.com/ambv/black

.. |Checked with mypy| image:: http://www.mypy-lang.org/static/mypy_badge.svg
   :target: http://mypy-lang.org

.. |Imports: isort| image:: https://img.shields.io/badge/%20imports-isort-%231674b1?style=flat&labelColor=ef8336
   :target: https://pycqa.github.io/isort/

.. |Imports: python| image:: https://img.shields.io/badge/python-3.8%20%7C%203.9-blue
   :target: https://img.shields.io/badge/python-3.8%20%7C%203.9-blue

.. |Build| image:: https://github.com/datacoves/dbt-coves/actions/workflows/main_ci.yml/badge.svg
   :target: https://github.com/datacoves/dbt-coves/actions/workflows/main_ci.yml/badge.svg

.. |pre-commit.ci status| image:: https://results.pre-commit.ci/badge/github/bitpicky/dbt-coves/main.svg
   :target: https://results.pre-commit.ci/latest/github/datacoves/dbt-coves/main

.. |codecov| image:: https://codecov.io/gh/datacoves/dbt-coves/branch/main/graph/badge.svg?token=JB0E0LZDW1
   :target: https://codecov.io/gh/datacoves/dbt-coves

.. |Maintainability| image:: https://api.codeclimate.com/v1/badges/1e6a887de605ef8e0eca/maintainability
   :target: https://codeclimate.com/github/datacoves/dbt-coves/maintainability

.. |Downloads| image:: https://pepy.tech/badge/dbt-coves
   :target: https://pepy.tech/project/dbt-coves

What is dbt-coves?
==================

dbt-coves is a complimentary CLI tool for `dbt <https://www.getdbt.com>`_ that allows users to quickly apply `Analytics Engineering <https://www.getdbt.com/what-is-analytics-engineering/>`_ best practices.

⚠️ **dbt-coves is in alpha version, don’t use on your prod models unless you have tested it in a safe place before.**

Here's the tool in action
-------------------------

.. image:: https://cdn.loom.com/sessions/thumbnails/74062cf71cbe4898805ca508ea2d9455-1624905546029-with-play.gif
   :target: https://www.loom.com/share/74062cf71cbe4898805ca508ea2d9455

Supported dbt versions
**********************

+----------------------------------------------------+----------------------------------------------------+
| Version                                            | Status                                             |
+====================================================+====================================================+
| 0.17.0                                             | 🕥 In progress                                      |
+----------------------------------------------------+----------------------------------------------------+
| 0.18.2                                             | 🕥 In progress                                      |
+----------------------------------------------------+----------------------------------------------------+
| 0.19.1                                             | ✅ Tested                                           |
+----------------------------------------------------+----------------------------------------------------+
| 0.20.0                                             | ❌ Not tested                                       |
+----------------------------------------------------+----------------------------------------------------+


Supported adapters
******************

+----------------------+----------------------+----------------------+----------------------+----------------------+
| Feature              | Snowflake            | Redshift             | BigQuery             | Postgres             |
+======================+======================+======================+======================+======================+
| profile.yml          | ✅ Tested             | ❌ Not tested         | ❌ Not tested         | ❌ Not tested         |
+----------------------+----------------------+----------------------+----------------------+----------------------+
| sources generation   | ✅ Tested             | ❌ Not tested         | ❌ Not tested         | ❌ Not tested         |
+----------------------+----------------------+----------------------+----------------------+----------------------+


Installation
************

.. code:: console

   pip install dbt-coves


Main Features
*************


Project initialization
======================

.. code:: console

   dbt-coves init

Initializes a new ready-to-use dbt project that includes recommended
integrations such as `sqlfluff
<https://github.com/sqlfluff/sqlfluff>`_, `pre-commit
<https://pre-commit.com/>`_, dbt packages, among others.

Uses a `cookiecutter <https://github.com/datacoves/cookiecutter-dbt>`_
template to make it easier to maintain.


Models generation
=================

.. code:: console

   dbt-coves generate <resource>

Where *<resource>* could be *sources*.

Code generation tool to easily generate models and model properties
based on configuration and existing data.

Supports `Jinja <https://jinja.palletsprojects.com/>`_ templates to
adjust how the resources are generated.


Quality Assurance
=================

.. code:: console

   dbt-coves check

Runs a set of checks in your local environment to ensure high quality
data.

Checks can be extended by implementing `pre-commit hooks
<https://pre-commit.com/#creating-new-hooks>`_.


CLI Reference
*************

CLI tool for dbt users applying analytics engineering best practices.

::

   usage: dbt_coves [-h] [-v] {init,generate,check,fix} ...


Named Arguments
===============

-v, --version

show program’s version number and exit


dbt-coves commands
==================

task

Possible choices: init, generate, check, fix


Sub-commands:
=============


init
----

Initializes a new dbt project using predefined conventions.

::

   dbt_coves init [-h] [--log-level LOG_LEVEL] [-vv] [--config-path CONFIG_PATH] [--project-dir PROJECT_DIR] [--profiles-dir PROFILES_DIR] [--profile PROFILE] [-t TARGET] [--vars VARS] [--template TEMPLATE]


Named Arguments
~~~~~~~~~~~~~~~

--log-level

overrides default log level

Default: “”

-vv, --verbose

When provided the length of the tracebacks will not be truncated.

Default: False

--config-path

Full path to .dbt_coves file if not using default.

--project-dir

Which directory to look in for the dbt_project.yml file. Default is
the current working directory and its parents.

--profiles-dir

Which directory to look in for the profiles.yml file.Default =
~/.dbt

Default: “~/.dbt”

--profile

Which profile to load. Overrides setting in dbt_project.yml.

-t, --target

Which target to load for the given profile

--vars

Supply variables to the project. This argument overrides variables
defined in your dbt_project.yml file. This argument should be a YAML
string, eg. ‘{my_variable: my_value}’

Default: “{}”

--template

Cookiecutter template github url, i.e.
‘https://github.com/datacoves/cookiecutter-dbt-coves.git’


generate
--------

Generates sources and models with defaults.

::

   dbt_coves generate [-h] [--log-level LOG_LEVEL] [-vv] [--config-path CONFIG_PATH] [--project-dir PROJECT_DIR] [--profiles-dir PROFILES_DIR] [--profile PROFILE] [-t TARGET] [--vars VARS] {sources} ...


Named Arguments
~~~~~~~~~~~~~~~

--log-level

overrides default log level

Default: “”

-vv, --verbose

When provided the length of the tracebacks will not be truncated.

Default: False

--config-path

Full path to .dbt_coves file if not using default.

--project-dir

Which directory to look in for the dbt_project.yml file. Default is
the current working directory and its parents.

--profiles-dir

Which directory to look in for the profiles.yml file.Default =
~/.dbt

Default: “~/.dbt”

--profile

Which profile to load. Overrides setting in dbt_project.yml.

-t, --target

Which target to load for the given profile

--vars

Supply variables to the project. This argument overrides variables
defined in your dbt_project.yml file. This argument should be a YAML
string, eg. ‘{my_variable: my_value}’

Default: “{}”


dbt-coves generate commands
~~~~~~~~~~~~~~~~~~~~~~~~~~~

task

Possible choices: sources


Sub-commands:
~~~~~~~~~~~~~


sources
"""""""

Generate source dbt models by inspecting the database schemas and
relations.

::

   dbt_coves generate sources [-h] [--log-level LOG_LEVEL] [-vv] [--config-path CONFIG_PATH] [--project-dir PROJECT_DIR] [--profiles-dir PROFILES_DIR] [--profile PROFILE] [-t TARGET] [--vars VARS] [--schemas SCHEMAS]
                              [--destination DESTINATION] [--model_props_strategy MODEL_PROPS_STRATEGY] [--templates_folder TEMPLATES_FOLDER]


Named Arguments
+++++++++++++++

--log-level

overrides default log level

Default: “”

-vv, --verbose

When provided the length of the tracebacks will not be truncated.

Default: False

--config-path

Full path to .dbt_coves file if not using default.

--project-dir

Which directory to look in for the dbt_project.yml file. Default is
the current working directory and its parents.

--profiles-dir

Which directory to look in for the profiles.yml file.Default =
~/.dbt

Default: “~/.dbt”

--profile

Which profile to load. Overrides setting in dbt_project.yml.

-t, --target

Which target to load for the given profile

--vars

Supply variables to the project. This argument overrides variables
defined in your dbt_project.yml file. This argument should be a YAML
string, eg. ‘{my_variable: my_value}’

Default: “{}”

--schemas

Comma separated list of schemas where raw data resides, i.e.
‘RAW_SALESFORCE,RAW_HUBSPOT’

--destination

Where models sql files will be generated, i.e.
‘models/{schema_name}/{relation_name}.sql’

--model_props_strategy

Strategy for model properties files generation, i.e.
‘one_file_per_model’

--templates_folder

Folder with jinja templates that override default sources generation
templates, i.e. ‘templates’


check
-----

Runs pre-commit hooks and linters.

::

   dbt_coves check [-h] [--log-level LOG_LEVEL] [-vv] [--config-path CONFIG_PATH] [--project-dir PROJECT_DIR] [--profiles-dir PROFILES_DIR] [--profile PROFILE] [-t TARGET] [--vars VARS] [--no-fix]


Named Arguments
~~~~~~~~~~~~~~~

--log-level

overrides default log level

Default: “”

-vv, --verbose

When provided the length of the tracebacks will not be truncated.

Default: False

--config-path

Full path to .dbt_coves file if not using default.

--project-dir

Which directory to look in for the dbt_project.yml file. Default is
the current working directory and its parents.

--profiles-dir

Which directory to look in for the profiles.yml file.Default =
~/.dbt

Default: “~/.dbt”

--profile

Which profile to load. Overrides setting in dbt_project.yml.

-t, --target

Which target to load for the given profile

--vars

Supply variables to the project. This argument overrides variables
defined in your dbt_project.yml file. This argument should be a YAML
string, eg. ‘{my_variable: my_value}’

Default: “{}”

--no-fix

Do not suggest auto-fixing linting errors. Useful when running this
command on CI jobs.

Default: False


fix
---

Runs linter fixes.

::

   dbt_coves fix [-h] [--log-level LOG_LEVEL] [-vv] [--config-path CONFIG_PATH] [--project-dir PROJECT_DIR] [--profiles-dir PROFILES_DIR] [--profile PROFILE] [-t TARGET] [--vars VARS]


Named Arguments
~~~~~~~~~~~~~~~

--log-level

overrides default log level

Default: “”

-vv, --verbose

When provided the length of the tracebacks will not be truncated.

Default: False

--config-path

Full path to .dbt_coves file if not using default.

--project-dir

Which directory to look in for the dbt_project.yml file. Default is
the current working directory and its parents.

--profiles-dir

Which directory to look in for the profiles.yml file.Default =
~/.dbt

Default: “~/.dbt”

--profile

Which profile to load. Overrides setting in dbt_project.yml.

-t, --target

Which target to load for the given profile

--vars

Supply variables to the project. This argument overrides variables
defined in your dbt_project.yml file. This argument should be a YAML
string, eg. ‘{my_variable: my_value}’

Default: “{}”

Select one of the available sub-commands with –help to find out more
about them.


Thanks
******

The project main structure was inspired by `dbt-sugar
<https://github.com/bitpicky/dbt-sugar>`_. Special thanks to `Bastien
Boutonnet <https://github.com/bastienboutonnet>`_ for the great work
done.


Authors
*******

*  Sebastian Sassi `@sebasuy <https://twitter.com/sebasuy>`_ –
   `Convexa <https://convexa.ai>`_

*  Noel Gomez `@noel_g <https://twitter.com/noel_g>`_ – `Ninecoves
   <https://ninecoves.com>`_


About
*****

Learn more about `Datacoves <https://datacoves.com>`_.
