# Bin Tools

Bin tools are various tools I've written to handle my day to day. 

## Lemon

Lemon is a wrapper so that files can be stored in Dropbox or another cloud program.  It creates a memory disk and encrypts and decrypts to/from the memory volume. 

The password is a hash created in `~/.lemon_password`. Be sure to back that up, as without it all of your lemon files are unavailable. 

Here is the Automator code: 

``` bash
#!/bin/bash
set -euo pipefail

LEMON="/Users/[user-user]/.local/bin/lemon"  # absolute path to lemon bash file as Automator doesn't reliably expand "~". I put ~/.local/bin in my PATH.

if [ "$#" -eq 0 ]; then
  echo "No arguments received"
  exit 64
fi

for f in "$@"; do
  "$LEMON" "$f"
done
```

Save the Automator script to your /Application/ directory. Use "Get Info" in the finder to associate .enc files with .enc

### Optionality

Consider changing the extension to `.lenc` instead of `.enc` for lemon encryption versus other encryption processes you might be using.  
