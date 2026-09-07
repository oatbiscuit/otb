# otb
oatbiscuit's toolbox for image organisation.

## installation
### quick install (single user)
```sh
# download the script
curl -o ~/.local/bin/otb https://raw.githubusercontent.com/oatbiscuit/otb/main/otb
chmod +x ~/.local/bin/otb

# Make sure ~/.local/bin is in your PATH
# Add this to your ~/.bashrc or ~/.zshrc if not already:
export PATH="$HOME/.local/bin:$PATH"
```

### system-wide install
```
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
cp otb ~/.local/bin/  # or /usr/local/bin/
```

### verify installation
```sh
otb --version
# should output: otb <version>
```

### uninstallation
```sh
# Remove the script
rm ~/.local/bin/otb   # or /usr/local/bin/otb

# Optional: Remove data file
rm -rf ~/.local/share/otb/
```
