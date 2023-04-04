# one-liners
A collection of useful one liners

## Finding an orphaned commit containing a specific string in a specific file

If you know you had introduced a specific string (e.g. `magic-string-to-locate`) to a specific file (e.g. `path/to/search`), you can run:

    for SHA in $(git reflog --all | awk '{print $1}'); do if git show $SHA -- path/to/search | grep magic-string-to-locate >/dev/null; then echo found in $SHA; fi; done
    
which will display any matching git shas.
