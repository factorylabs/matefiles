
# F/ TextMate Configuration

The default configuration for installed Bundles, Plugins and Themes set directly to `~/Library/Application\ Support/TextMate`. If you have to roll with TextMate, roll with this, but highly recommend switching to Vim.


## Installation Notes

Since you are over writing existing directories, it's probably a good idea to check and make any necessary backups before diving in.

Link your TextMate directory to the `github` repository:

    cd ~/Library/Application\ Support/TextMate/
    git init
    git remote add origin git@github.com:factorylabs/matefiles.git
    git fetch
    git branch master origin/master
    git checkout master
    git submodule init
    git submodule update


Before you move on, fire up TextMate and go to `Preferences -> Advanced -> Shell Variables` and fill in a few variables this installation is looking for.

    PATH :: Whatever lives in your environment path (type echo $PATH in Terminal and paste in here)
    TM_GIT :: /usr/local/bin/git
    TM_RUBY :: /Users/<username>/.rvm/bin/textmate_ruby

*Don't forget this step!*


## Updating

From time to time, it's necessary to update the settings from the F/ repository and the submodules. There is a shell script `update.sh` included to ease the pain.


### Updating From The F/ Repository

To update from the latest changes in the F/ repository run the following:

1. Quit out of TextMate
- `git stash` or `git add` any updates from your environment
- `git pull --rebase`

Commit your changes back up to the repository.


### Updating Submodules

To pull upstream changes for all of the submodules run the following:

1. Quit out of TextMate
- `bash update.sh`
- `git stash` or `git add` any updates from your environment
- `git pull --rebase`

Commit your changes back up to the repository. F/ will run this script once in awhile to keep the submodules as up to date as possible.


## Bundles

`~/Library/Application\ Support/TextMate/Bundles`  
`~/Library/Application\ Support/TextMate/Pristine\ Copy/Bundles`

The `Bundles` directory take precedence over the `Pristine Copy/Bundles` directory in the eyes of TextMate. We use `Pristine Copy/Bundles` as a storage area for `git submodules` to the original maintainer. Any changes you make within TextMate's Bundle editor will make a copy into the `Bundle` directory of the changes made, then inherit the rest from `Pristine Copy/Bundles`. This allows you to have some customization with the ability to pull any upstream changes in. Go view the [default bundles](https://github.com/factorylabs/matefiles/tree/master/Pristine%20Copy/Bundles) we start it off with.

## Plug-ins
    
There are a couple of plugins enabled by default.

- [AckMate][AckMate]
- [ProjectPlus][ProjectPlus]


## Editor Themes

Themes included with this configuration:

1. `colorblind`: Black background, super vibrant colors
- `snowblind`: White background, vibrant colors
- `cataracts`: Grey background with muted colors
- `bloodshot`: Similar to colorblind but with muted colors

The color themes have been designed with similarities in the syntax settings. Jumping between multiple languages should be easy on the mind and the eyes. Be adventurous and mix it up once in a while.

**Most themes use the custom [MesloGM font](https://github.com/andreberg/Meslo-Font). Download, install and live the dream.**


## Submodules ##

A few notes for future reference about working with `git submodules` taken from [cheat sheets][cheat-sheets].

### Adding Submodules: ###

    git submodule add <remote_repository> <path/to/submodule>
    git submodule init
    git submodule update

### Updating Submodules ###

    git submodule foreach <command>


### Removing Submodules ###

   1. Delete the relevant line from the `.gitmodules` file
   2. Delete the relevant section from `.git/config`
   3. Run `git rm --cached path_to_submodule` (no trailing slash)


## License and Contributions ##

All licensing for the Bundles should be found on their respective repositories. This repo is only a means to quickly install and track a TextMate configuration. While contributions are welcome, you're probably better off forking and tuning it to your own machine. Better yet switch to Vim.

[AckMate]: http://github.com/protocool/AckMate
[ProjectPlus]: http://ciaranwal.sh/category/textmate
[cheat-sheets]: http://cheat.errtheblog.com/s/git

