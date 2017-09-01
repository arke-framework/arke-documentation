# Installation process

## Binary process

1. Get the [binary package](Binary_package.md)
2. Extract file to local repository
3. Test existing files in local repository
    1. If exists (and not forced) end with error
    2. If exists and process forced, remove directory and continue
3. Check all file hash
    1. If hash differ from reference (and process not forced) rollback process

### Get the [binary package](Binary_package.md)

Which can get [binary package](Binary_package.md) directly with existinging file or on a remote repository.

#### From file

You can specify directly a package file.

```sh
> arke install MyPackage.arke
```

#### From remote repository

Usage:
```
# Install last version
> arke install MyPackage

# Install last version from serie 1.X.X
> arke install MyPackage --version 1.*.*

# Install specific version
> arke install MyPackage --version 1.2.3
```

1. Find package in repository database listing
    1. If the database or package doesn't exist download [repository index](remote/Repository_Index_file.md) at url *{repository}/arke/{version}/repository.json*
2. Download [package index](remote/Package_Index_file.md) containing versions and targets at url *{repository}/arke/{version}/{organization}/{name}/package.json*
3. If version doesn't exist end with error
4. If target exists
    1. Download it from *{repository}/arke/{version}/{organization}/{name}/{version}/package/{organization}_{name}_{os}-{arch}(-{variant}).arke* to *{arkeHome}/distfiles*
4. If target doesn't exist but there is buidable
    1. [Build](../build/Build_package.md) the package
5. In other cases exit with error
