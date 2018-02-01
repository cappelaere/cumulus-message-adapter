# Cumulus Message Adapter

[![CircleCI](https://circleci.com/gh/cumulus-nasa/cumulus-message-adapter.svg?style=svg)](https://circleci.com/gh/cumulus-nasa/cumulus-message-adapter)

## Releases

CircleCI manages releases and release assets.

Whenever CircleCI passes on the master branch of cumulus-message-adapter and `message_adapter/version.py` has a new version, CircleCI will:

* Create a new tag with `tag_name` of the string in `message_adapter/version.py`
* Create a new release off the new new tag, with name equal to `tag_name` (equal to version).
* Build a `cumulus-message-adapter.zip` file and attach it as a release asset to the newly created release. The zip file is created using the [`Makefile`]('./Makefile') in the root of this repository.

These steps are fully detailed in the [`.circleci/config.yml`](./.circleci/config.yml) file.

## Development

### Dependency Installation

    $ pip install -r requirements-dev.txt
    $ pip install -r requirements.txt

### Running Tests

Running tests requires [localstack](https://github.com/localstack/localstack).

Tests only require localstack running S3, which can be initiated with the following command:

```
$ SERVICES=s3 localstack start
```

And then you can check tests pass with the following nosetests command:

```
$ CUMULUS_ENV=testing nosetests -v -s
```

### Linting

     $ pylint message

### Contributing

If changes are made to the codebase, you can create the cumulus-message-adapter zip archive for testing libraries that require it:

```bash
$ make clean
$ make cumulus-message-adapter.zip
```

Then you can run some integration tests:

```bash
./examples/example-node-message-adapter-lib.js 
```
