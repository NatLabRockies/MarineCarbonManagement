# MarineCarbonManagement
[![PyPI version](https://badge.fury.io/py/marine-carbon-management.svg)](https://badge.fury.io/py/marine-carbon-management)
![PyPI - Python Version](https://img.shields.io/pypi/pyversions/marine-carbon-management)
[![License](https://img.shields.io/badge/License-BSD%203--Clause-blue.svg)](https://opensource.org/licenses/BSD-3-Clause)
[![Link](https://img.shields.io/badge/Publication-Electrochemical_Direct_Ocean_Capture-brightgreen)](https://www.nrel.gov/docs/fy24osti/90673.pdf)
[![Static Badge](https://img.shields.io/badge/SWR-24--122-purple)](https://www.osti.gov/biblio/code-148916)

The marine carbon management software is an open-source Python based software that contains generic models for marine carbon capture. More models are under development and will be added soon. 

## Software requirements

- Python version 3.10+

## Installing Marine Carbon Management

### PyPI

```bash
pip install marine-carbon-management
```

### Source Installation

1. Using Git, navigate to a local target directory and clone repository:

    ```bash
    git clone https://github.com/NREL/MarineCarbonManagement.git
    ```

2. Navigate to `MarineCarbonManagement`

    ```bash
    cd MarineCarbonManagement
    ```

3. Create a new virtual environment and change to it. Using Conda and naming it 'mcm':

    ```bash
    conda create --name mcm python=3.11 -y
    conda activate mcm
    ```

4. Install MarineCarbonManagement and its dependencies:

    - If you want to just use MarineCarbonManagement:

       ```bash
       pip install .  
       ```

    - If you also want development dependencies for running tests:  

       ```bash
       pip install -e ".[develop]"
       ```

    - If you also want development dependencies for running tests:  

       ```bash
       pip install -e ".[examples]"
       ```

    - In one step, all dependencies can be installed as:

      ```bash
      pip install -e ".[all]"
      ```


7. Verify setup by running tests:

    ```bash
    pytest
    ```

## Release Notes

1. Ensure tests pass.
2. Ensure README is up to date with any updated information.
3. Ensure dependency and Python versions are up to date.
4. Ensure `CHANGELOG.md` is up to date.
5. Bump version in `mcm/__init__.py` using semantic versioning logic (https://semver.org/).
6. Make a pull request into the `main` branch from `develop` or a patch release branch.
   1. Merge `main` back into `develop`, if `develop` was not the base branch.
7. Tag the new release and push it.

    ```bash
    git tag -a v1.2.3 -m "message for v1.2.3"
    git push origin v1.2.3
    ```

    1. This will kick off the "Deploy to Test PyPI" GitHub action. If this aciton passes
      successfully, move onto the step 8. If the action failed, keep following these sub
      instructions.
    2. Delete the tag locally and on remote.

        ```bash
        git tag -d v1.2.3
        git push --delete origin v1.2.3
        ```

    3. Create a new branch off main, and fix whatever was broken in the build process.
    4. Return to step 5.
8. Create a new release at <https://github.com/NatLabRockies/MarineCarbonManagement/releases>,
  ensuring that:
   1. The newly created tag is selected, and
   2. "Generate release notes" is selected.

  This will kick off the "Deploy to PyPI" GitHub action, and should pass if the "Deploy to Test
  PyPI" action passed. In the rare instance that the "Deploy to PyPI" action fails, follow the steps
  starting at 6.2. Just note that the Test PyPI action will now fail, so there will not be a check
  to ensure publishing to PyPI should work.
