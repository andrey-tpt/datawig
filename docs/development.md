# Developer Documentation

## Requirements



There are three types of dependencies: core dependencies, development dependencies and dependencies for generating the documentation.

Install them via

```bash
> pip install -r requirements/requirements.txt
> pip install -r requirements/requirements.dev.txt
> pip install -r requirements/requirements.docs.txt
```


## Developer Guidelines

We welcome contributions to DataWig in form of pull requests on Github.
If you want to develop sockeye, please adhere to the following development guidelines.


 * Write Python3, PEP8 compatible code.

 * Functions should be documented with Sphinx-style docstrings and
   should include type hints for static code analyzers.

    ```python
    def foo(bar: <type of bar>) -> <returnType>:
        """
        <Docstring for foo method, followed by a period>.

        :param bar: <Description of bar argument followed by a period>.
        :return: <Description of the return value followed by a period>.
        """
    ```

 * The desired line length of Python modules should not exceed 120 characters.

 * Make sure to pass unit tests before submitting a pull request.

 * Whenever reasonable, write py.test unit tests covering your contribution.

## Building the Documentation
Full documentation, including a code reference, can be generated using Sphinx with the following command:

```bash
> python setup.py docs
```
The results are written to ```docs/_build/html/index.html```.


## Unit & Integration Tests
Unit & integration tests are written using py.test.
They can be run in a venv setup in the root dir of the package as follows:

```bash
> ./venv/bin/python -m pytest
```

## Code of Conduct
This project has adopted the [Amazon Open Source Code of Conduct](https://aws.github.io/code-of-conduct).
For more information see the [Code of Conduct FAQ](https://aws.github.io/code-of-conduct-faq) or contact
opensource-codeofconduct@amazon.com with any additional questions or comments.


## Licensing

See the [LICENSE](https://github.com/awslabs/datawig/blob/master/LICENSE) file for our project's licensing. We will ask you confirm the licensing of your contribution.

We may ask you to sign a [Contributor License Agreement (CLA)](http://en.wikipedia.org/wiki/Contributor_License_Agreement) for larger changes.