Changelog
=========

1.1.1 (2023-09-14)
------------------

Bug fixes

* Fix attempt of emitting OpenLineage events if task execution fails by @tatiana in #526
* Fix Rust dependency for Windows users by @tatiana in #526
* Fix DbtRunOperationLocalOperator missing flags by @tatiana in #529
* Fix DbtRunLocalOperator to support the full refresh argument by @tatiana in #529
* Remove redundant prefix of task names when test_behavior = TestBehavior.AFTER_EACH by @binhnq94 in #524
* Fix rendering vars in ``DbtModel`` when using ``LoadMode.CUSTOM`` by @dojinkimm in #502

Others

* Docs: add `documentation comparing Airflow and dbt concepts <https://astronomer.github.io/astronomer-cosmos/getting_started/dbt-airflow-concepts.html>`_ by @tatiana in #523.
* Update PyPI project links by @tatiana in #528
* pre-commit updates


1.1.0 (2023-09-06)
------------------

Features

* Support dbt global flags (via dbt_cmd_global_flags in operator_args) by @tatiana in #469
* Support parsing DAGs when there are no connections by @jlaneve in #489

Enhancements

* Hide sensitive field when using BigQuery keyfile_dict profile mapping by @jbandoro in #471
* Consistent Airflow Dataset URIs, inlets and outlets with `Openlineage package <https://pypi.org/project/openlineage-integration-common/>`_ by @tatiana in #485. `Read more <https://astronomer.github.io/astronomer-cosmos/configuration/lineage.html>`_.
* Refactor ``LoadMethod.DBT_LS`` to run from a temporary directory with symbolic links by @tatiana in #488
* Run ``dbt deps`` when using ``LoadMethod.DBT_LS`` by @DanMawdsleyBA in #481
* Update Cosmos log color to purple by @harels in #494
* Change operators to log ``dbt`` commands output as opposed to recording to XCom by @tatiana in #513

Bug fixes

* Fix bug on select node add exclude selector subset ids logic by @jensenity in #463
* Refactor dbt ls to run from a temporary directory, to avoid Read-only file system errors during DAG parsing, by @tatiana in #414
* Fix profile_config arg in DbtKubernetesBaseOperator by @david-mag in #505
* Fix SnowflakePrivateKeyPemProfileMapping private_key reference by @nacpacheco in #501
* Fix incorrect temporary directory creation in VirtualenvOperator init by @tatiana in #500
* Fix log propagation issue by @tatiana in #498
* Fix PostgresUserPasswordProfileMapping to retrieve port from connection by @jlneve in #511

Others

* Docs: Fix RenderConfig load argument by @jbandoro in #466
* Enable CI integration tests from external forks by @tatiana in #458
* Improve CI tests runtime by @tatiana in #457
* Change CI to run coverage after tests pass by @tatiana in #461
* Fix forks code revision in code coverage by @tatiana in #472
* [pre-commit.ci] pre-commit autoupdate by @pre-commit-ci in #467
* Drop support to Python 3.7 in the CI test matrix by @harels in #490
* Add Airflow 2.7 to the CI test matrix by @tatiana in #487
* Add MyPy type checks to CI since we exceeded pre-commit disk quota usage by @tatiana in #510

1.0.5 (2023-08-09)
------------------

Enhancements

* Improve logs to include astornomer-cosmos identifier by @tatiana in #450
* Support OAuth authentication for Big Query by @MonideepDe in #431

Bug fixes

* Fix selector for config tags by @javihernovoa in #441
* Fix BigQuery keyfile_dict mapping for connection created from webserver UI by @jbandoro in #449

Others

* [pre-commit.ci] pre-commit autoupdate by @pre-commit-ci in #446
* Resolve MyPy errors when adding Airflow pre-commit dependency by @abhi12mohan in #434


1.0.0 (2022-12-14)
-------------------

* Initial release, with the following **6** workflow Operators/Parsers:

.. list-table::
   :header-rows: 1

   * - Operator/Sensor Class
     - Import Path
     - Example DAG

   * - ``DBTTestOperator``
     - .. code-block:: python

        from cosmos.providers.dbt.core.operators import DBTBaseOperator
     - N/A

   * - ``DBTSeedOperator``
     - .. code-block:: python

        from cosmos.providers.dbt.core.operators import DBTSeedOperator
     - `Example DAG <https://github.com/astronomer/astronomer-cosmos/blob/1.0.0/examples/dags/extract_dag.py>`__

   * - ``DBTRunOperator``
     - .. code-block:: python

        from cosmos.providers.dbt.core.operators import DBTRunOperator
     - N/A

   * - ``DBTTestOperator``
     - .. code-block:: python

        from cosmos.providers.dbt.core.operators import DBTTestOperator
     - N/A

   * - ``DbtDag``
     - .. code-block:: python

        from cosmos.providers.dbt.core.dag import DbtDag
     - `Example DAG <https://github.com/astronomer/astronomer-cosmos/blob/1.0.0/examples/dags/attribution-playbook.py>`__

   * - ``DbtTaskGroup``
     - .. code-block:: python

        from cosmos.providers.dbt.core.dag import DbtTaskGroup
     - `Example DAG <https://github.com/astronomer/astronomer-cosmos/blob/1.0.0/examples/dags/jaffle_shop.py>`__
