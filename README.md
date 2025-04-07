# WillGauvin.com
## A portfolio website showcasing all of the game development projects I (Will Gauvin) have worked on
Visit my [website](https://willgauvin.com), or run it localy by following the guide below.

### Local Hosting Setup

## Installing Ruby V2
Install Ruby [here](https://rubyinstaller.org/)

Run and install the program.

Once finished installing, a command window will open and give 3 options of downloading. Choose #3

Boom, Finished

## Installing Bundler
Using the console in the root of the project, run the command
```
gem install bundler
```
Next run the following
```
bundle install
```
Bundler is pretty good at letting you know what gems need updating, however depending on what gems you already have installed, you may have to run
```
bundle update
```
Finally, run
```
bundle exec jekyll serve
```
This will return you with an address to copy and paste in your preferred browser.
Any saved changes to your local version of the repository will now appear at the address given!


