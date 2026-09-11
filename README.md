# otb
oatbiscuit's toolbox is a lightweight file organiser for the terminal, with a focus on photos.

## why otb?
- **Lightweight**: ~900 lines of POSIX shell
- **Non-destructive**: metadata in XMP sidecars, originals untouched
- **Composable**: works with standard Unix tools
- **Photo-aware**: EXIF-aware import, XMP tags/ratings
- **General-purpose**: `import`, `dupes`, and `audit` work on any file type

## features
- import photos with date based organisation
- tag and rate images with XMP sidecars
- find and delete duplicates (based on file hash)
- verify library integrity

## dependencies
- `b3sum`: BLAKE3 hashing
- `exiftool`: metadata

Optional:
- `$EDITOR`: for `otb config` (defaults to `vi`)

## help menu
```sh
Usage: otb [OPTION] [COMMAND] [ARGUMENTS...]

Commands (short/long):
    i, import       [DIR]   Import files from a folder/media device.
    t, tag          [FILE]  Add/remove tags from images.
    r, rate         [FILE]  Rate images (1-5 stars).
    d, dupes        [DIR]   Find duplicate files.
    a, audit        [DIR]   Check integrity of file collection.
    v, version              Show version information.
    config                  Edit configuration file. 

Options:
    --target        [DIR]   Override root directory for this command.
    --template      [STR]   Override import template for this command.
    --dry-run               Show what would be done without executing.
    -d, --delete            Delete duplicates (dupes only).
    -v, --verbose           Show detailed output.
    -h, --help              Show this help message.
    -V, --version           Show version information.

Environment Variables:
    IMG_ROOT                Default file directory (default: $HOME/Pictures).
    IMPORT_TEMPLATE         Default import template (default: %Y/%m).
    EDITOR                  Editor for config/tag editing (default: vi).
```

## examples

```sh
# Import photos from a camera or download folder
otb import ~/Downloads/

# Tag a photo
otb tag -a sunset -a landscape photo.jpg

# Rate a photo
otb rate -s 4 photo.jpg

# Find duplicates
otb dupes

# Interactive delete of duplicates
otb dupes --delete

# Verify library integrity
otb audit

# Custom organization template
otb --template "%Y/%m/%d" import ~/Downloads/
```

## configuration

otb reads its config from `~/.config/otb/config` (XDG-compliant).

```sh
otb config   # opens the config in $EDITOR
```

## data files

otb stores its data in XDG-compliant locations:

- `~/.config/otb/config`: configuration
- `~/.local/share/otb/checksums`: file hashes
- `~/.local/share/otb/metadata`: tag/rating cache

## installation
### quick install (single user)
```sh
mkdir -p ~/.local/bin

# download the script
curl -o ~/.local/bin/otb https://raw.githubusercontent.com/oatbiscuit/otb/main/otb
chmod +x ~/.local/bin/otb

# Make sure ~/.local/bin is in your PATH
# Add this to your ~/.bashrc or ~/.zshrc if not already:
export PATH="$HOME/.local/bin:$PATH"
```

### system-wide install
```sh
# Install to /usr/local/bin (requires sudo)
sudo curl -o /usr/local/bin/otb https://raw.githubusercontent.com/oatbiscuit/otb/main/otb
sudo chmod +x /usr/local/bin/otb
```

### manual install
```sh
# Clone the repository or download the script
git clone https://github.com/oatbiscuit/otb.git
cd otb

# Make executable and copy to your PATH
chmod +x otb
mkdir -p ~/.local/bin
cp otb ~/.local/bin/  # or /usr/local/bin/
```

### verify installation
```sh
otb --version
# should output:
-> otb 0.1.0
-> Copyright (c) 2026 oatbiscuit
-> License GPL-3.0-or-later
```

### uninstallation
```sh
# Remove the script
rm ~/.local/bin/otb   # or /usr/local/bin/otb

# Optional: Remove data file
rm -rf ~/.local/share/otb/
```

## license

GPL-3.0-or-later. See [COPYING](https://github.com/oatbiscuit/otb/blob/main/COPYING) for details.
