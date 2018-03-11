powerline-installation
======================

##### Update 11/03/2018

Install patched fonts for Powerline
```
sudo apt-get install fonts-powerline
```

Install Powerline with Python PIP

```
sudo pip install powerline-shell
```

Add Powerline Prompt to .bashrc

```
function _update_ps1() {
    PS1=$(powerline-shell $?)
}

if [[ $TERM != linux && ! $PROMPT_COMMAND =~ _update_ps1 ]]; then
    PROMPT_COMMAND="_update_ps1; $PROMPT_COMMAND"
fi
```

##### Bonus: Fix VSCode terminal Powerline

In User Settings add:
```
"terminal.integrated.fontFamily": "'xx for Powerline'"
```
Replace xx with your default font, i.e:

``` Inconsolata for Powerline ```


### Powerline Shell Installation procedure
### Step by step powerline installation on Linux Mint (Ubuntu)

#### Installing powerline fonts (user wide)

	wget https://github.com/Lokaltog/powerline/raw/develop/font/PowerlineSymbols.otf https://github.com/Lokaltog/powerline/raw/develop/font/10-powerline-symbols.conf
	mkdir -p ~/.fonts/ && mv PowerlineSymbols.otf ~/.fonts/
	fc-cache -vf ~/.fonts
	mkdir -p ~/.config/fontconfig/conf.d/ && mv 10-powerline-symbols.conf ~/.config/fontconfig/conf.d/

#### Installing Powerline Shell

git clone https://github.com/milkbikis/powerline-shell

	cd /powerline-shell && ./install.py


##### touch ~/.bashrc && vim ~/.bashrc

	function _update_ps1() {
	       export PS1="$("path/to/cloned/repo/"powerline-shell.py $? 2> /dev/null)"
	    }

	    export PROMPT_COMMAND="_update_ps1; $PROMPT_COMMAND"

#### Close all terminal instances and you're done!
