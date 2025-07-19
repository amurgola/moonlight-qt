# GitHub Actions Workflows

This repository includes GitHub Actions workflows for automated building and testing.

## build-windows.yml

This workflow automatically builds Windows executables (.exe) for the Moonlight PC client.

### Triggers
- **Push to main/master**: Builds and uploads artifacts for development testing
- **Pull Requests**: Validates that the build works with proposed changes  
- **Releases**: Builds and automatically attaches release assets
- **Manual trigger**: Can be run manually from the Actions tab

### Build Matrix
- **Architectures**: x64, ARM64
- **Configuration**: Release

### Artifacts
For each build, the workflow produces:
- `MoonlightPortable-{arch}-Release.zip` - Portable executable package
- `MoonlightDebuggingSymbols-{arch}-Release.zip` - Debug symbols (when available)

### Release Integration
When a new release is published on GitHub, this workflow automatically:
1. Builds Windows executables for both x64 and ARM64
2. Uploads the portable packages and debug symbols as release assets
3. Makes them available for download alongside the release

This provides the same Windows build capabilities as the existing AppVeyor setup, but integrated directly with GitHub's infrastructure for faster feedback and easier access to build artifacts.