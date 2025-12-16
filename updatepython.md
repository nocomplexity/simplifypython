# Update Python Version using Conda

If you are using `conda` and wish to update your Python version (be it a major, minor, or patch release), follow these instructions.

## Updating Python in a `conda` Environment 


Major or Minor Version Update/UpgradeTo update to a specific **major or minor** version, for example, moving from Python 3.13 to 3.14, use the following command. `conda` will find the latest available patch release for that specific version (e.g., 3.14.x) and update your environment.

1. **Activate** the `conda` environment you wish to modify.
2. Run the installation command, specifying the desired version:

```bash
conda install python=3.14 

```

> **Note:** For security, it is highly recommended to keep your Python version up to date unless there is a specific, well-justified reason not to do so.



## Patch Version Update (Within the Same Minor Version)

If you have, for instance, Python 3.13.2 installed and only want to update to the latest patch release (e.g., 3.13.5), but do **not** want to upgrade to a newer minor version (like 3.14):

1. **Activate** the `conda` environment you wish to update.
2. Within this environment, run the installation command, specifying the currently installed minor version:

```bash
conda install python=3.13 

```

This will update your Python version to the latest 3.13.x release available in the `conda` channels, ensuring you remain on the 3.13 minor branch.

---

## Alternative

Using `conda update`Another option for general updates is the `update` command. If you simply want to update the Python version within your active environment to the latest available version without specifying a number (often useful for patch updates):

```bash
conda update python

```
