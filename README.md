
1. Create virtual env

    `poetry install --extras=dev`

2. Activate venv

    1. Linux

        `source .venv/bin/activate`

    2. Windows

        `.venv\Scripts\activate`

3. Install dependencies

    `pip install .[dev]`

4. Install editable project

    `pip install --no-build-isolation --config-settings=editable-verbose=true -Cbuild-dir=".build_editable" --editable .`