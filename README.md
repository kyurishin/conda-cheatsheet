# Conda Cheatsheet

## Quick Start
Tip: It is recommended to create a new environment for any new project or workflow.
| Fuction                                   | Command                               |
|:---------------------------------------|:-----------------------------------|
| verify conda install and check version | conda info      |
| update conda in base environment       | conda update -n base conda  |
| install latest anaconda distribution (see [release notes](https://docs.anaconda.com/navigator/release-notes/)) | conda install anaconda=**2022.05**  |
|create a new environment (tip: *name environment descriptively*) | conda create --name **ENVNAME**  |
| activate environment (do this before installing packages)  | conda activate **ENVNAME** |

## Channels and Packages
### Tip: Package dependencies and platform specifics are automatically resolved when using conda. 
| Fuction                                   | Command                               |
|:---------------------------------------|:-----------------------------------|
| list installed packages | conda list | 
| list installed packages with source info | conda list --show-channel-urls |
| update all packages | conda update --all |
| install a package from specific channel | conda install -c **CHANNELNAME PKG1 PKG2** |
| install specific version of package | conda install **PKGNAME**=**3.1.4** |
| install a package from specific channel | conda install **CHANNELNAME**::**PKGNAME** |
| install package with AND logic | conda install “**PKGNAME**>**2.5**,<**3.2**” |
| install package with OR logic | conda install “**PKGNAME** [version=’**2.5**|**3.2**’]” |
| uninstall package | conda uninstall **PKGNAME** |
| view channel sources | conda config --show-sources |
| add channel | conda config --add channels **CHANNELNAME** |
| set default channel for pkg fetching (targets first channel in channel sources) | conda config --set channel_priority strict |

## Working with Conda Environments
Tip:  List environments at the beginning of your session. Environments with an asterisk are active.
| Fuction                                   | Command                               |
|:---------------------------------------|:-----------------------------------|
| list all environments and locations | conda env list |
| list all packages + source channels | conda list -n **ENVNAME** --show-channel-urls |
| install packages in environment | conda install -n **ENVNAME** **PKG1** **PKG2** |
| remove package from environment | conda uninstall **PKGNAME** -n **ENVNAME** |
| update all packages in environment | conda update --all -n **ENVNAME** |

## Environment Management
Tip: Specifying the environment name confines conda commands to that environment.
| Fuction                                   | Command                               |
|:---------------------------------------|:-----------------------------------|
| create environment with Python version | conda create -n **ENVNAME** python=**3.10** |
| clone environment | conda create --clone **ENVNAME** -n **NEWENV** |
| rename environment | conda rename -n **ENVNAME** **NEWENVNAME** |
| delete environment by name | conda remove -n **ENVNAME** --all |
| list revisions made to environment | conda list -n **ENVNAME** --revisions |
| restore environment to a revision | conda install -n **ENVNAME** --revision NUMBER |
| uninstall package from specific channel | conda remove -n **ENVNAME** -c **CHANNELNAME** **PKGNAME** |

## Exporting Environments
Tip: Recommendation: Name the export file “environment.” Environment name will be preserved.
| Fuction                                   | Command                               |
|:---------------------------------------|:-----------------------------------|
| cross-platform compatible | conda env export --from-history>**ENV**.yml |
| platform + package specific | conda env export **ENVNAME**>**ENV**.yml |
| platform + package + channel specific | conda list --explicit>**ENV**.txt |

## Importing Environments
Tip: When importing an environment, conda resolves platform and package specifics
| Fuction                                   | Command                               |
|:---------------------------------------|:-----------------------------------|
| from a .yml file | conda env create -n **ENVNAME** --file **ENV**.yml |
| from a .txt file | conda create -n **ENVNAME** --file **ENV**.txt |

## Additional Hints
| Fuction                                   | Command                               |
|:---------------------------------------|:-----------------------------------|
| get help for any command | conda **COMMAND** --help |
| get info for any package | conda search **PKGNAME** --info |
| run commands w/o user prompt <br /> eg, installing multiple packages | conda **COMMAND** **ARG** --yes <br /> conda install **PKG1** **PKG2** --yes |
| remove all unused files | conda clean --all |
| examine conda configuration | conda config --show |
