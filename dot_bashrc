# COMMAND PROMT SETTINGS
# ======================

# 0 --> display full path
# 3 --> displaj last three parts of path: '.../subdir3/sundir2/subdir1'
export PROMPT_DIRTRIM=0

# 20241014: not used --> kept as a reference
#	parse_git_branch() {
#		if [ -d ./.git ] || [ -d ./hooks ]; then 
#			# printf '\e[01;38;5;141m%s\e[01;33;1;75m' "git:"
#			echo -en "\e[01;38;5;141mgit:\e[01;33;1;75m"
#			git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/(\1)/' -e 's/$/ /'
#		fi
#	}

date_stamp() {
	echo -e "\e[38;5;244m[$(date +"%Y-%m-%d")] [$(date +%T)]\e[0m"
}

# 20240214
# check: symbols and prompts_20240214.txt in ~/majstaf_en/metsys_en/

decorate_link() {
	pth=$(pwd)
	if [ -L $pth ]; then
		echo "[$pth]"
	else
		echo "$pth"
	fi
}

# 20241014
prompt_left() {
	# simple
	# echo -e "\[\e[01;38;5;75m\][\u@\h] \w"

	# NERD symbols
	off='\e[m'
	orange_bg='\e[01;38;5;215m'
	orange_inv='\e[07;38;5;215m'
	orange_blue='\e[07;48;5;215;38;5;111m'

	blue_inv='\e[07;48;5;0;38;5;111m'
	blue_bg='\e[01;38;5;111m'
	blue_lila='\e[01;38;5;111;48;5;141m'

	lila_bg='\e[01;38;5;141m'
	lila_inv='\e[07;38;5;141;48;5;0m'

	yllw_bg='\e[01;38;5;228m'
	yllw_inv='\e[07;38;5;228m'
	blue_yllw='\e[01;38;5;111;48;5;228m'

	red_bg='\e[01;91m'
	red_inv='\e[07;91m'
	blue_red='\e[01;38;5;111;101m'

	if [ -d ./.git ] || [ -d ./hooks ]; then
		git_info=" git: $(git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/(\1)/' -e 's/$/ /')"
		/usr/bin/git status | grep -i "new file\|modified\|untracked" &>/dev/null
		if [ $? -eq 1 ]; then
			echo -e "${orange_bg}${orange_inv}\u@\h ${orange_blue}${blue_inv}\w${off}${blue_yllw}${off}${yllw_inv}${git_info}${off}${yllw_bg}${off}"
		else
			echo -e "${orange_bg}${orange_inv}\u@\h${orange_blue}${blue_inv}\w${off}${blue_red}${off}${red_inv}${git_info}${off}${red_bg}${off}"
		fi
	else
		echo -e "${orange_bg}${orange_inv}\u@\h ${orange_blue}${blue_inv} $(pwd) ${off}${blue_lila}${off}${lila_bg}${off}"
	fi
}

# 20241014
prompt_next() {
	# simple

	# NERD symbols
	# echo -e  "\[\e[1;31m\]\u21AA \[\e[0m\]"
	# echo -e  "\[\e[1;31m\] \[\e[0m\]"
	echo -e  "\[\e[1;31m\] \[\e[0m\]"
}

# 20241014
prompt() {
	PS1=$(printf "\n%*s\r%s\n%s " "$(($(tput cols) + 14))" "$(date_stamp)" "$(prompt_left)" "$(prompt_next)")
}

# 20241014
PROMPT_COMMAND=prompt



# ================
# external sources
# ================
source $HOME/majstaf_en/majrcs_en/bashrc_gredelonghi_en
source $HOME/majstaf_en/majrcs_en/aliases_gredelonghi_en
source $HOME/majstaf_en/majrcs_en/funclist_en
source $HOME/majstaf_en/majrcs_en/startfuncs_en
source $HOME/majstaf_en/majconfig_en/centralna_en.conf
source $HOME/.SCRTS_en

# eval "`dircolors -b $HOME/.dircolorsrc`"

# export LANG=sl_SI.utf8
export LANG=en_US.utf8


###  EN-proxy ...
prx_ip=10.91.8.21
export http_proxy=http://${prx_ip}:80/
export ftp_proxy=ftp://${prx_ip}:8021/
export https_proxy=http://${prx_ip}:80/

export HTTP_PROXY=http://${prx_ip}:80/
export FTP_PROXY=ftp://${prx_ip}:8021/
export HTTPS_PROXY=http://${prx_ip}:80/


### added TEST 20170117
alias lg='ls -ah --color' && function cg(){ cd "$@" && lg; }


# POWERLINE SETTINGS 20201125 -- no powerline font gliphs -- unable to instal powerline fonts (no admin rigths)
# powerline-daemon -q
# POWERLINE_BASH_CONTINUATION=1
# POWERLINE_BASH_SELECT=1
# . /usr/local/lib/python3.8/site-packages/powerline_status-2.8.1.dev9999_git.b_f401ee3106b027efabdbbd7b920868cefd8277c4_-py3.8.egg/powerline/bindings/bash/powerline.sh
#

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/.local/bin" ] ; then
	    PATH="$HOME/.local/bin:$PATH"
fi

# 20241003
# after installing zoxside (for cygwin only): curl -sSfL https://raw.githubusercontent.com/ajeetdsouza/zoxide/main/install.sh | sh
# eval "$(zoxide init bash)"

