# Exercism TRACK_NAME_HERE Representer

The Docker image to automatically create a representation for TRACK_NAME_HERE solutions submitted to [Exercism].

## Getting started

Build the representer, conforming to the [Representer interface specification](https://github.com/exercism/docs/blob/main/building/tooling/representers/interface.md).
Update the files to match your track's needs. At the very least, you'll need to update `bin/run.sh`, `Dockerfile` and the test solutions in the `tests` directory.
The existing test solutions are suggestions for you could be testing, but remember to add your track-specific files too

- Tip: look for `TODO:` comments to point you towards code that need updating
- Tip: look for `OPTIONAL:` comments to point you towards code that _could_ be useful

### Default Implementation

The default implementation should work as follows:

- The `representation.txt` contains the concatenated solution files
  - Solution files are separated by an empty line
  - Solution files are identified via the the `.files.solution[]` property in the `.meta/config.json` file
- The `mapping.json` contains an empty JSON object (`{}`)

#### Normalizations

- Blank files in the solution files are removed in the `representation.txt`
- Line-based trailing whitespace in the solution files is removed in the `representation.txt`

## Run the representer

To create a representation for a single solution, do the following:

1. Open a terminal in the project's root
2. Run `./bin/run.sh <exercise-slug> <solution-dir> <output-dir>`

Once the representer has finished, its results will be written to `<output-dir>/representation.txt` and `<output-dir>/mapping.json`.

## Run the representer on a solution using Docker

_This script is provided for testing purposes, as it mimics how representers run in Exercism's production environment._

To create a representation for a single solution using the Docker image, do the following:

1. Open a terminal in the project's root
2. Run `./bin/run-in-docker.sh <exercise-slug> <solution-dir> <output-dir>`

Once the representer has finished, its results will be written to `<output-dir>/representation.txt` and `<output-dir>/mapping.json`.

## Run the tests

To run the tests to verify the behavior of the representer, do the following:

1. Open a terminal in the project's root
2. Run `./bin/run-tests.sh`

These are [golden tests][golden] that compare the `representation.txt` and `mapping.json` generated by running the current state of the code against the "known good" `tests/<test-name>/representation.txt` and `tests/<test-name>/mapping.json`. All files created during the test run itself are discarded.

When you've made modifications to the code that will result in a new "golden" state, you'll need to generate and commit a new `tests/<test-name>/representation.txt` and `tests/<test-name>/mapping.json` file.

## Run the tests using Docker

_This script is provided for testing purposes, as it mimics how representers run in Exercism's production environment._

To run the tests to verify the behavior of the representer using the Docker image, do the following:

1. Open a terminal in the project's root
2. Run `./bin/run-tests-in-docker.sh`

These are [golden tests][golden] that compare the `representation.txt` and `mapping.json` generated by running the current state of the code against the "known good" `tests/<test-name>/representation.txt` and `tests/<test-name>/mapping.json`. All files created during the test run itself are discarded.

When you've made modifications to the code that will result in a new "golden" state, you'll need to generate and commit a new `tests/<test-name>/representation.txt` and `tests/<test-name>/mapping.json` file.

[representers]: https://github.com/exercism/docs/tree/main/building/tooling/representers
[golden]: https://ro-che.info/articles/2017-12-04-golden-tests
[exercism]: https://exercism.io
