# git-shadow-config

Apply git config fragments to local repositories.


## Example

### Change git user config for each local repsitory

* Put `git-shadow-config` script in a suitable place.

* Add aliases for `git-shadow-config`.

  .gitconfig
  ```
  [alias]
    set-shadow-config = !path/to/git-shadow-config copy-to-local
    show-shadow-config = !path/to/git-shadow-config show
    list-shadow-config = !path/to/git-shadow-config list
  ```

* Disable guessed defaults for `user.email` and `user.name` .

  .gitconfig
  ```
  [user]
    useconfigonly = true
  ```

* Make a directory named `.gitconfig.shadow.d` under the `$HOME` (or `$USERPROFILE` on Windows .)

* Put a file in `.gitconfig.shadow.d` and add git config gragments to it.  
  For example,

  default
  ```
  [user]
    email = myname@local
    name = myname
  ```

  anon
  ```
  [user]
    email = anonymous@local
    name = anonymous
  ```

* Run `git list-shadow-config` to get the list of the names of git config gragments

* Run `git show-shadow-config [<git-config-fragment-name>]` to show the content of the git config fragment.
    - If `<git-config-fragment-name>` is not suppllied, `default` is used.

* Run `git set-shadow-config [<git-config-fragment-name>]` inside a git repository to apply the content of the git config fragment to the repository. 
    - If `<git-config-fragment-name>` is not suppllied, `default` is used.


## License

MIT License
