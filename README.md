# Java Package Workflow

Used as the GitHub workflow by the services team for Java packages.

Example of how the main workflow can be used in a package (e.g. service-client) repository:  
```yaml
# .github/workflows/buildAndPublish.yaml
name: Build and Publish Java Package

on:
  workflow_dispatch:
  push:
    branches:
      - master
      - dev

jobs:
  build:
    uses: QActions/publish-java-package-workflow/.github/workflows/buildAndPublish.yaml@1.1.0
    secrets:
      GH_PACKAGES_FULL_READ_ACCESS_TOKEN: ${{ secrets.GH_PACKAGES_FULL_READ_ACCESS_TOKEN }}
```

Example of how the build only workflow can be used in a package repository for feature branches:
```yaml
# .github/workflows/build.yaml
name: Build Java Package

on:
  workflow_dispatch:
  push:
    branches-ignore:
      - master
      - dev

jobs:
  build:
    uses: QActions/publish-java-package-workflow/.github/workflows/build.yaml@1.1.0
    secrets:
      GH_PACKAGES_FULL_READ_ACCESS_TOKEN: ${{ secrets.GH_PACKAGES_FULL_READ_ACCESS_TOKEN }}
```

