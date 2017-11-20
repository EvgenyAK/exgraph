=======
ExGraph
=======

Описание
=========

.. code-block:: python

    import exgraph

    graph = """
    MY_BIN:
        type: process

        on_start: on_start.sh
        on_finish: on_finish.sh

        exec: bin.sh

        config-path:
            config.yaml

        options:
            some-option: value

        execution:
            type: process
            execute:
                $EXEC -c $CONFIG -d

    pipeline:
        - name: single_bin
        exec:
            $MY_BIN

        - name: double_bin
        exec:
            $MY_BIN; $MY_BIN

        - name: double_bin
        exec:
            $MY_BIN || $MY_BIN

        - name: double_bin
        exec:
            $MY_BIN && $MY_BIN
    """

    exgraph.execute(config)
