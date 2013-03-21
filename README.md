# zsh-function-mysql

The wrapper zsh function of mysql command. Support flexible MySQL CLI prompt.

## Installation

    $ cd /path/to
    $ git clone git://github.com/tetsujin/zsh-function-mysql.git
    $ mkdir -p ~/.zsh.d/functions
    $ ln -s /path/to/zsh-function-mysql/mysql ~/.zsh.d/functions

## Usage

In your `.zshrc`, put bellow lines.

    fpath=(
        $HOME/.zsh.d/*(/N)
        $fpath
    )
    autoload -U colors; colors
    autoload -U $(echo ~/.zsh.d/functions/*(:t))

And configuration into your `.zshrc`.

    # mysql client user
    typeset -A mysql_prompt_style_client_user
    mysql_prompt_style_client_user=(
        # 'root'     $fg_bold[red]
        # '*'        $fg_bold[green]
    )
    # mysql client host
    typeset -A mysql_prompt_style_client_host
    mysql_prompt_style_client_host=(
        '*.local.*'     "$fg_bold[green]"
        '*.dev.*'       "$fg_bold[yellow]"
        '*'             "$fg_bold[red]"
    )
    # mysql server user
    typeset -A mysql_prompt_style_server_user
    mysql_prompt_style_server_user=(
        'root'          "$bg_bold[red]$fg_bold[yellow]"
        '*'             "$fg_bold[blue]"
    )
    # mysql server host
    typeset -A mysql_prompt_style_server_host
    mysql_prompt_style_server_host=(
        '*master*'      "$bg_bold[red]$fg_bold[yellow]"  # Master Server
        '*slave*'       "$bg[yellow]$fg[black]" # Slvae Server
        '*'             "$fg_bold[blue]"
    )
    # mysql prompt style (Should use single quoted string.)
    mysql_prompt='${style_client_host}${USER}@${HOST}${fg_bold[white]} -> '
    mysql_prompt=$mysql_prompt'${style_server_user}\u${reset_color}${fg_bold[white]}@${style_server_host}\h${reset_color}${fg_bold[white]}:${fg[magenta]}\d ${fg_bold[white]}\v${reset_color}\n'
    mysql_prompt=$mysql_prompt'mysql> '
    
## Screenshot

* ![sample1](https://raw.github.com/tetsujin/zsh-function-mysql/master/doc/img/sample1.png)
* ![sample2](https://raw.github.com/tetsujin/zsh-function-mysql/master/doc/img/sample2.png)

