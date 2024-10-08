# 💻 Personal shell configurations
  
> [!NOTE]  
These configurations are interdependent;  
follow them in the given order.  
WSL sections can be skipped for Linux configurations.  

<hr style="border: 0; height: 1px; background: #21262d;">

<details open>
  <summary><strong> Prerequisites</strong></summary>

  - **Packages** : ``eza`` ``figlet`` ``git`` ``gh`` ``tmux`` ``neofetch``
  - **Services** : ``sshd`` ``apache2`` ``mariadb`` ``postgres`` ``postfix``
  - **Plugins** : ``oh-my-zsh`` ``powerlevel10k``
  - **Terminal** : ``QTerminal``
  - **Fonts** : ``Nerd Font``
</details>

<hr style="border: 0; height: 1px; background: #21262d;">

<details>
  <summary><strong> Powerlevel10k Theme</strong></summary>

  ```sh
  ### Powerlevel10k Theme

  # Enable Powerlevel10k instant prompt. Should stay close to the top of ~/.zshrc.
  # Initialization code that may require console input (password prompts, [y/n]
  # confirmations, etc.) must go above this block; everything else may go below.
  if [[ -r "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh" ]]; then
    source "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh"
  fi

  # Make zsh instant prompt quiet
  typeset -g POWERLEVEL9K_INSTANT_PROMPT=quiet

  #######################################################################
  ```
</details>

<details>
  <summary><strong> ZSH Basic Config</strong></summary>

  ```sh
  ### ZSH Basic Config

  set autocd         # change directory just by typing his name
  setopt promptsubst # enable command substitution in prompt

  # configure keybindings
  bindkey -e # emacs keybindings
  bindkey ' ' magic-space # do history expansion on space

  # Uncomment the following line to use case-sensitive completion.
  CASE_SENSITIVE="true"

  #######################################################################
  ```
</details>

<details>
  <summary><strong> oh-my-zsh config</strong></summary>

  ```sh
  ### oh-my-zsh Config

  # Path to oh-my-zsh installation.
  export ZSH="$HOME/.oh-my-zsh"

  # Oh-My-Zsh custom theme
  ZSH_THEME="powerlevel10k/powerlevel10k"
  # ZSH_THEME="archcraft"

  # Which plugins would you like to load?
  # Standard plugins can be found in $ZSH/plugins/
  # Custom plugins may be added to $ZSH_CUSTOM/plugins/
  plugins=(
    zsh-syntax-highlighting
    zsh-autosuggestions
    web-search
    vscode
    sudo
  )

  # Here to disable oh-my-zsh auto update
  DISABLE_AUTO_UPDATE="true"

  # This is for fastfile Oh-My-Zsh Plugin
  fastfile_var_prefix='$'

  # Declare the variable for zsh-syntax-highlighting styles
  typeset -A ZSH_HIGHLIGHT_STYLES

  # From ~/.oh-my-zsh/plugins/zsh-syntax-highlighting/highlighters/main/README.md
  ZSH_HIGHLIGHT_STYLES[path]='none'
  ZSH_HIGHLIGHT_STYLES[autodirectory]=fg='#ffffff'
  ZSH_HIGHLIGHT_STYLES[suffix-alias]=fg='none'
  ZSH_HIGHLIGHT_STYLES[precommand]=fg='none'
  ZSH_HIGHLIGHT_STYLES[arg0]=fg='none'
  ZSH_HIGHLIGHT_STYLES[single-quoted-argument]=fg='#23ff45'
  ZSH_HIGHLIGHT_STYLES[double-quoted-argument]=fg='#23ff45'
  ZSH_HIGHLIGHT_STYLES[single-hyphen-option]='fg=#37b0ff,bold'
  ZSH_HIGHLIGHT_STYLES[double-hyphen-option]='fg=#37b0ff,bold'
  ZSH_HIGHLIGHT_STYLES[redirection]='fg=#ffe541,bold'
  ZSH_HIGHLIGHT_STYLES[globbing]='fg=#ff9000,bold'
  ZSH_HIGHLIGHT_STYLES[command-substitution-unquoted]='fg=#d30ccf,bold'
  ZSH_HIGHLIGHT_STYLES[command-substitution-delimiter]='fg=#d30ccf,bold'

  # here the color of the auto-suggestion
  # ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE=fg=#0000ff"

  # source oh-my-zsh after everything have been loaded
  source $ZSH/oh-my-zsh.sh

  #######################################################################
  ```
</details>

<details>
  <summary><strong> Tmux Config</strong></summary>

  ```sh
  ### Tmux Config

  # Launch tmux at startup
  case $TERM in
    screen|tmux-256color);;
    *)tmux att -t 0 2>/dev/null|| tmux;;
  esac;

  # this alias to launch tmux
  alias tmx="tmx"

  #this function for tmx alias
  function tmx(){
    if [[ $(tmux ls | wc -l) -gt 0 ]]; then
     tmux rename-session "$(basename "$PWD")"
    else
    clear && br
    fi
  }

  #######################################################################
  ```
</details>

<details>
  <summary><strong>ANSI Color Codes</strong></summary>

  ```sh
  ### ANSI CODES VARIABLES

  # Text Color
  BLACK="\e[30m"
  RED="\e[31m"
  GREEN="\e[32m"
  YELLOW="\e[33m"
  BLUE="\e[34m"
  MAGENTA="\e[35m"
  CYAN="\e[36m"
  LIGHT_GRAY="\e[37m"
  DARK_GRAY="\e[90m"
  LIGHT_RED="\e[91m"
  LIGHT_GREEN="\e[92m"
  LIGHT_YELLOW="\e[93m"
  LIGHT_BLUE="\e[94m"
  LIGHT_MAGENTA="\e[95m"
  LIGHT_CYAN="\e[96m"
  WHITE="\e[97m"

  # Background Color
  BG_BLACK="\e[40m"
  BG_RED="\e[41m"
  BG_GREEN="\e[42m"
  BG_YELLOW="\e[43m"
  BG_BLUE="\e[44m"
  BG_MAGENTA="\e[45m"
  BG_CYAN="\e[46m"
  BG_LIGHT_GRAY="\e[47m"
  BG_DARK_GRAY="\e[100m"
  BG_LIGHT_RED="\e[101m"
  BG_LIGHT_GREEN="\e[102m"
  BG_LIGHT_YELLOW="\e[103m"
  BG_LIGHT_BLUE="\e[104m"
  BG_LIGHT_MAGENTA="\e[105m"
  BG_LIGHT_CYAN="\e[106m"
  BG_WHITE="\e[107m"

  # Text Style
  BOLD="\e[1m"
  DIM="\e[2m"
  UNDERLINE="\e[4m"
  BLINK="\e[5m"
  INVERT="\e[7m"
  HIDDEN="\e[8m"

  # Reset
  RESET="\e[0m"
  RESETBG="\e[49m\n"

  # Character
  CHECKMARK="$(printf '\xE2\x9C\x94')"
  QUESTION_MARK="$(printf '\xE2\x9D\x93')"

  #######################################################################
  ```
</details>

<details>
  <summary><strong> Basic Aliases</strong></summary>

  ```sh
  ### Basic Aliases

  # this alias to update the package
  alias upd="allow_sudo && upd"

  # this function for up alias
  function upd(){
    echo "u p d a t i n g .  .  ." | figlet -t -c;
    br && sudo apt update && br;
  }

  # this alia to update the package
  alias upg="allow_sudo && upg"

  # this function for up alias
  function upg(){
    echo "u p g r a d i n g . . ." | figlet -t -c;
    br && sudo apt upgrade && br;
  }

  # this alias to install package
  alias ist="allow_sudo && ist"

  # this function for ist alias
  function ist(){
    case "${1##*.}" in
      git)
        echo "   C l o n i n g .  .  . " | figlet;
        br && echo "Package =======> "${1%.*}" ";
        br && git clone "$1" && br;
        ;;
      *)
        echo "   I n s t a l l i n g .  .  . " | figlet;
        c && br && echo "Package =======> "$1" ";
        br && sudo apt install "$1" && br;
        ;;
    esac
  }

  # this alias to install package
  alias rmv="rmv"

  # this function for ist alias
  function rmv(){
    case "${1##*.}" in
      deb)
        c && echo -e && echo -e && sudo clear && echo -e && echo -e && echo "   r e m o v i n g .  .  . " | figlet | lolcat && echo -e && echo "Package =======> "${1%.*}" " && echo -e && sudo dpkg -r "$1" && echo -e;
        ;;
      *)
        c && echo -e && echo -e && sudo clear && echo -e && echo -e && echo "   r e m o v  i n g .  .  . " | figlet | lolcat && echo -e && echo "Package =======> "$1" " && echo -e && sudo apt remove "$1" && echo -e;
        ;;
    esac
  }

  # this alias to rename a file / directory; and display it after
  alias nm="nm"

  # this function for cpf alias
  function nm(){
    mv "$1" "$2" && cv;
  }

  # this line to count line inside a file
  alias cl="linecount"

  # this function for the cl alias
  function linecount() {
    if [ -z "$1" ]; then
        echo "Please provide a filename"
    elif [ -z "$2" ]; then
        wc -l "$1" | awk '{print $1, "lines"}'
    else
        grep -c "$1" "$2" | awk -v var="$1" '{print $1, var, "in it"}'
    fi
  };

  # this line to view a command manual
  alias mn="mn"

  # this function for mn alias
  function mn(){
    if [[ $# -eq 1 ]]; then
      man $1 | less
    else
      man $1 | grep $2 | less
    fi
  }

  # this alias to view tthe manual entry for a command
  alias mns="mns"

  # this function for mn alias
  function mns(){
    if [[ $(command -v "$1") ]]; then
      local manual_path=~/NTSOA/manual
      # here to check if the command exists
      man "$1" | cat > $manual_path/"$1"_manual.txt;
      all $manual_path/"$1"_manual.txt;
      vf $manual_path/"$1"_manual.txt;
      cv;
    else
      cv
    fi
  }

  # this alias to enter the manual directory
  alias mnv="mnv"

  # this function for mnv alias
  function mnv(){
    if [[ $# -eq 0 ]]; then
      op /home/h471x/NTSOA/manual;
    elif [[ $# -eq 1 ]]; then
      op /home/h471x/NTSOA/manual "$1";
    fi
  }

  # this alias to view the pc state
  alias pc="c && br 2 && neofetch --source ~/.config/neofetch/htx2.txt"

  # this alias to view the history
  alias hst="hst"

  # this function for hst alias
  function hst(){
    if [[ $# -eq 0 ]]; then
      history | less && cv
    else
      re='^[0-9]+$'
      # check if the argument is an integrer
      if [[ $1 =~ $re ]]; then
        history | tail -$1 | less && cv
      else  # else if it's a text to grep
        history | grep "$1" | less && cv
      fi
    fi
  }

  # this alias to specify which command in the history to search
  alias hsg="hsg"

  # this function for hsg alias
  function hsg(){
    if [[ $# -eq 0 ]]; then
      history | less && cv;
    else
      history | grep "$1" | less && cv;
    fi
  }

  # this alias to count line and words inside a file
  alias flc="flc"

  # this function for the cl alias
  function flc(){
    if [[ -f "$1" ]]; then
      if [ -z "$1" ]; then
        echo "Please provide a filename"
      elif [ -z "$2" ]; then
        c && br;
        echo -ne " ==> "
        file "$1";
        echo -ne " ==> ";
        wc -l "$1" | awk '{print $1, "lines"}';
        echo -ne " ==> ";
        wc -w "$1" | awk '{print $1, "words"}';
        br;
      else
        grep -c "$1" "$2" | awk -v var="$1" '{print $1, var, "in it"}'
      fi
    elif [[ -d "$1" ]]; then
      dc "$1";
    fi
  }

  # this alias to list
  alias list="list"

  # this function for list alias
  function list(){
    local list_app="eza --icons=always --no-quotes"
    eval $list_app
  }

  # this alias to save a file content to another file
  alias sv="sv"

  # this function for sv alias
  function sv(){
    cat "$1" > "$2";
  }

  kill-line() {
    if [[ $BUFFER == "" ]]; then
      zle backward-kill-line
    else
      zle kill-whole-line
    fi
  }

  zle -N kill-line
  bindkey "²²" kill-line

  # this alias to clear
  alias c="clear"

  # this alias to clear but with extra lines
  alias x="clear && echo -e && echo -e && echo -e && echo -e && echo -e && echo -e"

  # this alias to break a line
  alias br="br"

  # this function for br alias
  function br(){
    if [[ $# -eq 1 ]]; then
      for ((i=1; i<=$1;i++)); do
        echo -e;
      done
    elif [[ $# -eq 0 ]]; then
      echo -e;
    fi
  }

  # this alias to show the welcome message
  alias cvi="cvii"

  # here to write a welcome message
  function cvii(){
    clear && br 2;
    echo "H    4    7    1    X" | figlet -t -c;
    br 2;
  }

  x;

  # this alias to exit
  alias q='exit'

  # this alias to give full permission
  alias all="all"

  # this function for all alias
  function all(){
    if [[ $# -eq 0 ]]; then
      if [[ -d "$1" ]]; then
        chmod 700 * && cv;
      elif [[ -f "$1" ]]; then
        chmod 777 * && cv;
      fi
    else
      if [[ -d "$1" ]]; then
        chmod 700 "$@" && cv;
      elif [[ -f "$1" ]]; then
        chmod 777 "$@" && cv;
      fi
    fi
  }

  #######################################################################
  ```
</details>

<details>
  <summary><strong> Navigation Aliases</strong></summary>

  ```sh
  ### Navigation Aliases

  # this alias to have the current view
  # of working directory content using ls
  alias cv="cv"

  # this function for cv alias
  # UPDATED : 01/25/2024
  # to adjust the title
  # when we have more than 50 visible items
  function cv() {
    local target="$1"
    local folder_content="${target:-$PWD}"
    local folder_name=$(basename $folder_content)
    local visible_item=$(ls $folder_content | wc -l)
    local total_item=$(ls -A $folder_content | wc -l)
    local hidden_item=$((total_item - visible_item))

    # this function for the header of cv alias
    function show_header(){
      local folder_header
      if [[ $total_item -eq 0 ]]; then
        folder_header="Empty(0)";
        folder_icon=" "
      elif [[ $hidden_item -eq 0 ]]; then
        folder_header="total($visible_item)";
        folder_icon=" "
      else
        folder_header="visible($visible_item) hidden($hidden_item) total($total_item) ";
        folder_icon=" "
      fi
      echo "${BOLD}${WHITE} $folder_icon $folder_name -> $folder_header ${RESET}";
    }

    # this function to show the content of the cv
    function show_content(){
      # local flag="${1:-}"
      # ls $flag $folder_content;
      eza --icons=always --no-quotes --group-directories-first $folder_content
    }

    # this function to show the all of the cv content
    function show_all(){
      c && br;

      if [[ $visible_item -lt 30 ]]; then
        show_header;
        br;
        show_content;
        br;
      else
        show_content;
        br 2;
        show_header;
        br;
      fi
    }
    show_all;
  }

  # this alias to view the current directory content
  alias cvf="cvf"

  # this function for cvf alias
  # UPDATED : 01/25/2024
  # to adjust the title
  # when we have more than 50 visible items
  function cvf() {
    local target="$1"
    local folder_content="${target:-$PWD}"
    local folder_name=$(basename $folder_content)
    local visible_item=$(ls $folder_content | wc -l)
    local total_item=$(ls -A $folder_content | wc -l)
    local hidden_item=$((total_item - visible_item))

    # this function for the header of cv alias
    function show_header(){
      local folder_header
      if [[ $total_item -eq 0 ]]; then
        folder_header="Empty(0)";
        folder_icon=" "
      elif [[ $hidden_item -eq 0 ]]; then
        folder_header="total($visible_item)";
        folder_icon=" "
      else
        folder_header="visible($visible_item) hidden($hidden_item) total($total_item) ";
        folder_icon=" "
      fi
      echo "${BOLD}${WHITE} $folder_icon $folder_name -> $folder_header ${RESET}";
    }

    # this function to show the content of the cv
    function show_content(){
      eza --icons=always --no-quotes -a --group-directories-first $folder_content;
    }

    # this function to show the cv
    function show_all(){
      c && br;

      if [[ $hidden_item -lt 30 ]]; then
        show_header;
        br;
        show_content;
        br;
      else
        show_content;
        br 2;
        show_header;
        br;
      fi
    }
    show_all;
  }

  # this alias to view the current directory content
  # with specifications
  alias cvg="cvg"

  # this function for cvg alias
  function cvg(){
    local folder_name=$(basename $PWD)
    local item="$1"
    local matched_items=$(ls -A | grep "$item" | wc -l)

    function show_header(){
      echo "${BOLD}   $folder_name -> contains $matched_items '$1' ${RESET}";
    }

    function show_content(){
      eza --icons=always --color=always -a --group-directories-first | grep "$1";
    }

    # this function to show the cv
    function show_all(){
      c && br;

      if [[ $matched_items -lt 20 ]]; then
        show_header $1; br;
        show_content $1; br;
      else
        show_content $1; br;
        show_header $1;
      fi
    }
    show_all $item;
  }

  # this alias to open a directory
  alias op="op"

  # this function for op alias
  function op() {
    # Check if $1 is a symbolic link
    if [[ -L "$1" ]]; then
      # Resolve the real path of the symbolic link
      real_path=$(readlink -f "$1")
      # Check if the resolved path is a directory
      if [[ -d "$real_path" ]]; then
        if [[ $# -eq 1 ]]; then
          cd "$real_path" && cv
        elif [[ $# -eq 2 ]]; then
          cd "$real_path" && cvg "$2"
        fi
      # Check if the resolved path is a file
      elif [[ -f "$real_path" ]]; then
        vf "$real_path"
      fi
    # If $1 is a directory (but not a symbolic link)
    elif [[ -d "$1" ]]; then
      if [[ $# -eq 1 ]]; then
        cd "$1" && cv
      elif [[ $# -eq 2 ]]; then
        cd "$1" && cvg "$2"
      fi
    # If $1 is a file (but not a symbolic link)
    elif [[ -f "$1" ]]; then
      vf "$1"
    fi
  }

  # this alias to create a directory
  alias dr="dr"

  # this function for dr alias
  function dr(){
    mkdir "$@" && cv;
  }

  # this alias to remove a directory
  alias rd="rd"

  # this function for rd alias
  function rd(){
    rm -r "$@" && cv;
  }

  # this line to have destination location for copy / cut
  alias dt="dt"

  # this function for dst alias
  function dt(){
    dest="$PWD" && c && echo -e && echo "d e s t   s a v e d" | figlet -t -c && sleep 0.6 && cv;
  }

  # this alias to open a directory
  # and make it as destination
  alias opd="opd"

  # this function for opd alias
  function opd(){
    op "$1" && dt && nd;
  }

  # this alias to create a directory
  # and then directly enter to it
  alias opdr="opdr"

  # this function for opdr alias
  function opdr(){
    dr "$*" && op "$*";
  }

  # this alias to go back from a directory
  alias b="b"

  # this function for b alias
  function b(){
    if [[ $# -eq 0 ]]; then
      cd .. && cv
    else
      for ((i=1; i<=$1;i++)); do
        cd .. && cv
      done
    fi
  }

  # this alias to go to the previous directory
  alias nd="nd"

  # this function for nd alias
  function nd(){
    cd - &>/dev/null;
    cv;
  }

  #######################################################################
  ```
</details>

<details>
  <summary><strong> Sudo Aliases</strong></summary>

  ```sh
  ### Sudo Aliases

  # this alias to give sudo
  # access before command execution
  alias allow_sudo="allow_sudo"

  # this function for allow_sudo alias
  # HACK : 05-12-2024 15:28
  # check if sudo requires a password
  # then show the password prompt,
  # otherwise just execute the next command
  function allow_sudo(){
    sudo -n true &>/dev/null
    if [ $? -eq 1 ]; then
      sudo echo && return 0 || return 1
    else
      return 0
    fi
  }

  # this alias to simulate the sudo behaviour
  alias hndo="hndo"

  # this function for hndo alias
  function hndo(){
    local attempts=3
    local attempts_num=$(echo $attempts)
    local expected_hashed_password="5e884898da28047151d0e56f8dc6292773603d0d6aabbdd62a11ef721d1542d8"
    # this is "password" hashed
    # use this command : echo -n password | sha256sum | awk '{print $1}'

    c && br 2

    while [ $attempts -gt 0 ]; do
      echo -ne "Your Password, Sir : "
      read -s password

      # Hash the entered password
      hashed_input=$(echo -n "$password" | sha256sum | awk '{print $1}')

      if [ "$hashed_input" = "$expected_hashed_password" ]; then
        c && br
        eval "$@"
        return
      else
        attempts=$((attempts - 1))
        br
        echo -n "Wrong, Try Again"
        br
        if [ $attempts -gt 0 ]; then
          continue
        else
          echo "hndo: $attempts_num incorrect password attempts"
          return 1
        fi
      fi
    done
  }

  # this alias to switch to root
  alias ad="ad"

  # this function for ad alias
  function ad(){
    c && echo -e && echo -e && sudo su && cv;
  }

  #######################################################################
  ```
</details>

<details>
  <summary><strong> Git Aliases</strong></summary>

  ```sh
  ### Git Aliases

  # this alias to git add and git commit at the same time
  alias gad="gad"

  # this function for gad alias
  # SOLVED: 05-11-2024 23:43
  # handled git add and git commit
  # according to the first argument
  # if it's not a file then it is
  # a commit message, otherwise check
  # if it is a file then the rest
  # of the argument is the commit
  function gad(){
    local is_a_git_repo=$(git rev-parse --is-inside-work-tree 2>/dev/null)

    if [[ "$is_a_git_repo" == "true" ]]; then
      if [[ $# -eq 0 ]]; then
        git add --all && git commit
      elif [[ $# -ge 1 ]]; then
        if [[ -f "$1" ]]; then
          if [[ $# -eq 1 ]]; then
            echo "${BOLD}${RED}Error : no commit message !"
          else
            # consider all arguments from the second one as one string
            git add "$1" && git commit "$1" -m "${*:2}";
          fi
        else
          git add --all && git commit -m "$*"
        fi
      fi
    else
      echo "${BOLD} ■■▶ This won't work, you are not in a git repo !" && br;
    fi
  }

  # this alias to rename a git branch
  alias gnm="gnm"

  # this function for gnm alias
  function gnm(){
    local is_a_git_repo=$(git rev-parse --is-inside-work-tree 2>/dev/null)

    if [[ "$is_a_git_repo" == "true" ]]; then
      local current_branch=$(git branch | awk '/\*/ {print $2}');

      if [[ $# -eq 1 ]]; then
        git branch -M $current_branch "$1";
        cv;
      elif [[ $# -eq 0 ]]; then
        echo "${BOLD} ■■▶ Please pass the new name of '$current_branch' branch as argument " && br;
      else
        echo "${BOLD} ■■▶ Usage : gnm new_name_of_the_branch" && br;
      fi
    else
      echo "${BOLD} ■■▶ This won't work, you are not in a git repo !" && br;
    fi
  }

  # autocomplete gnm
  complete -F branch_auto_complete gnm

  # this alias to switch to the last git branch
  alias gck="gck";

  # this function for gck alias
  function gck(){
    local is_a_git_repo=$(git rev-parse --is-inside-work-tree 2>/dev/null)
    local has_remote=$(git remote -v)

    if [[ "$is_a_git_repo" == "true" ]]; then
      local current_branch=$(git branch | awk '/\*/ {print $2}');

      if [ "$has_remote" ]; then
        local default_branch=$(git symbolic-ref refs/remotes/origin/HEAD 2>/dev/null | sed 's@^refs/remotes/origin/@@')
        local repo_url=$(git config --get remote.origin.url)
        local repo_name="$(echo "$repo_url" | awk -F '/' '{print $NF}' | sed 's/.git$//')"
      else
        local default_branch=$(git config --get init.defaultBranch)
        local repo_name=$(basename "$(git rev-parse --show-toplevel)")
      fi

      if [[ -z "$default_branch" ]]; then
        default_branch=$(git config --get init.defaultBranch)
      fi

      if [[ $# -eq 0 ]]; then
        if [[ "$current_branch" != "$default_branch" ]]; then
          git checkout "$default_branch"
        else
          local user="$(whoami)"
          if ! git rev-parse --verify "$user" >/dev/null 2>&1; then
            function check_new_branch(){
              echo -ne "${BOLD}${WHITE}New branch${GREEN} "$user"${WHITE} ? (y/n) ";
              read branch
              if [ "$branch" = "y" ]; then
                git checkout -b "$user" &>/dev/null;

                # check for remote
                if [ "$has_remote" ]; then
                  function check_new_remote_branch(){
                    echo -ne "${BOLD}${WHITE}Add${GREEN} "$user"${WHITE} branch to ${LIGHT_BLUE}$repo_name ${WHITE} on GitHub ? (y/n) ";
                    read remote_branch
                    if [ "$remote_branch" = "y" ]; then
                      git push origin "$user";
                    elif [ "$remote_branch" = "n" ];then
                      return 0
                    else
                      check_new_remote_branch
                    fi
                  }
                  check_new_remote_branch
                fi
              elif [ "$branch" = "n" ];then
                return 0
              else
                check_new_branch
              fi
            }
            check_new_branch
          else
            git checkout "$user"
          fi
        fi
      elif [[ $# -eq 1 ]]; then
        # check if the branch doesn't exist yet
        if ! git rev-parse --verify "$1" >/dev/null 2>&1; then
          local new_branch="$1"
          function check_new_branch(){
            echo -ne "${BOLD}${WHITE}New branch${GREEN} "$new_branch"${WHITE} ? (y/n) ";
            read branch
            if [ "$branch" = "y" ]; then
              git checkout -b "$new_branch" &>/dev/null;

              # check for remote
              if [ "$has_remote" ]; then
                function check_new_remote_branch(){
                  echo -ne "${BOLD}${WHITE}Add${GREEN} "$new_branch"${WHITE} branch to ${LIGHT_BLUE}$repo_name ${WHITE} on GitHub ? (y/n) ";
                  read remote_branch
                  echo ${RESET}
                  if [ "$remote_branch" = "y" ]; then
                    git push origin "$new_branch";
                  elif [ "$remote_branch" = "n" ];then
                    return 0
                  else
                    check_new_remote_branch
                  fi
                }
                check_new_remote_branch
              fi
            elif [ "$branch" = "n" ];then
              return 0
            else
              check_new_branch
            fi
          }
          check_new_branch
        else
          git checkout "$1";
        fi
      else
        echo "${BOLD} ■■▶ Usage : gck branch or gck (switch default branch)" && br;
      fi
    else
      echo "${BOLD} ■■▶ This won't work, you are not in a git repo !" && br;
    fi
  }

  # this function to autocomplete
  # the branches of gck alias
  function branch_auto_complete(){
    local cur branches

    # Get the current word being completed
    cur="${COMP_WORDS[COMP_CWORD]}"

    # Get the list of branches from `git branch`
    branches=$(git branch --format '%(refname:short)')

    # Generate completions
    COMPREPLY=($(compgen -W "${branches}" -- "${cur}"))
  }

  # Register the completion function for `gck`
  complete -F branch_auto_complete gck

  # this alias to switch to the last git branch
  alias gcb="gcb";

  # this function for gcb alias
  function gcb(){
    local is_a_git_repo=$(git rev-parse --is-inside-work-tree 2>/dev/null)

    if [[ "$is_a_git_repo" == "true" ]]; then
      if [[ $# -eq 0 ]]; then
        git checkout -;
      else
        echo "${BOLD} ■■▶ Usage : gcb (no argument)" && br;
      fi
    else
      echo "${BOLD} ■■▶ This won't work, you are not in a git repo !" && br;
    fi
  }

  # this alias to create a new branch and switch to it
  alias gbr="gbr"

  # this function for gbr alias
  function gbr(){
    local is_a_git_repo=$(git rev-parse --is-inside-work-tree 2>/dev/null)

    if [[ "$is_a_git_repo" == "true" ]]; then
      if [[ $# -eq 1 ]]; then
        git checkout -b "$1";
      elif [[ $# -eq 0 ]]; then
        git branch -a;
      else
        echo "${BOLD} ■■▶ Usage : gbr new_branch" && br;
      fi
    else
      echo "${BOLD} ■■▶ This won't work, you are not in a git repo !" && br;
    fi
  }

  # this alias to revert back to last commit
  alias grst="grst"

  # this function for grst alias
  function grst(){
    if [[ $# -eq 0 ]]; then
      git checkout -- .;
    elif [[ $1 == "cmt" ]]; then
      git reset --soft HEAD~1
    else
      git restore "$@";
    fi
  }

  # this function to autocomplete
  # files to reset from git status
  function _grst_completion() {
    local cur opts

    # Get the current word being completed
    cur="${COMP_WORDS[COMP_CWORD]}"

    # Get the list of uncommitted changes from `git status -s`
    opts=$(git status -s | awk '{print $2}')

    # Generate completions
    COMPREPLY=($(compgen -W "${opts}" -- "${cur}"))
  }

  # Register the completion function for `grst`
  complete -F _grst_completion grst

  # this alias to push changes on current repo to remote repo
  alias gpsh="gpsh"

  # this function for gpsh alias
  function gpsh(){
    local is_a_git_repo=$(git rev-parse --is-inside-work-tree 2>/dev/null)
    local has_remote=$(git remote -v)

    if [ "$has_remote" ]; then
      local repo_url=$(git config --get remote.origin.url)
      local repo_name="$(echo "$repo_url" | awk -F '/' '{print $NF}' | sed 's/.git$//')"
    else
      local repo_name=$(basename "$(git rev-parse --show-toplevel)")
    fi


    if [[ "$is_a_git_repo" == "true" ]]; then
      local current_branch=$(git branch | awk '/\*/ {print $2}');

      # check if it has a remote to push
      if [ "$has_remote" ]; then
        git push origin $current_branch;
      else
        echo "${BOLD} The local repo ${LIGHT_BLUE}$repo_name ${WHITE}has ${RED}no remote";
      fi
    else
      echo "${BOLD} ■■▶ This won't work, you are not in a git repo !" && br;
    fi
  }

  # this alias to pull changes from remote repo
  alias gpl="gpl"

  # this function for gpsh alias
  function gpl(){
    local is_a_git_repo=$(git rev-parse --is-inside-work-tree 2>/dev/null)
    local has_remote=$(git remote -v)

    if [ "$has_remote" ]; then
      local repo_url=$(git config --get remote.origin.url)
      local repo_name="$(echo "$repo_url" | awk -F '/' '{print $NF}' | sed 's/.git$//')"
    else
      local repo_name=$(basename "$(git rev-parse --show-toplevel)")
    fi

    if [[ "$is_a_git_repo" == "true" ]]; then
      local current_branch=$(git branch | awk '/\*/ {print $2}');

      if [ "$has_remote" ]; then
        local is_remote_branch=$(git branch -r | grep "origin/$current_branch")

        # check if the current branch has remote
        if [ -n "$is_remote_branch" ]; then
          git pull origin $current_branch;
        else
          echo "${BOLD} ■■▶ The remote repo ${LIGHT_BLUE}$repo_name ${WHITE}has no branch named ${GREEN}$current_branch ${WHITE}!" && br;
        fi
      else
        echo "${BOLD} The local repo ${LIGHT_BLUE}$repo_name ${WHITE}has ${RED}no remote";
      fi
    else
      echo "${BOLD} ■■▶ This won't work, you are not in a git repo !" && br;
    fi
  }

  # this alias to view git status
  alias gst="gst"

  # this function for gst alias
  function gst(){
    local is_a_git_repo=$(git rev-parse --is-inside-work-tree 2>/dev/null)

    if [[ "$is_a_git_repo" == "true" ]]; then
      git status -s
    else
      echo "${BOLD} ■■▶ This won't work, you are not in a git repo !" && br;
    fi
  }

  # this alias to view git diff
  alias gdf="gdf"

  # this function for gdf alias
  function gdf(){
    local is_a_git_repo=$(git rev-parse --is-inside-work-tree 2>/dev/null)

    if [[ "$is_a_git_repo" == "true" ]]; then
      git diff
    else
      echo "${BOLD} ■■▶ This won't work, you are not in a git repo !" && br;
    fi
  }

  # this alias to view the git log commits number
  alias glc="glc"

  # this function for glc alias
  function glc(){
    local is_a_git_repo=$(git rev-parse --is-inside-work-tree 2>/dev/null)

    if [[ "$is_a_git_repo" == "true" ]]; then
      local has_commits=$(git log > /dev/null 2>&1 && echo "true" || echo "false")

      if [[ "$has_commits" == "true" ]]; then
        local repo_name=$(basename "$(git rev-parse --show-toplevel)")
        local current_branch=$(git branch | awk '/\*/ {print $2}');
        local commits_num=$(git log --oneline | wc -l);
        local commit_text;
        local last_commit=$(git log --format="%H" -n 1);
        local last_commit_message=$(git show --format=%B -s "$last_commit" | head -n 1);
        local last_commit_author=$(git log --format='%an' -n 1)
        local current_user=$(git config user.name)
        local commits_done_today=$(git log --oneline --since="$(date +"%Y-%m-%d 00:00:00")" --author="$current_user" | wc -l)
        local commits_contrib_today=$(git log --oneline --since="$(date +"%Y-%m-%d 00:00:00")" --author="$last_commit_author" | wc -l)

        [[ $commits_num -le 1 ]] && commit_text="commit" || commit_text="commits";
        [[ $commits_done_today -le 1 ]] && commit_done_text="commit" || commit_done_text="commits";
        [[ $commits_contrib_today -le 1 ]] && commit_contrib_text="commit" || commit_contrib_text="commits";
        [[ $commits_done_today -gt 0 ]] &&
          commit_done="${WHITE}Including ${LIGHT_BLUE}$commits_done_today $commit_done_text ${WHITE}by ${GREEN}$current_user ${WHITE}today" ||
          commit_done="${WHITE}Including ${LIGHT_BLUE}$commits_contrib_today $commit_contrib_text ${WHITE}by ${GREEN}$last_commit_author ${WHITE}today"

        if [[ "$1" == "show" ]]; then
          git log --oneline --no-decorate;
        else
          echo "${BOLD}${LIGHT_BLUE} $repo_name ${WHITE}has ${LIGHT_BLUE}$commits_num $commit_text ";
          echo " $commit_done";
          echo "${BOLD}${WHITE} Last Commit on ${GREEN}$current_branch ${WHITE}: $last_commit_message";
          br;
        fi
      else
        echo "${BOLD} ■■▶ Sorry, no commits yet inside this repo !" && br;
      fi
    else
      echo "${BOLD} ■■▶ This won't work, you are not in a git repo !" && br;
    fi
  }

  # Completion function for glc
  _glc_completion() {
    local cur prev
    cur="${COMP_WORDS[COMP_CWORD]}"
    prev="${COMP_WORDS[COMP_CWORD-1]}"

    if [[ ${COMP_CWORD} -eq 1 ]]; then
      # Only suggest 'show' if no argument is provided
      COMPREPLY=($(compgen -W "show" -- "$cur"))
    else
      # If there are additional arguments, clear completions
      COMPREPLY=()
    fi
  }

  # Register the completion function for ghv
  complete -F _glc_completion glc

  # this alias to merge branches
  alias gmb="gmb"

  # this function for gmb alias
  function gmb(){
    local is_a_git_repo=$(git rev-parse --is-inside-work-tree 2>/dev/null)

    if [[ "$is_a_git_repo" == "true" ]]; then
      local current_branch=$(git branch | awk '/\*/ {print $2}');
      if [[ $# -eq 1 ]]; then
        # check if the branch doesn't exist
        if ! git rev-parse --verify "$1" >/dev/null 2>&1; then
          echo "${BOLD} ■■▶ Fatal ! $1 is a Non Existing branch " && br;
        else
          if [[ "$current_branch" == "$1" ]]; then
            echo "${BOLD} ■■▶ Fatal ! Cannot Merge Identical Branch " && br;
          else
            git merge "$1";
          fi
        fi
      elif [[ $# -eq 0 ]]; then
        echo "${BOLD} ■■▶ Fatal ! Specify the Branch to merge to $current_branch" && br;
      fi
    else
      echo "${BOLD} ■■▶ This won't work, you are not in a git repo !" && br;
    fi
  }

  # Register the completion function for `gmb`
  complete -F branch_auto_complete gmb

  #######################################################################
  ```
</details>

<details>
  <summary><strong> GitHub CLI Aliases</strong></summary>

  ```sh
  ### GitHub CLI Aliases

  # this function to sanitize the repository name
  function clean_repo() {
    local repo_name="$1"
    # Replace any characters that are
    # not alphanumeric or hyphen with hyphen
    local repo_pattern='s/[^a-zA-Z0-9-]+/_/g'
    local clean_name="$(echo "$repo_name" | sed -E "$repo_pattern")"
    echo "$clean_name"
  }

  # this alias to create a new github repository using github cli
  alias ghc="ghc"

  # this function for ghc alias
  # SOLVED: 05-11-2024 23:28
  # use shift to assign the argument
  # after the first one to be the
  # condition of is Private
  function ghc() {
    if [[ $# -eq 0 ]]; then
      local repo="$(basename "$PWD")"
    elif [[ $# -eq 1 ]]; then
      if [[ $1 != "private" ]]; then
        local repo="$1"
      elif [[ $1 -eq "private" ]]; then
        local repo="$(basename "$PWD")"
        local isPrivate="$1"
      fi
    elif [[ $# -gt 1 ]]; then
      local repo="$1"
      shift
      local isPrivate="$1"
    fi

    local repo_name="$(clean_repo "$repo")"
    local repo_visibility=$([[ $isPrivate == "private" ]] && echo "private" || echo "public")
    local is_a_git_repo=$(git rev-parse --is-inside-work-tree 2>/dev/null)

    if [[ "$is_a_git_repo" == "true" ]]; then
      local has_remote=$(git remote -v)

      if [ "$has_remote" ]; then
        echo "${BOLD} ■■▶ This repo has already a remote on GitHub !" && br;
      else
        local current_user=$(awk '/user:/ {print $2; exit}' ~/.config/gh/hosts.yml)

        function check_set_repo(){
          echo -ne "${BOLD}${WHITE} Create ${GREEN}$repo_visibility ${WHITE}repo ${LIGHT_BLUE}$repo_name ${WHITE}? (y/n) ";
          read set_repo
          if [ "$set_repo" = "y" ]; then
            # create the repo & set it as remote of the local one
            echo -ne "${BOLD} New repository ${LIGHT_BLUE}$repo_name ${WHITE}on GitHub ... "
            gh repo create "$repo_name" --$repo_visibility &>/dev/null;
            git remote add origin "git@github.com:$current_user/$repo_name.git";
            echo "${BOLD}${GREEN} ${WHITE}"

            function check_push(){
              echo -ne "${BOLD}${WHITE} Push local commits to ${LIGHT_BLUE}$repo_name ${WHITE}? (y/n) ";
              read check_push_commit

              if [ "$check_push_commit" = "y" ]; then
                local current_branch=$(git branch | awk '/\*/ {print $2}');
                git push origin $current_branch;
              elif [ "$check_push_commit" = "n" ];then
                return 0
              else
                check_push
              fi
            }

            local current_branch=$(git branch | awk '/\*/ {print $2}');

            if git rev-list --count "$current_branch" 2>/dev/null | grep -q '^[1-9]'; then
              check_push
            fi
          elif [ "$set_repo" = "n" ];then
            return 0;
          else
            check_set_repo
          fi
        }
        check_set_repo
      fi
    else
      function check_create_repo(){
        echo -ne "${BOLD}${WHITE} Create ${GREEN}$repo_visibility ${WHITE}repo ${LIGHT_BLUE}$repo_name ${WHITE}? (y/n) ";
        read create_repo
        if [ "$create_repo" = "y" ]; then
          # create the repo & clone it locally
          echo -ne "${BOLD} New repository ${LIGHT_BLUE}$repo_name ${WHITE}on GitHub ... "
          gh repo create "$repo_name" --$repo_visibility -c &>/dev/null;
          mv "$repo_name/.git" . && rm -rf "$repo_name";
          echo "${BOLD}${GREEN} ${WHITE}"
        elif [ "$create_repo" = "n" ];then
          function check_local(){
            echo -ne "${BOLD}${WHITE} Create ${GREEN}local  ${WHITE}repo ${LIGHT_BLUE}$repo_name ${WHITE}? (y/n) ";
            read create_local
            echo ${RESET}

            if [ "$create_local" = "y" ]; then
              git init &>/dev/null
            elif [ "$create_local" = "n" ];then
              return 0
            else
              check_local
            fi
          }
          check_local
        else
          check_create_repo
        fi
      }
      check_create_repo
    fi
  }

  # this alias to delete a github repo via Github CLI
  alias ghd="ghd"

  # this function for ghd alias
  # IMPROVED : 09-11-2024 16:13
  # Added has_remote check
  function ghd(){
    local is_a_git_repo=$(git rev-parse --is-inside-work-tree 2>/dev/null)

    if [[ "$is_a_git_repo" == "true" ]]; then
      local has_remote=$(git remote -v)

      if [ "$has_remote" ]; then
        local repo_url=$(git config --get remote.origin.url)
        local current_user=$(awk '/user:/ {print $2; exit}' ~/.config/gh/hosts.yml)
        local repo_owner=$(echo "$repo_url" | awk -F '[/:]' '{print $(NF-1)}')

        if [[ "$repo_owner" != "$current_user" ]]; then
          echo "${BOLD} ■■▶ Sorry, you are not the owner of this repo !" && br;
        else
          local repo_name="$(echo "$repo_url" | awk -F '/' '{print $NF}' | sed 's/.git$//')"
          local isPrivate=$(gh repo view $repo_name --json isPrivate --jq '.isPrivate')
          local repo_visibility=$([[ $isPrivate == "true" ]] && echo "private" || echo "public")

          function check_delete_local_repo(){
            echo -ne "${BOLD}${WHITE} Delete ${GREEN}local ${WHITE}repo ${LIGHT_BLUE}$repo_name ${WHITE}? (y/n) ";
            read delete_local_repo

            if [ "$delete_local_repo" = "y" ]; then
              local repo_source=$(git rev-parse --show-toplevel)
              # delete the repo
              echo -ne "${BOLD} Deleting ${GREEN}local ${WHITE}repo ${LIGHT_BLUE}$repo_name ${WHITE}... ";
              rm -rf $repo_source/.git;
              echo "${BOLD}${GREEN} ${WHITE}";
            elif [ "$delete_local_repo" = "n" ];then
              return 0
            else
              check_delete_local_repo
            fi
          }

          function check_delete_repo(){
            echo -ne "${BOLD}${WHITE} Delete ${GREEN}$repo_visibility ${WHITE}repo ${LIGHT_BLUE}$repo_name ${WHITE}? (y/n) ";
            read delete_repo
            if [ "$delete_repo" = "y" ]; then
              # delete the repo
              echo -ne "${BOLD} Deleting repository ${LIGHT_BLUE}$repo_name ${WHITE}on GitHub ... ";
              gh repo delete "$repo_name" --yes &>/dev/null;

              # remove the remote since we already
              # deleted it in GitHub
              git remote remove origin
              echo "${BOLD}${GREEN} ${WHITE}";
              echo -e;
              check_delete_local_repo
            elif [ "$delete_repo" = "n" ];then
              return 0
            else
              check_delete_repo
            fi
          }
          check_delete_repo
        fi
      else
        local repo_name=$(basename "$(git rev-parse --show-toplevel)")

        function check_delete_local_repo(){
          echo -ne "${BOLD}${WHITE} Delete ${GREEN}local ${WHITE}repo ${LIGHT_BLUE}$repo_name ${WHITE}? (y/n) ";
          read delete_local_repo
          if [ "$delete_local_repo" = "y" ]; then
            local repo_source=$(git rev-parse --show-toplevel)
            # delete the repo
            echo -ne "${BOLD} Deleting ${GREEN}local repo ${LIGHT_BLUE}$repo_name ${WHITE}... ";
            rm -rf $repo_source/.git;
            echo "${BOLD}${GREEN} ${WHITE}";
          elif [ "$delete_local_repo" = "n" ];then
            return 0
          else
            check_delete_local_repo
          fi
        }
        check_delete_local_repo
      fi
    else
      echo "${BOLD} ■■▶ This won't work, you are not in a git repo !" && br;
    fi
  }

  # this function to autocomplete
  # the branches of gbd alias
  function branch_delete_auto_complete(){
    local cur branches

    # Get the current word being completed
    cur="${COMP_WORDS[COMP_CWORD]}"

    # Get the list of branches from `git branch`
    branches=$(git branch --format '%(refname:short)')

    # Generate completions
    COMPREPLY=($(compgen -W "${branches}" -- "${cur}"))
  }

  # this alias to delete a branch
  alias gbd="gbd"

  # this function for gbd alias
  function gbd() {
    local is_a_git_repo=$(git rev-parse --is-inside-work-tree 2>/dev/null)
    local has_remote=$(git remote -v)

    if [[ "$is_a_git_repo" == "true" ]]; then
      local current_branch=$(git branch | awk '/\*/ {print $2}');
      local default_branch=$(git symbolic-ref refs/remotes/origin/HEAD 2>/dev/null | sed 's@^refs/remotes/origin/@@')

      if [[ -z "$default_branch" ]]; then
        default_branch=$(git config --get init.defaultBranch)
      fi

      if [[ $# -eq 1 ]]; then
        if [[ "$1" == "$default_branch" ]]; then
          echo "${BOLD} ■■▶ Fatal ! Cannot Delete the Default Branch " && br;
        elif ! git show-ref --verify --quiet "refs/heads/$1" &>/dev/null; then
          echo "${BOLD} ■■▶ Fatal ! Branch ${GREEN}$1 ${WHITE}doesn't exist ${RESET}" && br;
        else
          # this to check if we want to delete the remote branch too
          function check_delete_remote_branch() {
            if [[ "$current_branch" == "$default_branch" ]]; then
              echo "${BOLD} ■■▶ Fatal ! Cannot Delete the Default Branch " && br;
            else
              echo -ne "${BOLD}${WHITE}Delete remote branch${GREEN} "$current_branch"${WHITE} ? (y/n) ${RESET}";
              read delete_remote_branch
              echo ${RESET}
              if [ "$delete_remote_branch" = "y" ]; then
                git push origin --delete "$current_branch";
              elif [ "$delete_remote_branch" = "n" ];then
                return 0
              else
                check_delete_remote_branch
              fi
            fi
          }

          function check_delete_branch() {
            local branch_name="$1"

            echo -ne "${BOLD}${WHITE}Delete branch${GREEN} "$branch_name"${WHITE} ? (y/n) ${RESET}";
            read delete_branch

            if [ "$delete_branch" = "y" ]; then
              if [[ "$current_branch" != "$default_branch" ]]; then
                git checkout $default_branch &>/dev/null;
              fi
              if [ "$has_remote" ]; then
                local is_remote_branch=$(git branch -r | grep "origin/$1")
                if [ -n "$is_remote_branch" ]; then
                  check_delete_remote_branch
                fi
              fi
              git branch -D "$1";
            elif [ "$delete_branch" = "n" ]; then
              return 0;
            else
              check_delete_branch $branch_name
            fi
          }
          check_delete_branch $1
        fi
      elif [[ $# -eq 0 ]]; then
        if [[ "$current_branch" == "$default_branch" ]]; then
          echo "${BOLD} ■■▶ Fatal ! Cannot Delete the Default Branch " && br;
        else
          function check_delete_branch() {
            echo -ne "${BOLD}${WHITE}Delete branch${GREEN} "$current_branch"${WHITE} ? (y/n) ${RESET}";
            read delete_branch
            if [ "$delete_branch" = "y" ]; then
              # TODO : Remote branch Deletion
              function check_delete_remote_branch() {
                if [[ "$current_branch" == "$default_branch" ]]; then
                  echo "${BOLD} ■■▶ Fatal ! Cannot Delete the Default Branch " && br;
                else
                  echo -ne "${BOLD}${WHITE}Delete remote branch${GREEN} "$current_branch"${WHITE} ? (y/n) ${RESET}";
                  read delete_remote_branch
                  echo ${RESET}
                  if [ "$delete_remote_branch" = "y" ]; then
                    git push origin --delete "$current_branch";
                  elif [ "$delete_remote_branch" = "n" ];then
                    return 0
                  else
                    check_delete_remote_branch
                  fi
                fi
              }

              git checkout "$default_branch" &>/dev/null;

              if [ "$has_remote" ]; then
                local is_remote_branch=$(git branch -r | grep "origin/$current_branch")
                if [ -n "$is_remote_branch" ]; then
                  check_delete_remote_branch
                fi
              fi
              git branch -D "$current_branch";
            elif [ "$delete_branch" = "n" ];then
              return 0
            else
              check_delete_branch
            fi
          }
          check_delete_branch
        fi
      else
        echo "${BOLD} ■■▶ Usage : gbd branch_to_delete" && br;
      fi
    else
      echo "${BOLD} ■■▶ This won't work, you are not in a git repo !" && br;
    fi
  }

  # Register the completion function for `gbd`
  complete -F branch_delete_auto_complete gbd

  # this alias to change repo visibility
  alias ghv="ghv"

  # this function for ghv alias
  # IMPROVED : 06-06-2024 10:47
  function ghv(){
    local is_a_git_repo=$(git rev-parse --is-inside-work-tree 2>/dev/null)
    local has_remote=$(git remote -v)

    if [[ "$is_a_git_repo" == "true" ]]; then
      if [[ "$#" -eq 0 || "$1" == "show" || "$1" == "owner" ]]; then
        local current_user=$(awk '/user:/ {print $2; exit}' ~/.config/gh/hosts.yml)

        if [ "$has_remote" ]; then
          local repo_url=$(git config --get remote.origin.url)
          local repo_owner=$(echo "$repo_url" | awk -F '[/:]' '{print $(NF-1)}')
          local repo_name="$(echo "$repo_url" | awk -F '/' '{print $NF}' | sed 's/.git$//')"
        else
          local repo_owner=$(git config user.username)
          local repo_name=$(basename "$(git rev-parse --show-toplevel)")
        fi

        if [[ "$repo_owner" != "$current_user" && "$1" != "owner" ]]; then
          echo "${BOLD} ■■▶ Sorry, you are not the owner of this repo !" && br;
        elif [[ "$1" == "owner" ]]; then
          if [ "$has_remote" ]; then
            echo "${BOLD} The repo ${LIGHT_BLUE}$repo_name ${WHITE}is owned by ${GREEN}$repo_owner";
          else
            echo "${BOLD} The local repo ${LIGHT_BLUE}$repo_name ${WHITE}is owned by ${GREEN}$repo_owner";
          fi
        else
          if [ "$has_remote" ]; then
            local isPrivate=$(gh repo view $repo_name --json isPrivate --jq '.isPrivate')

            if [[ "$1" == "show" ]]; then
              local visibility=$([[ $isPrivate == "true" ]] && echo "private" || echo "public")
              echo "${BOLD} This repo ${LIGHT_BLUE}$repo_name ${WHITE}is ${GREEN}$visibility";
            else
              local new_visibility=$([[ $isPrivate == "true" ]] && echo "public" || echo "private")
              function toggle_visibility(){
                echo -ne "${BOLD}${WHITE} Make ${LIGHT_BLUE}$repo_name ${WHITE}repo ${GREEN}$new_visibility ${WHITE}? (y/n) ";
                read change_visibility
                if [ "$change_visibility" = "y" ]; then
                  # toggle visibility
                  echo -ne "${BOLD} Changing repo visibility to ${GREEN}$new_visibility ${WHITE}... ";
                  gh repo edit "$repo_owner/$repo_name" --visibility "$new_visibility" &>/dev/null;
                  echo "${BOLD}${GREEN} ${WHITE}";
                elif [ "$change_visibility" = "n" ];then
                  return 0
                else
                  toggle_visibility
                fi
              }
              toggle_visibility
            fi
          else
            echo "${BOLD} The local repo ${LIGHT_BLUE}$repo_name ${WHITE}is owned by ${GREEN}$repo_owner";
          fi
        fi
      else
        echo "${BOLD} ■■▶ Sorry, wrong command argument !" && br;
      fi
    else
      echo "${BOLD} ■■▶ This won't work, you are not in a git repo !" && br;
    fi
  }

  # Completion function for ghv
  # 07-31-2024 00:30
  _ghv_completion() {
    local cur prev opts
    cur="${COMP_WORDS[COMP_CWORD]}"
    prev="${COMP_WORDS[COMP_CWORD-1]}"
    opts="show owner"

    if [[ ${COMP_CWORD} -eq 1 ]]; then
        # Complete the options
        COMPREPLY=($(compgen -W "$opts" -- "$cur"))
    else
        # No further completion needed
        COMPREPLY=()
    fi
  }

  # Register the completion function for ghv
  complete -F _ghv_completion ghv

  #this alias to view all repos in the GitHub
  alias ghls="gh repo list -L 1000"

  # this function to check if a username exists on github
  # INSPIRED FROM : https://gist.github.com/RitheeshBaradwaj/22eafb0c33acf42af4db000366343d63
  # 06-04-2024 19:48
  function is_a_github_user() {
    username="$1"

    # Check if username is empty
    if [[ -z "$username" ]]; then
      return 1
    fi

    # Build the API URL
    url="https://api.github.com/users/$username"

    # Use wget to capture the response (redirecting output to a variable)
    # wget by default outputs content, so we use the -q (quiet) option to suppress it
    # -O- option specifies that the downloaded content should be written
    # to standard output (stdout) instead of a file.
    response=$(wget -qO- --no-check-certificate "$url")

    # Check if there is no output
    # meaning it is not found
    if [[ -z "$response" ]]; then
      # Not Found
      return 1
    else
      # Found
      return 0
    fi
  }

  # this alias to add collaborator to the repo
  alias ghadd="ghadd"

  # this function for ghadd alias
  # INSPIRED FROM : https://github.com/cli/cli/issues/2807
  # 06-04-2024 19:23
  # Uses the github cli rest API
  function ghadd(){
    local is_a_git_repo=$(git rev-parse --is-inside-work-tree 2>/dev/null)
    local has_remote=$(git remote -v)

    if [[ "$is_a_git_repo" == "true" ]]; then
      if [ "$has_remote" ]; then
        if [[ $# -eq 0 ]]; then
          echo "${BOLD} ■■▶ Specify the username of the new collaborator !" && br;
        elif [[ $# -gt 0 ]]; then
          local current_user=$(awk '/user:/ {print $2; exit}' ~/.config/gh/hosts.yml)
          local repo_url=$(git config --get remote.origin.url)
          local repo_owner=$(echo "$repo_url" | awk -F '[/:]' '{print $(NF-1)}')
          local repo_name="$(echo "$repo_url" | awk -F '/' '{print $NF}' | sed 's/.git$//')"

          # check if we are not the owner of the repo
          if [[ "$repo_owner" != "$current_user" ]]; then
            echo "${BOLD} ■■▶ Sorry, you are not the owner of this repo !" && br;
          else
            # Loop through each collaborator username provided as an argument
            for collaborator in "$@"; do
              echo -ne "${BOLD} Inviting ${LIGHT_BLUE}$collaborator ${WHITE}to collaborate on ${LIGHT_BLUE}$repo_name${WHITE} "

              # Check if the collaborator exists on GitHub
              if is_a_github_user "$collaborator"; then
                # Add collaborator using gh api
                gh api --method=PUT "repos/$current_user/$repo_name/collaborators/$collaborator" &>/dev/null
                echo "${BOLD}${GREEN} ${WHITE}"
              else
                echo "${BOLD}${RED}✘ ${WHITE}"
              fi
            done
          fi
        fi
      else
        echo "${BOLD} ■■▶ This repo has no remote on GitHub !" && br;
      fi
    else
      echo "${BOLD} ■■▶ This won't work, you are not in a git repo !" && br;
    fi
  }

  # this alias to delete a contributor
  alias ghdel="ghdel"

  # this function for ghdel alias
  # IMPROVED : 06-04-2024 23:52
  # Derived from ghadd
  function ghdel(){
    local is_a_git_repo=$(git rev-parse --is-inside-work-tree 2>/dev/null)
    local has_remote=$(git remote -v)

    if [[ "$is_a_git_repo" == "true" ]]; then
      if [ "$has_remote" ]; then
        if [[ $# -eq 0 ]]; then
          echo "${BOLD} ■■▶ Specify the username of the collaborator to remove !" && br;
        elif [[ $# -gt 0 ]]; then
          local current_user=$(awk '/user:/ {print $2; exit}' ~/.config/gh/hosts.yml)
          local repo_url=$(git config --get remote.origin.url)
          local repo_owner=$(echo "$repo_url" | awk -F '[/:]' '{print $(NF-1)}')
          local repo_name="$(echo "$repo_url" | awk -F '/' '{print $NF}' | sed 's/.git$//')"

          # check if we are not the owner of the repo
          if [[ "$repo_owner" != "$current_user" ]]; then
            echo "${BOLD} ■■▶ Sorry, you are not the owner of this repo !" && br;
          else
            # Retrieve the list of collaborators
            local collaborators=$(gh api "repos/$current_user/$repo_name/collaborators" --jq '.[].login')
            local invitations=$(gh api "repos/$current_user/$repo_name/invitations" --jq '.[].invitee.login')

            # Loop through each collaborator username provided as an argument
            for collaborator in "$@"; do
              # Check if the collaborator exists in the list of collaborators
              if echo "$collaborators" | grep -q "$collaborator" ||
                echo "$invitations" | grep -q "$collaborator"; then
                echo -ne "${BOLD} Removing ${LIGHT_BLUE}$collaborator ${WHITE}from ${LIGHT_BLUE}$repo_name${WHITE} "
                # Check for pending invitations
                local invitation_id=$(gh api "repos/$current_user/$repo_name/invitations" --jq ".[] | select(.invitee.login==\"$collaborator\") | .id")

                if [[ -n "$invitation_id" ]]; then
                  # Delete the pending invitation
                  gh api --method=DELETE "repos/$current_user/$repo_name/invitations/$invitation_id" &>/dev/null
                  echo -ne " ${BOLD}(invitation deleted) "
                fi

                # Remove collaborator using gh api
                gh api --method=DELETE "repos/$current_user/$repo_name/collaborators/$collaborator" &>/dev/null
                echo "${BOLD}${GREEN} ${WHITE}"
              else
                echo "${BOLD}${LIGHT_BLUE}$collaborator ${WHITE}is not a ${LIGHT_BLUE}collaborator ${RED}✘ ${WHITE}"
              fi
            done
          fi
        fi
      else
        echo "${BOLD} ■■▶ This repo has no remote on Github !" && br;
      fi
    else
      echo "${BOLD} ■■▶ This won't work, you are not in a git repo !" && br;
    fi
  }

  # Completion function for ghdel
  _ghdel_completion() {
    local cur prev opts
    cur="${COMP_WORDS[COMP_CWORD]}"
    prev="${COMP_WORDS[COMP_CWORD-1]}"

    if [[ ${COMP_CWORD} -eq 1 ]]; then
      # Ensure we are in a git repository
      local is_a_git_repo=$(git rev-parse --is-inside-work-tree 2>/dev/null)
      if [[ "$is_a_git_repo" == "true" ]]; then
        local current_user=$(awk '/user:/ {print $2; exit}' ~/.config/gh/hosts.yml)
        local repo_url=$(git config --get remote.origin.url)
        local repo_owner=$(echo "$repo_url" | awk -F '[/:]' '{print $(NF-1)}')
        local repo_name="$(basename "$repo_url" .git)"

        # Fetch collaborators and invitees
        local collaborators=$(gh api "repos/$repo_owner/$repo_name/collaborators" --jq '.[].login')
        local invitations=$(gh api "repos/$repo_owner/$repo_name/invitations" --jq '.[].invitee.login')

        # Combine collaborators and invitees into a single list
        local all_users=$(echo "$collaborators" "$invitations" | tr ' ' '\n' | sort | uniq)

        # Provide completion suggestions
        COMPREPLY=($(compgen -W "$all_users" -- "$cur"))
      else
        echo "Not inside a git repository."
      fi
    else
      COMPREPLY=()
    fi
  }

  # Register the completion function for ghdel
  # complete -F _ghdel_completion ghdel

  # this alias to list all collaborators
  alias ghcls="ghcls"

  # this function for ghcls alias
  # IMPROVED : 06-04-2024 23:52
  # Derived from ghadd
  function ghcls(){
    local is_a_git_repo=$(git rev-parse --is-inside-work-tree 2>/dev/null)
    local has_remote=$(git remote -v)

    if [[ "$is_a_git_repo" == "true" ]]; then
      if [ "$has_remote" ]; then
        local current_user=$(awk '/user:/ {print $2; exit}' ~/.config/gh/hosts.yml)
        local repo_url=$(git config --get remote.origin.url)
        local repo_owner=$(echo "$repo_url" | awk -F '[/:]' '{print $(NF-1)}')
        local repo_name="$(echo "$repo_url" | awk -F '/' '{print $NF}' | sed 's/.git$//')"

        # check if we are not the owner of the repo
        if [[ "$repo_owner" != "$current_user" ]]; then
          echo "${BOLD} ■■▶ Sorry, you are not the owner of this repo !" && br;
        else
          echo -ne "${BOLD} ${LIGHT_BLUE}Collaborators ${WHITE}for the ${LIGHT_BLUE}$repo_name ${WHITE}repository "

          # List collaborators using gh api
          local collaborators=$(gh api "repos/$current_user/$repo_name/collaborators" --jq '.[].login')
          local invitations=$(gh api "repos/$current_user/$repo_name/invitations" --jq '.[].invitee.login')

          local collaborators_count=$(echo "$collaborators" | wc -l)
          local invitations_count=$(echo "$invitations" | wc -l)
          local collaborators_num=$((collaborators_count + invitations_count))
          echo "${WHITE}${BOLD}($collaborators_count)"

          # Iterate through each collaborator
          if [[ -n "$collaborators" ]]; then
            while IFS= read -r collaborator; do
              if [[ "$collaborator" == "$current_user" ]]; then
                echo " ● $collaborator (owner)"
              else
                echo " ● $collaborator"
              fi
            done <<< "$collaborators"
          else
            echo "No collaborators found."
          fi

          # Check if there are pending invitations
          if [[ -n "$invitations" ]]; then
            # Print pending invitations
            while IFS= read -r invitee; do
              echo " ● $invitee (invitation pending)"
            done <<< "$invitations"
          fi
        fi
      else
        echo "${BOLD} ■■▶ This repo has no remote on GitHub !" && br;
      fi
    else
      echo "${BOLD} ■■▶ This won't work, you are not in a git repo !" && br;
    fi
  }

  #######################################################################
  ```
</details>

<details>
  <summary><strong> Services Aliases</strong></summary>

  ```sh
  ### Services Aliases

  # this alias to start services
  alias svc_on="allow_sudo && svc_on"

  # this function for svc_on alias
  function svc_on(){
    sudo service "$1" start;
  }

  # this alias to stop systemctl based services
  alias svc_off="allow_sudo && svc_off"

  # this function for svc_off alias
  function svc_off(){
    sudo service "$1" stop;
  }

  # this alias to view systemctl
  # based services status
  alias svc_stat="allow_sudo && svc_stat"

  # this function for svc_stat alias
  function svc_stat(){
    sudo service "$1" status;
  }

  # this alias to show if a service if on or off
  alias svc_show_stat="allow_sudo && svc_show_stat"

  # this function for svc_show_stat alias
  function svc_show_stat(){
    br;

    local service_name="$1";
    local check_command="$2";

    if [[ "$check_command" == *"Active: active"* ]]; then
      echo "${BOLD}$service_name Active [${GREEN}✓${WHITE}]";
    elif [[ "$check_command" =~ ^[0-9]+$ ]]; then
      echo "${BOLD}$service_name Active [${GREEN}✓${WHITE}]";
    else
      echo "${BOLD}$service_name Off [${RED}x${WHITE}]";
    fi

    br;
  }

  # this alias to view the ssh server status
  alias sth="sth"

  # this function for sth alias
  function sth(){
    c && br;
    if [[ $(pgrep sshd) ]]; then
      c && br;
      echo "${BOLD}Ssh Server Active [${GREEN}✓${WHITE}]"
      br;

      local is_wsl=$(grep -qi microsoft /proc/version && echo true || echo false)

      if $is_wsl; then
       local wifi_iface="wifi0"
      else
       # at least it is on kali linux
       local wifi_iface="wlan0"
      fi

      local wifi_ip=$(ifconfig $wifi_iface | grep inet | awk '{print $2}');
      # echo " Connect Via  ==>  ssh $USER@$ip";
      # check_ngrok="cmd.exe /c 'tasklist | findstr /I "ngrok"'"
      echo "Ssh Connection via $wifi_iface Interface";
      echo "${BOLD}${WHITE}==> ssh $USER@$wifi_ip";
    else
      echo "${BOLD}Ssh Server Off [${RED}x${WHITE}]"
    fi
  }

  # this alias to enable the ssh server
  alias sshon="allow_sudo && sshon"

  # this function for sshon alias
  function sshon(){
    local is_wsl=$(grep -qi microsoft /proc/version && echo true || echo false)

    if $is_wsl; then
      sudo /etc/init.d/ssh start &>/dev/null;
    else
      svc_on ssh;
    fi
    sth;
  }

  # this alias to kill the ssh server process
  alias sshoff="allow_sudo && sshoff"

  # this function for sshoff alias
  function sshoff(){
    # sudo /etc/init.d/ssh stop;
    if [[ $(pgrep sshd) ]]; then
      sudo kill $(pgrep sshd);
    fi
    sth;
  }

  # this function to view the current apache2
  # service, its status
  function stap(){
    c && br;
    if [[ $(pgrep apache2) ]]; then
      echo "${BOLD}Apache Server Active [${GREEN}✓${WHITE}]"
      br;

      local eth_iface="eth0"

      if $is_wsl; then
        local wifi_iface="wifi0"
      else
        # at least it is on kali linux
        local wifi_iface="wlan0"
      fi
      
      local loopback_iface="lo"
      local wlan_ip=$(ifconfig $wifi_iface | grep "inet " | awk '{print $2}');
      local loopback_ip=$(ifconfig $loopback_iface | grep "inet " | awk '{print $2}');

      echo "$wifi_iface Interface Connection (Public)  : ${BRIGHT_BLUE}http://$wlan_ip${WHITE}";
      echo "$loopback_iface    Interface Connection (Private) : ${BRIGHT_BLUE}http://$loopback_ip ${WHITE}";
      br;
    else
      echo "${BOLD}Apache Server Off [${RED}x${WHITE}]"
      br
    fi
  }

  # this alias to start the apache2 service
  alias apon="allow_sudo && apon"

  # this function for apch alias
  function apon(){
    cd /var/www/html;
    c && br;
    echo "${BOLD}[${GREEN}+${WHITE}]${WHITE} Starting Apache Server ..."; br;
    sudo service apache2 start &>/dev/null;
    stap;
  }

  # this alias to stop the apache2 service
  alias apoff="allow_sudo && apoff"

  # this function for apch alias
  function apoff(){
    sudo service apache2 stop;
    stap;
  }

  # this alias to open the
  # Apache2 server directory
  alias apd="apd"

  # this function for apd alias
  function apd(){
    op /var/www/html
  }

  # this alias to start the sql service
  alias sqlon="allow_sudo && sqlon"

  # this function for sqlon alias
  function sqlon(){
    sudo service mariadb start;
    sqls;
  }

  # this alias to stop the sql service
  alias sqloff="allow_sudo && sqloff"

  # this function for sqloff alias
  function sqloff(){
    sudo service mariadb stop;
    sqls;
  }

  # this alias to view the sql service
  alias sqls="allow_sudo && sqls"

  # this function for sqloff alias
  function sqls(){
    c && br;
    if [[ $(pgrep mariadb) ]]; then
      echo "${BOLD}MySQL Server Active [${GREEN}✓${WHITE}]"
    else
      echo "${BOLD}MySQL Server Down [${RED}x${WHITE}]"
    fi
  }

  # this alias to start the postgresql service
  alias psqlon="allow_sudo && psqlon"

  # this function for sqlon alias
  function psqlon(){
    if [[ $(pgrep postgres) ]]; then
      sudo -u postgres psql;
    else
      c && br;
      echo "${BOLD}${WHITE}[${GREEN}+${WHITE}] Starting ${WHITE}PostgreSQL Server ...";
      sudo service postgresql start &>/dev/null;
      c && br;
      echo "${BOLD}PostgreSQL Server Active [${GREEN}✓${WHITE}]";
      br;

      function check_postgres_shell(){
        echo -ne "${BOLD}${WHITE}Access PostgreSQL${GREEN} Shell${WHITE} ? (y/n) ";
        read postgres_shell
        if [ "$postgres_shell" = "y" ]; then
          clear;
          sudo su - postgres;
        elif [ "$postgres_shell" = "n" ];then
          return 1
        else
          check_postgres_shell
        fi
      }
      check_postgres_shell
    fi
    return 0
  }

  # this alias to stop the postgresql service
  alias psqloff="allow_sudo && psqloff"

  # this function for sqloff alias
  function psqloff(){
    c && br;
    echo "${BOLD}${WHITE}[${RED}x${WHITE}] Stopping ${WHITE}PostgreSQL Server ...";
    sudo service postgresql stop &>/dev/null;
    psqls;
  }

  # this alias to view the postgresql service
  alias psqls="allow_sudo && psqls"

  # this function for psqls alias
  function psqls(){
    c && br;

    if [[ $(pgrep postgres) ]]; then
      echo "${BOLD}PostgreSQL Server Active [${GREEN}✓${WHITE}]";
    else
      echo "${BOLD}PostgreSQL Server Off [${RED}x${WHITE}]";
    fi

    br;
  }

  # this alias to start the web servers
  alias webon="allow_sudo && webon"

  # this function for webon alias
  function webon(){
    c && br;
    echo "${BOLD}${WHITE} Starting Web Servers"; br;

    # Apache Server
    echo -ne "${BOLD}${WHITE} ==> Starting ${GREEN}Apache ${WHITE}Server ..."
    sudo service apache2 start &>/dev/null;
    echo -e "[${GREEN}✓${WHITE}]";

    # MySQL Server
    echo -ne "${BOLD} ==> Starting ${GREEN}MySQL ${WHITE} Server ..."
    sudo service mariadb start &>/dev/null;
    echo -e "[${GREEN}✓${WHITE}]";

    # Postfix Server
    echo -ne "${BOLD} ==> Starting ${GREEN}Mail ${WHITE}  Server ..."
    sudo service postfix start &>/dev/null;
    echo -e "[${GREEN}✓${WHITE}]";

    # Status
    br;
    local eth_iface="eth0"
    local is_wsl=$(grep -qi microsoft /proc/version && echo true || echo false)

    if $is_wsl; then
      local wifi_iface="wifi0"
    else
      # at least it is on kali linux
      local wifi_iface="wlan0"
    fi

    local loopback_iface="lo"
    local wlan_ip=$(ifconfig $wifi_iface | grep "inet " | awk '{print $2}');
    local loopback_ip=$(ifconfig $loopback_iface | grep "inet " | awk '{print $2}');

    echo "${BOLD} Access the Server"; br;
    echo " ==> WAN : ${BRIGHT_BLUE}http://$wlan_ip${WHITE}";
    echo " ==> LAN : ${BRIGHT_BLUE}http://$loopback_ip ${WHITE}";
    br;
  }

  # this alias to stop the web servers
  alias weboff="allow_sudo && weboff"

  # this function for weboff alias
  function weboff(){
    c && br;
    echo "${BOLD}${WHITE} Stopping Web Servers"; br;

    # Apache Server
    echo -ne "${BOLD}${WHITE} ==> Stopping ${RED}Apache ${WHITE}Server ..."
    sudo service apache2 stop &>/dev/null;
    echo -e "[${RED}x${WHITE}]";

    # MySQL Server
    echo -ne "${BOLD} ==> Stopping ${RED}MySQL ${WHITE} Server ..."
    sudo service mariadb stop &>/dev/null;
    echo -e "[${RED}x${WHITE}]";

    # Postfix Server
    echo -ne "${BOLD} ==> Stopping ${RED}Mail ${WHITE}  Server ..."
    sudo service postfix stop &>/dev/null;
    echo -e "[${RED}x${WHITE}]";

    # Status
    br;
  }

  # this alias to view the web servers status
  alias webs="allow_sudo && webs"

  # this function for webs alias
  function webs(){
    c && br;
    echo "${BOLD} Web Servers Status"; br;

    function check_web(){
      local server_name="$1";
      local app_service="$2";
      local color;
      local sign;

      if sudo service $app_service status &>/dev/null; then
        color="${GREEN}";
        sign="✓";
      else
        color="${RED}";
        sign="x";
      fi

      echo "${BOLD} ==> $server_name Server $color$switch${WHITE}... [$color$sign${WHITE}]";
    }

    # Check apache server
    check_web "Apache" apache2
    check_web "MySQL " mariadb
    check_web "Mail  " postfix

    if sudo service apache2 status &>/dev/null; then
      br;
      local eth_iface="eth0"
      local is_wsl=$(grep -qi microsoft /proc/version && echo true || echo false)

      if $is_wsl; then
        local wifi_iface="wifi0"
      else
        # at least it is on kali linux
        local wifi_iface="wlan0"
      fi

      local loopback_iface="lo"
      local wlan_ip=$(ifconfig $wifi_iface | grep "inet " | awk '{print $2}');
      local loopback_ip=$(ifconfig $loopback_iface | grep "inet " | awk '{print $2}');

      echo "${BOLD} Access the Server"; br;
      echo " ==> WAN : ${BRIGHT_BLUE}http://$wlan_ip${WHITE}";
      echo " ==> LAN : ${BRIGHT_BLUE}http://$loopback_ip ${WHITE}";
      br;
    fi
  }

  # this alias to start the sql cli
  alias rdb="allow_sudo && rdb"

  # this function for rdb alias
  function rdb(){
    if ! pgrep mariadb > /dev/null; then
      sudo service mariadb start &>/dev/null
    fi
    c && br
    local user=${1:-root}
    echo "${BOLD}MySQL Server Active [${GREEN}✓${WHITE}]"
    echo "${BOLD}User : $user"
    local is_root='[[ "$user" == "root" ]]';
    local flag=$(eval "$is_root" && echo "" || echo "-p");
    sudo mysql -u $user $flag;
    br
    function check_mysql_server(){
      echo -ne "${BOLD}${WHITE}[${GREEN}?${WHITE}]${WHITE} ${GREEN}Stop ${WHITE}MySQL Server ? (y/n) ";
      read server
      if [ "$server" = "y" ]; then
        # echo -ne " ${WHITE}[${GREEN}+${WHITE}]${WHITE} Stopping ${GREEN}MySQL ${WHITE}Server  ";
        echo "${BOLD}${WHITE}[${GREEN}+${WHITE}]${WHITE} Stopping MySQL Server ... "
        sudo service mariadb stop &>/dev/null
        echo "${BOLD}${WHITE}[${GREEN}+${WHITE}]${WHITE} MySQL Server Stopped  ... ${GREEN}✓"
      elif [ "$server" = "n" ];then
        echo "${BOLD}${WHITE}[${GREEN}+${WHITE}]${WHITE} Keeping ${GREEN}MySQL ${WHITE}Server ${GREEN}On";
      else
        check_mysql_server
      fi
    }
    check_mysql_server
  }

  # this alias to start the sql cli
  alias rdbp="rdbp"

  # this function for rdbp alias
  function rdbp(){
    clear && br 2 && sudo clear;
    sudo systemctl start psql;
    sudo mysql -u root;
    sudo systemctl stop psql;
  }

  # this alias to check sendmail process
  alias mails="allow_sudo && mails"

  # this function for mails alias
  function mails(){
    c && br;
    if sudo service postfix status &>/dev/null; then
      echo "${BOLD}Mail Server Active [${GREEN}✓${WHITE}]"
    else
      echo "${BOLD}Mail Server Down [${RED}x${WHITE}]"
    fi
  }

  # this alias to start sendmail service
  alias mailon="allow_sudo && mailon"

  # this function for mailon alias
  function mailon(){
    sudo service postfix start
    mails
  }

  # this alias to stop sendmail service
  alias mailoff="allow_sudo && mailoff"

  # this function for mailon alias
  function mailoff(){
    sudo service postfix stop
    mails
  }

  # this alias to check snmp service
  alias snmps="snmps"

  # this function for snmps alias
  function snmps(){
    local name="SNMP Server";
    local cmd="$(pgrep snmpd)";
    svc_show_stat $name $cmd;
  }

  # this function to start snmpd service
  alias snmpon="snmpon"

  # this function for snmpon alias
  function snmpon(){
    svc_on snmpd;
    snmps;
  }

  # this alias to stop the snmp service
  alias snmpoff="snmpoff"

  # this function for snmpoff alias
  function snmpoff(){
    svc_off snmpd;
    snmps;
  }

  #######################################################################
  ```
</details>

<details>
  <summary><strong> File Aliases</strong></summary>

  ```sh
  ### File Aliases

  # this alias to create a file
  alias tf="tf"

  # this function for tf alias
  function tf(){
    touch "$@" && all "$@" && cv;
  }

  # this alias to delete file
  alias dlf="dlf"

  # this function for dlf alias
  function dlf(){
    rm "$@" && cv;
  }

  # this alias to copy a file then display it
  alias cpf="cpf"

  # this function for cpf alias
  function cpf(){
    if [[ $# -eq 2 ]]; then
      if [[ -d "$1" ]]; then #here to check if the first argument is a directory
        cp -r "$1" "$2" && op "$2" && all "$1";
      else
        cp "$1" "$2" && op "$2" && all "$1";
      fi
    elif [[ $# -eq 1 ]]; then
      if [[ -d "$1" ]]; then #here to check if the first argument is a directory
        cp -r "$1" "$dest" && op "$dest" && all "$1";
      else
        cp "$@" "$dest" && op "$dest" && all "$@";
      fi
    fi
  }

  # this alias to copy the content of a file
  alias cnf="cnf"

  # this function for cnf alias
  function cnf(){
    cat "$1" > "$2" && dlf "$1" && all "$2";
  }

  # this alias to copy a file then display it
  alias mvf="mvf"

  # this function for cpf alias
  function mvf(){
    if [[ $# -eq 2 ]]; then
      mv "$1" "$2" && op "$2";
    elif [[ $# -eq 1 ]]; then
      mv $@ $dest && op $dest;
      # if there is only one argument,
      # it will move the file / directory
      # to the the variable
      # dest defined in dt alias
    fi
  }

  # this alias to force delete
  alias rdf="allow_sudo && rdf"

  # this function for rdf alias
  function rdf(){
    sudo rm -rfv "$@";
    cv;
  }

  # this alias to count the number of file/directory
  # inside a directory
  alias dc="dc"

  #this function for dc alias
  function dc(){
    if [[ $# -eq 0 ]]; then
      clear;
      br;
      case "$(ls -1 | wc -l)" in
        0)
          br;
          echo "There is nothing inside $(basename $PWD)";
          br;;
        *)
          case "$(ls -1 | wc -l)" in
            1)it="item";;
            *)it="items";;
          esac
          echo "   $(basename $PWD) folder has $(ls -1 | wc -l) $it : ";
          br;
          if [[ $(ls -1 | wc -l) -gt 50 ]]; then
            br;
          else
            ls
          fi
          br;
      esac
    elif [[ $# -eq 1 ]]; then
      clear;
      br;
      case "$(ls -1 $1 | wc -l)" in
        0)
          br;
          echo "There is nothing inside $(basename $1)";
          br;
          sleep 1;
          cv;
          br;;
        *)
          case "$(ls -1 $1 | wc -l)" in
            1)it="item";;
            *)it="items";;
          esac
          echo "   $(basename $1) folder has $(ls -1 $1 | wc -l) $it : ";
          br;
          if [[ $(ls -1 "$1" | wc -l) -gt 50 ]]; then
            br;
          else
            ls "$1";
          fi
          br;
          sleep 1;
          cv;
      esac
    fi
  }

  # this alias to know the file type
  alias tp="tp"

  # this function for tp alias
  function tp(){
    type=$(ls -ld "$1" | cut -c1)
    case $type in
      -) echo "File" ;;
      d) echo "Directory" ;;
      b) echo "Block" ;;
      l) echo "Sym-Link" ;;
      c) echo "Character" ;;
      *) echo "Other" ;;
    esac
  }

  #######################################################################
  ```
</details>

<details>
  <summary><strong> Explorer Alias</strong></summary>

  ```sh
  ### Explorer Alias

  # this alias to open the current
  # directory inside windows explorer
  # or bu the default explorer on Linux
  alias exop="exop"

  # this function for exop alias
  function exop() {
    [ $# -eq 1 ] && cd "$1"

    # check WSL
    local is_wsl=$(
      grep -qi microsoft /proc/version && echo true || echo false
    )

    if $is_wsl; then
      explorer.exe .
    else
      xdg-open .
    fi
    cv
  }

  #######################################################################
  ```
</details>

<details>
  <summary><strong> Custom command not found</strong></summary>

  ```sh
  ### Custom command not found

  # Printing command not found when it is the case
  command_not_found_handler() {
    local command=$1
    local command_found=0

    # Check if the command is found in the .zshrc file
    if grep -q -E "^alias $command=" "$HOME/.zshrc" ; then
      command_found=1
    fi

    if [[ $command_found -eq 0 ]]; then
      echo " ${BOLD}${WHITE}[${RED}x${WHITE}]${WHITE} Command Not Found"
    fi
  }

  #######################################################################
  ```
</details>

<details>
  <summary><strong> $SHELLrc Aliases</strong></summary>

  ```sh
  ### $SHELLrc Aliases

  # this alias to edit $SHELLrc
  alias ct="nvim ~/.zshrc"

  # this alias to reload the zshrc file
  alias rld="rld"

  # this function for rld alias
  function rld(){
    c;

    # local variables
    local shellrc=.$(basename $SHELL)rc;
    local is_wsl=$(grep -qi microsoft /proc/version && echo true || echo false)
    local platform=$($is_wsl && echo "wsl" || echo "linux")
    local backup_dir=$HOME/NTSOA/zshrc/$platform;
    local backup_file=zshrc[$USER];
    local saved_message="$shellrc backed up"

    # source the config file and save it
    source ~/$shellrc;
    cat ~/$shellrc > $backup_dir/$backup_file;

    # saved message display
    c && br;
    echo "${BOLD}${WHITE}$saved_message";
    br && sleep 0.5;
    op $backup_dir;
  }

  #######################################################################
  ```
</details>

<details>
  <summary><strong> Neovim Aliases</strong></summary>

  ```sh
  ### Neovim Aliases

  # this alias to open the current directory inside neovim
  alias nvm="nvm"

  # this function for nvm aliases
  # if we have one argument then nvim will be launched with it,
  # otherwise open the current directory if there is no argument
  function nvm(){
    nvim "${1:-.}";
  }

  # this alias to call neovim in a cooler way
  alias hnvim="nvim"

  # this alias to open nvim as root
  alias nvmr="allow_sudo && nvmr"

  # this function for nvmr alias
  function nvmr(){
    sudo nvim "${1:-.}";
  }

  # this alias to edit a file
  alias ed="ed"

  # this function for ed alias
  function ed(){
    # nvim -c "startinsert" "$1" && cv;
    nvim "$1" && cv;
  }

  #######################################################################
  ```
</details>

<details>
  <summary><strong> Linux Network Aliases</strong></summary>

  ```sh
  ### Kali Linux Network Aliases

  # this function to switch from ethernet to wireless connection
  function wf(){
    c && br 2;
    sudo clear;
    br 2;
    if [ -d /sys/class/net/wlan0 ]; then
      downnet eth0 && upnet wlan0;
      echo "w i r e l e s s" | figlet -t -c;
      tlk "wifi on";
      br && sleep 1 && cv;
    else
      echo "Can't switch to wireless, wlan0 not found";
      br;
    fi
  }

  # this function to bring a connection interface up 
  function upnet(){
    sudo ifconfig "$1" up;
  }

  # this function to bring a connection interface down 
  function downnet(){
    sudo ifconfig "$1" down;
  }

  # this alias to show the network configuration
  alias ipsh="ipsh"

  # this function for ntsh alias
  function ipsh(){
    c && br;
    echo "  Available IP Adresses : ";
    br;
    # ifconfig wlan0;
    # br;
    local eth_ip=$(ifconfig eth0 | grep "inet " | awk '{print $2}');

    # Add a conditon to make it view
    # IP from interface passed as argument
    if [[ $# -eq 1 ]]; then
      local iface_ip=$(ifconfig "$1" | grep "inet " | awk '{print $2}');
      echo " $1 ==> $iface_ip";
    else
      if [ -d /sys/class/net/wlan0 ]; then
        local wlan_ip=$(ifconfig wlan0 | grep "inet " | awk '{print $2}');
        echo " wlan0 ==> $wlan_ip";
        echo " eth0  ==> $eth_ip" && br;
      else
        echo " eth0 IP ==> $eth_ip" && br;
      fi
    fi

    # ifconfig | awk -F '[ :]+' '/^[a-z]/ {interface=$1} /inet / {print interface " ==> " $3}'
  }

  # this alias to list the local IP adresses
  alias ipls="ipls"

  # this function for ipls alias
  function ipls(){
    c && br;
    echo "   Local Devices IP Adresses : ";
    br;
    arp -e;
    br;
  }

  # this alias to show the network configuration
  alias ntsh="ntsh"

  # this function for ntsh alias
  function ntsh(){
    c && br;

    if [ -d /sys/class/net/wlan0 ]; then
      echo "      Wireless Network informations : ";
      if [[ $# -eq 0 ]]; then
        br;
        iwconfig wlan0 | grep "Mode" | awk -F ":" '{print $2}' | grep M | awk '{print "wlan0 Mode ==> " $1}';
        br;
      elif [[ $# -eq 1 ]]; then
        br && iwconfig "$1" && br;
      fi
    else
      echo "No Wireless adapter found" && br;
    fi
  }

  # this alias to define the type of the wireless adapter
  alias wtp="wtp"

  # this function for wtp alias
  function wtp(){
    if [[ $# -eq 2 ]]; then
      sudo ip link set "$1" down;
      sudo iw "$1" set type "$2";
      sudo ip link set "$1" up;
    else
      c && br 2;
      echo "Invalid Argument" | figlet -t -c;
      br;
    fi
  }

  # this alias to scan wifi
  alias scn="scn"

  # this function for scn alias
  function scn(){
    c && br 2 && sudo clear;
    wtp wlan0 monitor;
    br 2;
    echo "s c a n n  i n g . . ." | figlet -t -c | lolcat;
    sleep 1;
    sudo airodump-ng wlan0;
    wtp wlan0 managed;
    br;
  }

  # this function to kill process
  function kl(){
    if pgrep -f "$1">/dev/null; then
      sudo kill $(pgrep "$1");
    fi
  }

  # this alias to switch to monitor mode
  alias mntr="mntr"

  # this function for mntr alias
  function mntr(){
    c && br 2;
    sudo clear;

    if [ -d /sys/class/net/wlan0 ]; then
      c && br 2 && sudo clear;
      kl NetworkManager;
      kl wpa_supplicant;
      kl dhclient;
      sudo airmon-ng start wlan0 && c;
      echo "M o n i t o r" | figlet -t -c;
      sleep 0.5;
      br;
    else
      br 2;
      echo "No wireless adapter";
      br;
    fi
  }

  # this alias to set the network adapter to monitor mode
  # in another way
  alias rmon="rmon"

  # this function for rmn alias
  function rmon(){
    c && br 2 && sudo clear;
    sudo airmon-ng check wlan0;
    c;
    sleep 1;
    sudo airmon-ng check kill wlan0;
    c;
    sleep 1;
    sudo airmon-ng start wlan0;
    c;
    echo "M o n i t o r     M o d e" | figlet -t -c | lolcat;
    sleep 1;
    c && br;
    ntsh;
  }

  # this alias to switch to managed mode
  alias mngd="mngd"

  # this function for mngd alias
  function mngd(){
    c && br 2 && sudo clear;
    wtp wlan0 managed;
    br 2;
    echo "M a n a g e d     M o d e" | figlet -t -c | lolcat;
    tlk "managed mode";
    sleep 0.5;
    c && br;
    ntsh;
  }

  # this alias to restart the network manager after a hack
  alias rst="allow_sudo && rst"

  # this function for rst alias
  function rst(){
    c && br 2;
    sudo service NetworkManager restart;
    br 2;
    echo "N e t     R e s e t" | figlet -t -c;
    # tlk "network reset";
    sleep 1;
    sudo service NetworkManager restart;
    upnet eth0;
    #upnet eth1;
    if [ -d /sys/class/net/wlan0 ]; then
      upnet wlan0;
      wtp wlan0 managed;
      sleep 0.5;
    fi
    cv;
  }

  # this alias to run wifite
  alias whk="allow_sudo && whk"

  # this function for whk alias
  function whk(){
    function hack_wifi(){
      sudo wifite --kill;
      br;

      # this function will ask if the
      # hacking should restart or not
      function check_quit(){
        echo -ne " ${BOLD}${WHITE}[${GREEN}?${WHITE}]${WHITE} ${GREEN}Restart ${WHITE}the wifi hacking ? (y/n) ";
        read wifi
        if [ "$wifi" = "y" ]; then
          whk
        elif [[ "$wifi" = "n" ]]; then
          echo -ne " ${BOLD}${WHITE}[${GREEN}+${WHITE}]${WHITE} Switching to ${GREEN}Managed ${WHITE}Mode  ";
          downnet eth0 && upnet wlan0;
          wtp wlan0 managed;
          echo "${GREEN}  ${WHITE}"
          echo -ne " ${BOLD}${WHITE}[${GREEN}+${WHITE}]${WHITE} Restarting Network Manager "
          sudo service NetworkManager restart;
          echo "${GREEN}  ${WHITE}"
        else
          check_quit
        fi
      }
      allow_sudo && check_quit
    }

    if [ -d /sys/class/net/wlan0 ]; then
      c && br
      hack_wifi
    else
      br
      echo "  ${BOLD}${WHITE}[${RED}x${WHITE}]${WHITE} No ${RED}Wireless Card ${WHITE}Available"
      br
    fi
  }

  # this alias to create a Fake Access Point
  alias facp="allow_sudo && facp"

  # this function for facp alias
  function facp(){
    if [ -d /sys/class/net/wlan0 ]; then
      sudo systemctl stop NetworkManager
      sudo systemctl stop wpa_supplicant
      sudo ifconfig wlan0 down
      sudo ifconfig wlan0 up
      sudo airbase-ng --essid "$*" -c 11 wlan0
    else
      echo "No wireless adapter found"
    fi

    function check_quit(){
      echo -ne " ${BOLD}${WHITE}[${GREEN}?${WHITE}]${WHITE} ${GREEN}Restart ${WHITE}the Fake Acces Point ? (y/n) ";
      read wifi
      if [ "$wifi" = "y" ]; then
        whk
      elif [[ "$wifi" = "n" ]]; then
        echo -ne " ${BOLD}${WHITE}[${GREEN}+${WHITE}]${WHITE} Switching to ${GREEN}Managed ${WHITE}Mode  ";
        downnet eth0 && upnet wlan0;
        wtp wlan0 managed;
        echo "${GREEN}  ${WHITE}"
        echo -ne " ${BOLD}${WHITE}[${GREEN}+${WHITE}]${WHITE} Restarting Network Manager "
        sudo service NetworkManager restart;
        echo "${GREEN}  ${WHITE}"
      else
        check_quit
      fi
    }
    check_quit
  }

  # function facp(){
  #   if [ -d /sys/class/net/wlan0 ]; then
  #     sudo systemctl stop NetworkManager
  #     sudo systemctl stop wpa_supplicant
  #     sudo ifconfig wlan0 down
  #     sudo ifconfig wlan0 up
  #
  #     sudo airbase-ng --essid "$*" -c 11 wlan0 &
  #
  #     sleep 5  # Wait for airbase-ng to create the at0 interface
  #
  #     sudo ifconfig at0 up 10.0.0.1 netmask 255.255.255.0
  #     sudo dnsmasq -C /etc/dnsmasq.conf -d &
  #
  #     echo 1 | sudo tee /proc/sys/net/ipv4/ip_forward
  #     sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
  #     sudo iptables -A FORWARD -i eth0 -o at0 -m state --state RELATED,ESTABLISHED -j ACCEPT
  #     sudo iptables -A FORWARD -i at0 -o eth0 -j ACCEPT
  #   else
  #     echo "No wireless adapter found"
  #   fi
  # }

  # this alias to deauth wireless connection
  alias deauth="deauth"

  # this function for deatuh alias
  function deauth(){
    if [[ $# -ge 1 ]]; then
      if [ -d /sys/class/net/wlan0 ]; then
        c && br 2 && sudo clear;

        if [[ !$(pgrep NetworkManager) ]]; then
          sudo systemctl start NetworkManager;
          wtp wlan0 managed;
        fi

        kl wpa_supplicant;
        kl dhclient;

        echo "        D e A u t h" | figlet && br;
        echo " ==> Target Wi-Fi : '$*' " && br;
        ssid="$*"
        bssid=$(nmcli -f BSSID,SSID device wifi list | grep "$ssid" | awk '{print $1}')
        # bssid=$(sudo iw dev wlan0 scan | grep -B 8 "SSID: $ssid" | awk -F "(" '/^BSS/{print $1}' | tr '[:lower:]' '[:upper:]' | sed 's/BSS //');
        # here we use the iw dev wlan0 scan to show the wireless networks without using nmcli
        # the grep -B 8 means it will match the eight's line before the found on the pattern
        # use grep -A to match lines after the matched one
        # awk -F "" will set the delimiter between matches and then it will print the first side of the matching pattern 
        # tr will then convert all the letter to uppercase
        # the sed 's/BSS //' will replace BSS to nothing
        # what can I say, today 11/11/2023 I'm becoming more and more good at pattern matching
        if [ -n "$bssid" ]; then
          # if [[ -n $(sudo airmon-ng check wlan0) ]]; then
          #   sudo airmon-ng check kill wlan0;
          # fi
          sudo aireplay-ng -0 0 -a "$bssid" wlan0 --ignore-negative-one;
        else
          echo "SSID '$ssid' not found";
          br;
        fi
      else
        echo "No wireless adapter found";
        br;
      fi
    else
      echo "Please pass the Wi-Fi SSID as the argument";
    fi
  }

  # this alias to connect to a wifi via CLI
  alias wcnt="wcnt"

  # this function for wcnt alias
  function wcnt(){
    if [[ $# -eq 1 ]]; then
      if [ -d /sys/class/net/wlan0 ]; then
        nmcli device wifi connect "$1";
      else
        echo " No wireless adapter found";
        br;
      fi
    elif [[ $# -eq 2 ]]; then
      if [ -d /sys/class/net/wlan0 ]; then
        nmcli device wifi connect "$1" password "$2";
      else
        echo " No wireless adapter found";
        br;
      fi
    else
      echo "Please pass the Wi-Fi SSID as argument";
    fi
  }

  # this alias to list all the wifi nearby
  alias wls="allow_sudo && wls"

  # this function for wls alias
  function wls(){
    if [ -d /sys/class/net/wlan0 ]; then
      downnet eth0 && upnet wlan0;
      c && br 2;
      echo " Wi-Fi connections nearby : " && br;
      nmcli device wifi list
      # nmcli -f SSID,BSSID,SECURITY,CHAN,SIGNAL,BARS,RATE,MODE device wifi list
      # nmcli -f SSID,SECURITY,CHAN,SIGNAL,BARS,RATE,MODE device wifi list
      # wait;
      br;
    else
      c && br 2;
      echo "No wireless adapter";
      br;
    fi
  }

  # this function to check saved wifi network
  function wchk(){
    # Get the saved Wi-Fi connections
    nmcli connection show | grep -q "$1" && echo "$1 found" || echo "$1 not found"
    # We have a cool ternary expression here :D
  }

  # this alias to run airgeddon
  alias rhk="allow_sudo && rhk"

  # this function for rhk alias
  function rhk(){
    sudo airgeddon
  }

  # this alias to run the cupp command
  alias cupp="cupp"

  # this function for cupp alias
  function cupp(){
    c && br;
    if [[ $# -eq 0 ]]; then
      cupp.py -i;
    elif [[ $# -gt 0 ]]; then
      cupp.py $@;
    fi
  }

  # this alias to ping a network
  alias reach="allow_sudo && reach"

  #this function to check if pfsense is reachable
  # coded 01/29/2024
  function reach(){
    local target_IP="$1"
    local check_message="Checking $target_IP reachability..."
    local check_IP="sudo ping -c 1 -W 5 "
    local reachable="c && br && echo ' $check_message' && eval $check_IP $target_IP &> /dev/null;"
    # the -c 1 means we send one packet to test it
    # the -W 5 means if the ping have 5 seconds to check
    # as always we run it in background in order to
    # not see all the boring logs messages

    if eval $reachable ;then
      #if PfSense is reachable then
      #we execute the next command after
      #this function calling
      # eval "$@"
      echo " $target_IP is reachable"
    else;
      echo " $target_IP is not reachable"
    fi
  }

  #######################################################################
  ```
</details>

<details>
  <summary><strong> Linux Programs Aliases</strong></summary>

  ```sh
  ### Kali Linux Programs Aliases

  # this alias to run an executable file or a script
  alias rn="rn"

  # this function for rn alias
  function rn(){
    #this will look for the extension of the file
    case "${1##*.}" in
      class)
        java "$1";;
      py)
        if [[ $# -eq 1 ]]; then
          # all "$1";
          # c && br;
          python3 "$1";
          return 0;
          # br;
        elif [[ $# -gt 1 ]]; then
          all "$1";
          c && br;
          python3 "$1" "$@";
          return 0;
          br;
        fi
      ;;
      c || cpp) # update 07/28/2023
        file="$1";
        out="${file%.*}"

        # Condition 1: Check if the file extension is c
        extension='[[ "${file##*.}" == "c" ]]';

        # Condition 2: Check if the file contains math library
        math='grep -E "^#include <math.h>" "$file" >/dev/null';

        # Ternary expressions to determine compiler and flags
        compiler=$(eval "$extension" && echo "gcc" || echo "g++");
        flags=$(eval "$math" && echo "-lm" || echo "");

        # check if an old executable exists
        if [[ -f "$out" ]]; then
          dlf "$out";
        fi

        # Compile the C file
        "$compiler" "$file" -o "$out" $flags;

        # Execute the resulting executable
        all "$out";
        clear && br;
        ./"$out";
        br;;
      html)
        google-chrome "$1" && cv;;
      asm)
        nasm -felf64 "$1"
        ld ${1%.*}.o -o ${1%.*}
        ./${1%.*}
        ;;
      *)
        all "$1" && c && ./"$1";;
  esac
  }

  # this alias to run an executable file or a script
  alias rns="allow_sudo && rns"

  # this function for rn alias
  function rns(){
    #this will look for the extension of the file
    case "${1##*.}" in
      py)
        if [[ $# -eq 1 ]]; then
          # all "$1";
          # c && br;
          python3 "$1";
          return 0;
          # br;
        elif [[ $# -gt 1 ]]; then
          all "$1";
          c && br;
          python3 "$1" "$@";
          return 0;
          br;
        fi
      ;;
      c || cpp) # update 07/28/2023
        file="$1";
        out="${file%.*}"

        # Condition 1: Check if the file extension is c
        extension='[[ "${file##*.}" == "c" ]]';

        # Condition 2: Check if the file contains math library
        math='grep -E "^#include <math.h>" "$file" >/dev/null';

        # Ternary expressions to determine compiler and flags
        compiler=$(eval "$extension" && echo "gcc" || echo "g++");
        flags=$(eval "$math" && echo "-lm" || echo "");

        # check if an old executable exists
        if [[ -f "$out" ]]; then
          dlf "$out";
        fi

        # Compile the C file
        "$compiler" "$file" -o "$out" $flags;

        # Execute the resulting executable
        all "$out";
        clear && br;
        ./"$out";
        br;;
      html)
        google-chrome "$1" && cv;;
      asm)
        nasm -felf64 "$1"
        ld ${1%.*}.o -o ${1%.*}
        ./${1%.*}
        ;;
      *)
        all "$1" && c && sudo ./"$1";;
  esac
  }

  # this alias to make the pc talk
  alias tlk="espeak -v en+m3 -s 150" 
  # -v en+m3 -s 150" ==> those are optional

  # this function for tlk alias
  function tlk1(){
    espeak "$1" && cv;
  }

  # this alias to serve files via the Php server
  alias srv="srv"

  # this function for srv alia
  function srv(){
    php -S 127.0.0.1:50000;
    google-chrome 127.0.0.1:50000/"$1";
  }

  # alias to view inside a file
  alias vf="vf"

  # function for vf alias
  # update 09/14/2023
  function vf() {
    local file="$1"
    local extension="${file##*.}"

    case "$extension" in
      mcd)
        cmd="katyushamcd";;
      *)
        cmd="xdg-open";;
    esac

    "$cmd" "$file" && cv
  }

  # this alias to view binary file
  alias vfb="vfb"

  # this function for vfb alias
  function vfb(){
    od -t x1 -A n "$1";
  }

  # this alias to copy files
  alias cpf="cpf"

  # this function for cpf alias
  function cpf(){
    local copy_target=${2:-$dest}
    cp -r "$@" "$copy_target" && op "$copy_target";
  }

  function cpf2() {
    cp "${@:1:$#-1}" "${@:$#}";
  }

  # this alias to copy the content of a file
  alias cnf="cnf"

  # this function for cnf alias
  function cnf(){
    cat "$1" > "$2" && dlf "$1" && all "$2";
  }

  # this alias to locate packages
  alias lc="lc"

  # this function for lc alias
  function lc(){
    locate "$1" | less && cv;
  }

  # this alias for ngrok
  alias ngrok="ngrok"

  # this function for ngrok alias
  # IMPROVED: 05-30-2024 14:12
  function ngrok() {
    # get the ngrok arguments
    local ngrok_args="$@"

    # check for dashes then do not
    # redirect to another terminal
    for arg in "$@"; do
      if [[ "$arg" == *-* ]]; then
        command ngrok "$@"
        return
      fi
    done

    (setsid qterminal -e bash -c "ngrok $ngrok_args" >/dev/null 2>&1 &)
  }

  # this alias to view the irc sever status
  alias irth="irth"

  # this function for irth alias
  function irth(){
    c && br 2 && sudo clear;
    echo "    irc server status : ";
    br;
    sudo service inspircd status ;
    br;
  }

  # this alias to start the irc server
  alias ircon="ircon"

  # this function for ircon alias
  function ircon(){
    clear && br 2 && sudo clear;
    sudo service inspircd start;
    irth;
  }

  # this alias to restart the irc server
  alias ircrst="ircrst"

  # this function for ircrst alias
  function ircrst(){
    clear && br 2 && sudo clear;
    sudo service inspircd restart;
    irth;
  }

  # this alias to stop the irc server
  alias ircoff="ircoff"

  # this function for ircoff alias
  function ircoff(){
    clear && br 2 && sudo clear;
    sudo service inspircd stop;
    irth;
  }

  #######################################################################
  ```
</details>

<details>
  <summary><strong> WSL Terminal Aliases</strong></summary>

  ```sh
  ### WSL Terminal Aliases

  # this alias to switch to windows terminal
  alias wds="wds"

  # this function for wds alias
  function wds(){
    c && br 2;
    # Check the current directory
    # because cmd will work only
    # on windows'directory rather
    # than WSL's one so we move
    if [[ "$PWD" == "/mnt/"* ]]; then
      cmd.exe;
    else
      cd /mnt/c
      cmd.exe;
      cd - &>/dev/null
    fi
    cv;
  }

  # this alias to switch to powershell terminal
  alias pws="pws"

  # this function for pws alias
  function pws(){
    c && br 2;
    powershell.exe;
    cv;
  }

  # this alias to enter cmd as admin
  alias cmd="cmd"

  # this function for cmd alias
  function cmd(){
    powershell.exe -command "Start-Process cmd -Verb RunAs";
    x;
  }

  #######################################################################
  ```
</details>

<details>
  <summary><strong> WSL Network Aliases</strong></summary>

  ```sh
  ### WSL Network Aliases

  # this alias to show the network configuration
  alias ipsh="ipsh"

  # this function for ntsh alias
  function ipsh(){
    c && br;
    echo "  Available IP Adresses : ";
    br;
    local eth_ip=$(ip addr show eth0 | grep -oP 'inet \K[\d.]+');
    local wifi_ip=$(ip addr show wifi0 | grep -oP 'inet \K[\d.]+');
    echo " eth0  ==> $eth_ip" && br;
    echo " wifi0  ==> $wifi_ip" && br;
  }

  function clean_argument() {
    local arg="$1"
    # Replace spaces with backslashes
    local clean_arg="${arg// /\\}"

    # Replace special characters with escaped versions
    local special_chars='[][{}()*+?.\\^$|]'
    # Escape backslashes for sed
    local escaped_special_chars="$(echo "$special_chars" | sed 's/\\/\\\\/g')"
    local arg_pattern="s/[$escaped_special_chars]/\\\\&/g"

    clean_arg="$(echo "$clean_arg" | sed -E "$arg_pattern")"
    echo "$clean_arg"
  }

  # I don't know why but this alias
  # make the PC slow down
  # this alias to view saved wifi password
  # SOLVED: 05-11-2024 22:44
  # Just execute it inside the
  # hard drive of windows instead of WSL
  # directories, so just cd to whatever
  # hard drive of windows to make it run
  alias wpass="wpass"

  # this function for wpass alias
  function wpass(){
    cd /mnt/c
    if [[ $# -eq 0 ]]; then
      # consider all arguments as one string
      local wifi=$(
        cmd.exe /c netsh wlan show profiles |
          grep -i "All User Profile" |
          awk '{print $5}' | shuf -n 1
      )
      local password=$(
        cmd.exe /c netsh wlan show profiles "$wifi" key=clear |
          grep "Key Content" |
          awk '{print $4}'
      )
      echo "Wifi SSID : $wifi";
      echo "Password  : $password";
    else
      # consider all arguments as one string
      local wifi="$*"
      local password=$(
        cmd.exe /c netsh wlan show profiles "$wifi" key=clear |
          grep "Key Content" |
          awk '{print $4}'
      )
      echo "Wifi SSID : $wifi";
      echo "Password  : $password";
    fi
    cd - &>/dev/null;
  }

  # Completion function for wpass
  _wpass_completion() {
    cd /mnt/c
    local cur

    # Get the current word being completed
    cur="${COMP_WORDS[COMP_CWORD]}"

    # Fetch WiFi profiles
    local profiles=$(cmd.exe /c netsh wlan show profiles |
      grep -i "All User Profile" |
      awk '{$1=$2=$3=""; print substr($0, 6)}' |
      head -n 1000
    )

    # Generate completions
    COMPREPLY=($(compgen -W "${profiles}" -- "${cur}"))
    cd - &>/dev/null
  }

  # Register the completion function for wpass
  complete -F _wpass_completion wpass

  # this alias to "list known wifi"
  alias wls="wls"

  # this function for wls alias
  function wls(){
    cd /mnt/c

    function print_message(){
      wifi="$1"
      password="$2"
      # Print Wi-Fi SSID and password
      echo "Wifi SSID : $wifi"
      echo "Password  : $password"
      echo
    }

    function wifi_and_pass(){
      num_profiles="$1"
      grep_string="$2"
      # Loop through each Wi-Fi profile
      while IFS= read -r wifi; do
        # Retrieve password for the current Wi-Fi profile
        local password=$(
          cmd.exe /c netsh wlan show profiles "$wifi" key=clear |
            grep "Key Content" | awk '{print $4}'
        )
        print_message $wifi $password
      done < <(
        cmd.exe /c netsh wlan show profiles |
          grep -i "$grep_string" |
          grep 'All User Profile' |
          awk '{$1=$2=$3=""; print substr($0, 6)}' |
          head -n "$num_profiles"
      )
    }

    function wifi_name(){
      wifi_count=0
      # Loop through each Wi-Fi profile
      while IFS= read -r wifi; do
        echo "- $wifi"
        ((wifi_count++))
      done < <(
        cmd.exe /c netsh wlan show profiles |
          grep 'All User Profile' |
          awk '{$1=$2=$3=""; print substr($0, 6)}'
      )
    }

    if [[ $# -eq 0 ]]; then
      num_profiles=1
      grep_string=$(
        cmd.exe /c netsh wlan show profiles |
          grep -i "All User Profile" |
          awk '{print $5}' | shuf -n 1
      )
      wifi_and_pass $num_profiles $grep_string
    elif [[ $# -eq 1 ]]; then
      if [[ "$1" =~ ^[0-9]+$ ]]; then
        num_profiles=$1
        grep_string=""
        wifi_and_pass $num_profiles $grep_string
      elif [[ "$1" != "-a" ]]; then
        num_profiles=99999999
        grep_string="$1"
        wifi_and_pass $num_profiles $grep_string
      elif [[ "$1" -eq "-a" ]]; then
        wifi_name
        echo
        echo "Known Wi-Fi Connections ($wifi_count) "
      fi
    fi

    cd - &>/dev/null;
  }

  # this alias to reach a network
  alias reach="allow_sudo && reach";

  # this function to check if pfsense is reachable
  # coded 01/29/2024
  function reach(){
    c && br;

    local target_IP="$1"
    local check_message="Checking $target_IP reachability..."
    local check_IP="sudo ping -c 1 -W 5 "
    local reachable="br && echo ' $check_message' && eval $check_IP $target_IP &> /dev/null;"
    # the -c 1 means we send one packet to test it
    # the -W 5 means if the ping have 5 seconds to check
    # as always we run it in background in order to
    # not see all the boring logs messages

    if eval $reachable ;then
      #if PfSense is reachable then
      #we execute the next command after
      #this function calling
      # eval "$@"
      echo " $target_IP is reachable"
    else;
      echo " $target_IP is not reachable"
    fi
  }

  #######################################################################
  ```
</details>

<details>
  <summary><strong> WSL Browser</strong></summary>

  ```sh
  ### WSL Browser

  # SOLVED :
  # this to make Github CLI know which default browser it would use
  # this WSL issue was solved in gh GitHub Repo Pull Request
  export BROWSER="chrome.exe"

  # this alias to open file with browser
  alias bwsop="bwsop"

  # SOLVED : no need for this annoying code
  # since we only use Windows Explorer to
  # open files according to their default apps
  # and there is no lag like we did here
  # IMPROVED : 06-18-2024 21:44
  # Handled the shell access after launch
  #
  # this function bwsop alias
  function bwsop(){
    local file_name="$1"
    local file_extension="${file_name##*.}"
    local current_directory="$PWD"

    # Replace all Spaces and Back-slashes with %20
    local formatted_path=$(wslpath -m . | sed -e 's/ /%20/g' -e 's/\\//g')
    local formatted_file=$(echo "$file_name" | sed -e 's/ /%20/g' -e 's/\\//g')

    # Check if it a Pdf file
    local isPdf="[[ "$file_extension" == "pdf" ]]"

    # Open Pdf file with edge and the other files with chrome
    local browser=$( eval $isPdf && echo msedge.exe || echo chrome.exe)

    # if the current directory is a WSL
    # directory then switch to windows
    # directory before executing the script
    if [[ "$current_directory" != "/mnt/"* ]]; then
      cd /mnt/c
    fi

    # Open the file with the browser
    cmd.exe /c start $browser file:///$formatted_path/$formatted_file

    # if we changed directory then get back
    if [[ "$PWD" != "$current_directory" ]]; then
      cd - &>/dev/null
    fi

    return 0
  }

  #######################################################################
  ```
</details>

<details>
  <summary><strong> WSL PWA Alias</strong></summary>

  ```sh
  ### WSL PWA Alias

  # HTX:
  # this alias to open web app
  alias open_web_app="allow_sudo && open_web_app";

  # CREATED :  02-11-2024 20:13
  # this function to open chrome based app
  # it uses the Id of the App we created within
  # the Chrome browser, it will take 3 arguments :
  # first the domain of the App
  # then the chrome App Id
  # finally the name of the App (optional)
  # NOTE : 08-26-2024 11:28
  # This is just PWA that can
  # be installed in whatever browser
  # IMPROVED : 05-30-2024 18:36
  # Shell access after execution
  function open_web_app(){
    local browser="chrome.exe"
    local app_domain="$1"
    local app_id="$2"
    local app_name="${3:-$(convert_url $app_domain)}"
    local current_directory="$PWD"
    local check="sudo ping -c 1 -W 5 "
    local check_message="Checking $app_name ..."
    local reachable="c && br && echo ' $check_message' && eval $check $app_domain &> /dev/null;"

    # if the current directory is a WSL
    # directory then switch to windows
    # directory before executing the script
    if [[ "$current_directory" != "/mnt/"* ]]; then
      cd /mnt/c
    fi

    # if there is an app ID open
    # that windowed chrome app
    # otherwise launch chrome with
    # with the domain passed as argument
    if [ -n "$app_id" ]; then
      open_app='cmd.exe /c start $browser --profile-directory=Default --app-id=$app_id;'
    else
      open_app='cmd.exe /c start $browser $app_domain'
    fi

    # this function to display the web app status
    function web_app_stat(){
      c && br
      echo " WebApp  : $app_name"
      echo " Link    : $app_domain"
      echo " Browser : $browser"
      echo " Status  : $1"
    }

    # check the stat
    if eval $reachable; then
      web_app_stat "Connected"
    else
      web_app_stat "Not Connected"
    fi

    # here to call the open_app function
    eval $open_app

    # if we changed directory then get back
    if [[ "$PWD" != "$current_directory" ]]; then
      cd - &>/dev/null
    fi

    return 0
  }

#######################################################################
  ```
</details>

<details>
  <summary><strong> WSL PWAs</strong></summary>

  ```sh
  ### PWAs Aliases

  # this function to convert url to name
  function convert_url(){
    url="$1"
    domain="${url%.*}"

    # Capitalize the first letter of the domain
    capitalized_domain="$(tr '[:lower:]' '[:upper:]' <<< ${domain:0:1})${domain:1}"
    echo "$capitalized_domain"
  }

  # this alias to open the GitHub app
  alias gthb="gthb"

  # this function for gthb alias
  function gthb(){
    local is_a_git_repo=$(git rev-parse --is-inside-work-tree 2>/dev/null)

    local github_id="mjoklplbddabcmpepnokjaffbmgbkkgg"
    local github_link="github.com"
    local github_name="GitHub"

    if [[ "$is_a_git_repo" == "true" ]]; then
      local has_remote=$(git remote -v)
      if [ "$has_remote" ]; then
        local repo_url=$(git config --get remote.origin.url)
        local repo_owner=$(echo "$repo_url" | awk -F '[/:]' '{print $(NF-1)}')
        local repo_name="$(echo "$repo_url" | awk -F '/' '{print $NF}' | sed 's/.git$//')"
      else
        local repo_owner=$(git config user.username)
        local repo_name=$(basename "$(git rev-parse --show-toplevel)")
      fi

      local current_branch=$(git branch | awk '/\*/ {print $2}');

      function check_view(){
        echo -ne "${BOLD}${GREEN}Open ${WHITE}the repo ${LIGHT_BLUE}$repo_name ${WHITE}on GitHub ? (y/n) ";
        read check_view
        echo ${RESET}

        if [ "$check_view" = "y" ]; then
          cd /mnt/c

          cmd.exe /c start chrome.exe \
            --profile-directory=Default --app-id=$github_id \
            --app=https://github.com/$repo_owner/$repo_name/tree/$current_branch \

          cd - &>/dev/null
          # gh repo view $repo_owner/$repo_name \
          #   --web --branch $current_branch \
          #   &>/dev/null
        elif [ "$check_view" = "n" ];then
          open_web_app $github_link $github_id $github_name
        else
          check_view
        fi
      }

      # check if the repo has a remote
      # on github otherwise open the pwa
      if [ "$has_remote" ]; then
        local is_remote_branch=$(git branch -r | grep "origin/$current_branch")

        # check if the current branch has remote
        if [ -n "$is_remote_branch" ]; then
          check_view
        else
          echo "${BOLD} ■■▶ The remote repo ${LIGHT_BLUE}$repo_name ${WHITE}has no branch named ${GREEN}$current_branch ${WHITE}!" && br;
        fi
      else
        open_web_app $github_link $github_id $github_name
      fi
    else
      if [[ $# -eq 0 ]]; then
        open_web_app $github_link $github_id $github_name
      fi
    fi
  }

  # this alias to open chatGpt app
  alias gpt="gpt"

  # this function for gpt alias
  function gpt(){
    local gpt_id="febkkahnhhdppidjakkemnckfhnkidba"
    local gpt_link="chatgpt.com"
    local gpt_name="ChatGpt"
    open_web_app $gpt_link $gpt_id $gpt_name
  }

  # this alias to open Google Gemini app
  alias gmn="gmn"

  # this function for gmn alias
  function gmn(){
    local gmn_id="acehpdabncjaanhpihehcmhidhmbdcoo"
    local gmn_link="gemini.google.com"
    local gmn_name="Gemini"
    open_web_app $gmn_link $gmn_id $gmn_name
  }

  # this alias to open ClaudeAI app
  alias cld="cld"

  # this function for cld alias
  fuction cld(){
    local claude_id="fmpnliohjhemenmnlpbfagaolkdacoja"
    local claude_link="claude.ai"
    local claude_name="ClaudeAI"
    open_web_app  $claude_link $claude_id $claude_name
  }

  # this alias to open reddit forum
  alias rdt="rdt"

  # this function for rdt alias
  function rdt(){
    local reddit_id="lgnggepjiihbfdbedefdhcffnmhcahbm"
    local reddit_link="reddit.com"
    open_web_app $reddit_link $reddit_id
  }

  # this alias to open Digital Clock Web App
  alias clock="allow_sudo && clock"

  # this function for clock alias
  function clock(){
    local clock_id="pgoffdmnhcendlolaaobdojhhdnkfdlj"
    local clock_link="localhost"
    local clock_name="Digital Clock"

    # start apache server if not running
    if ! pgrep apache2 > /dev/null; then
      sudo service apache2 start &>/dev/null;
    fi

    # open clock PWA or Progressive Web App
    open_web_app $clock_link $clock_id $clock_name;

    # stop apache server
    sudo service apache2 stop &>/dev/null;
  }

  # this alias to open the GitLab app
  alias gtlb="gtlb"

  # this function for gthb alias
  function gtlb(){
    local gitlab_id="jndlecohfigjmhidboiabnpjfmjgmacp"
    local gitlab_link="gitlab.com"
    local gitlab_name="GitLab"
    open_web_app $gitlab_link $gitlab_id $gitlab_name
  }

  # this alias to open pypi
  alias pypi="pypi"

  # this function for pypi alias
  function pypi(){
    local pypi_id="dhfmdekmhnminddhppcomhncjifnohcg"
    local pypi_link="pypi.org"
    local pypi_name="PyPi"
    open_web_app $pypi_link $pypi_id $pypi_name
  }

  # this alias to open testpypi
  alias testpypi="testpypi"

  # this function for pypi alias
  function testpypi(){
    local test_pypi_id="opibpddgphoocjppppodcfdfdccdeoif"
    local test_pypi_link="test.pypi.org"
    local test_pypi_name="Test PyPi"
    open_web_app $test_pypi_link $test_pypi_id $test_pypi_name
  }
  # this alias to open crates Web App
  # crates.io is the official rust package repo
  alias crates="crates"

  # this function for crates alias
  function crates(){
    local crates_id="jeibpciabahgpgbljbmbkjgkkmjcfhdp"
    local crates_link="crates.io"
    local crates_name="Crates"
    open_web_app $crates_link $crates_id $crates_name
  }

  # this alias to open cloud convert
  alias conv="conv"

  # this function for img alias
  function conv(){
    local cloud_convert_id="hdmdoclnahphbppladolaimacehflnnb"
    local cloud_convert_link="cloudconvert.com"
    local cloud_convert_name="Cloud Convert"
    open_web_app $cloud_convert_link $cloud_convert_id $cloud_convert_name
  }

  # this alias to open mastodon.social
  alias mstdn="mstdn"

  # this function for mstdn alias
  function mstdn(){
    local mastodon_id="ikigfogfljecogfmdkeiipdcamdbibjl"
    local mastodon_link="mastodon.social"
    open_web_app $mastodon_link $mastodon_id
  }

  # this alias to open Facebook app
  alias fb="fb"

  # this function for fb alias
  function fb(){
    local fb_id="gelmehpcmiomoockkmdlfadoankpigol"
    local fb_link="facebook.com"
    open_web_app $fb_link $fb_id
  }

  # this alias to open Instagram app
  alias itg="itg"

  # this function for fb alias
  function itg(){
    local insta_id="akpamiohjfcnimfljfndmaldlcfphjmp"
    local insta_link="instagram.com"
    open_web_app $insta_link $insta_id
  }

  # this alias to open the discord app
  alias dsc="dsc"

  # this function for dsc alias
  function dsc(){
    local discord_id="magkoliahgffibhgfkmoealggombgknl"
    local discord_link="discord.com"
    open_web_app $discord_link $discord_id
  }

  # this alias to open Twitter X Web App
  alias twx="twx"

  # this function for twx alias
  function twx(){
    local twitter_id="lodlkdfmihgonocnmddehnfgiljnadcf"
    local twitter_link="x.com"
    local twitter_name="TwitterX"
    open_web_app $twitter_link $twitter_id $twitter_name
  }

  # this alias to open YouTube Web App
  alias ytb="ytb"

  # this function for ytb alias
  function ytb(){
    local youtube_id="agimnkijcaahngcdmfeangaknmldooml"
    local youtube_link="youtube.com"
    local youtube_name="YouTube"
    open_web_app $youtube_link $youtube_id $youtube_name
  }

  # this alias to open hackerank
  alias hcrk="hcrk"

  # this function for hcrk alias
  function hcrk(){
    local hackerrank_id="jlokchaaimeiedjgobonphmigfpingaj"
    local hackerrank_link="hackerrank.com"
    local hackerrank_name="HackerRank"
    open_web_app $hackerrank_link $hackerrank_id $hackerrank_name
  }

  # this alias to open LinkedIn WebApp
  alias lnk="lnk"

  # this function for lnk alias
  function lnk(){
    local linkedin_id="ohghonlafcimfigiajnmhdklcbjlbfda"
    local linkedin_link="linkedin.com"
    local linkedin_name="LinkedIn"
    open_web_app $linkedin_link $linkedin_id $linkedin_name
  }

  # this alias to open netlify web app
  alias ntlf="ntlf"

  # this function for ntlf alias
  function ntlf(){
    local netlify_id="dlbhokdiippnblopfealccihgfhaofkb"
    local netlify_link="netlify.com"
    local netlify_name="NetLify"
    open_web_app $netlify_link $netlify_id $netlify_name
  }

  # this alias to open dev.to web app
  alias devto="devto"

  # this function for devto alias
  function devto(){
    local devto_id="ecapchmcnohmakooheeinoaidebbiacm"
    local devto_link="dev.to"
    local devto_name="DevTo"
    open_web_app $devto_link $devto_id $devto_name
  }

  # this alias to open Compiler Explorer Web App
  alias cmplr="cmplr"

  # this function for cmplr alias
  function cmplr(){
    local cmplr_id="chjjlngghpbmipjipdfdjhcndbiklfje"
    local cmplr_link="godbolt.org"
    local cmplr_name="Compiler Explorer"
    open_web_app $cmplr_link $cmplr_id $cmplr_name
  }

  # this alias to open daedalOS Web App
  alias daeos="daeos"

  # this function for daeos alias
  function daeos(){
    local daeos_id="ojamcdcpaheomdkldanjflobhhpeoegg"
    local daeos_link="dustinbrett.com"
    local daeos_name="daedalOS"
    open_web_app $daeos_link $daeos_id $daeos_name
  }

  # this alias to open MacOs BigSur Web App
  alias bigsur="bigsur"

  # this function for bigsur alias
  function bigsur(){
    local bigsur_id="hejggljhmjcedakiebjfafljllofblid"
    local bigsur_link="macos-big-sur-clone.vercel.app"
    local bigsur_name="MacOs BigSur"
    open_web_app $bigsur_link $bigsur_id $bigsur_name
  }

  # this alias to open Windows 11 Web App
  alias win="win"

  # this function for win alias
  function win(){
    local win_id="kmdomeghommpdkfhamainmeepipgbgpi"
    local win_link="win11.blueedge.me"
    local win_name="Windows 11"
    open_web_app $win_link $win_id $win_name
  }

  # this alias to open Google Hacking Database Web App
  alias exdb="exdb"

  # this function for exdb alias
  function exdb(){
    local exdb_id="oibdijhbidmbckpcenopepmcaafbiiih"
    local exdb_link="www.exploit-db.com"
    local exdb_name="Google Hacking Database"
    open_web_app $exdb_link $exdb_id $exdb_name
  }

  # this alias to open Kaggle Web App
  alias kgl="kgl"

  # this function for kgl alias
  function kgl(){
    local kgl_id="ajdemkepbiggbelkgicfebbjokenncei"
    local kgl_link="kaggle.com"
    local kgl_name="Kaggle"
    open_web_app $kgl_link $kgl_id $kgl_name
  }

  # this alias to open Ip Info Web App
  alias ipinfo="ipinfo"

  # this function for ipinfo alias
  function ipinfo(){
    local ipinfo_id="adopfgmhmfaggadmlkiklebhncpjnnac"
    local ipinfo_link="ipinfo.io"
    local ipinfo_name="IpInfo"
    open_web_app $ipinfo_link $ipinfo_id $ipinfo_name
  }

  # this alias to open Course Careers Web App
  alias crs="crs"

  # this function for crs alias
  function crs(){
    local crs_id="ndljfckhgknkknnkmemfkalcibbpfhla"
    local crs_link="coursecareers.com"
    local crs_name="Course Careers"
    open_web_app $crs_link $crs_id $crs_name
  }

  # this alias to open Stackoverflow Web App
  alias stck="stck"

  # this function for stck alias
  function stck(){
    local stck_id="gafidhmaaknkinigcnolmldilpdlfdpa"
    local stck_link="stackoveerflow.com"
    local stck_name="Stack Over Flow"
    open_web_app $stck_link $stck_id $stck_name
  }

  # this alias to open Canva App
  alias canva="canva"

  # this function for canva alias
  function canva(){
    cd /mnt/c/Users/lab_l/AppData/Local/Programs/Canva
    cmd.exe /c start Canva.exe
    cd - &>/dev/null
  }

  # this alias to open MuseScore Web App
  alias mscr="mscr"

  # this function for mscr alias
  function mscr(){
    local mscr_id="ocbioacpdhnddoolpphbcnbndighhfkn"
    local mscr_link="musescore.com"
    local mscr_name="MuseScore"
    open_web_app $mscr_link $mscr_id $mscr_name
  }

  # this alias to open Docker Hub Web App
  alias dckhb="dckhb"

  # this function for dckhb alias
  function dckhb(){
    local dckhb_id="mclclddaglkchjeeijdmnlfcfedonbll"
    local dckhb_link="hub.docker.com"
    local dckhb_name="Docker Hub"
    open_web_app $dckhb_link $dckhb_id $dckhb_name
  }

  # this alias to open Nano Midi Web App
  alias midi="midi"

  # this function for midi alias
  function midi(){
    local midi_id="cajodfhkmmnbofphdiodilpglpkjaepb"
    local midi_link="nanomidi.net"
    local midi_name="Nano Midi"
    open_web_app $midi_link $midi_id $midi_name
  }

  # this alias to open Google Chat Web App
  alias chat="chat"

  # this function for chat alias
  function chat(){
    local chat_id="mdpkiolbdkhdjpekfbkbmhigcaggjagi"
    local chat_link="mail.google.com"
    local chat_name="Google Chat"
    open_web_app $chat_link $chat_id $chat_name
  }

  # this alias to open Virus Total Web App
  alias virustotal="virustotal"

  # this function for virustotal alias
  function virustotal(){
    local virustotal_id="dnopbpmlkabcondfpckfnhgabfcncjmg"
    local virustotal_link="virustotal.com"
    local virustotal_name="Virus Total"
    open_web_app $virustotal_link $virustotal_id $virustotal_name
  }

  # this alias to open CodinGame Web App
  alias codingame="codingame"

  # this function for codingame alias
  function codingame(){
    local codingame_id="mdmdhiclipbbmgikhgefloaghajjcheg"
    local codingame_link="codingame.com"
    local codingame_name="CodinGame"
    open_web_app $codingame_link $codingame_id $codingame_name
  }

  # this alias to open Cisco Skills For All Web App
  alias cisco="cisco"

  # this function for cisco alias
  function cisco(){
    local cisco_id="imjciepmglgacccklncenjgecohaihcj"
    local cisco_link="skillsforall.com"
    local cisco_name="Cisco Skills For All"
    open_web_app $cisco_link $cisco_id $cisco_name
  }

  # this alias to open Hack Tricks Web App
  alias tricks="tricks"

  # this function for tricks alias
  function tricks(){
    local tricks_id="mggngfogmkhbpicjamlefjpciidpodmm"
    local tricks_link="book.hacktricks.xyz"
    local tricks_name="Hack Tricks"
    open_web_app $tricks_link $tricks_id $tricks_name
  }

  # this alias to open Try Hack Me Web App
  alias hackme="hackme"

  # this function for hackme alias
  function hackme(){
    local hackme_id="daeaiadaklimdlhhcpgbdkgdkmghbkmf"
    local hackme_link="tryhackme.com"
    local hackme_name="Try Hack Me"
    open_web_app $hackme_link $hackme_id $hackme_name
  }

  # this alias to open google translate Web App
  alias translate="translate"

  # this function for translate alias
  function translate(){
    local translate_id="edanbjnaiofggfmimiidpfmhggkbokck"
    local translate_link="translate.google.com"
    local translate_name="Google Translate"
    open_web_app $translate_link $translate_id $translate_name
  }


  # this alias to open Marvell Web App
  alias marvell="marvell"

  # this function for marvell alias
  function marvell(){
    local marvell_id="fdleagllbcbhmlabenhdmdddefhohnbb"
    local marvell_link="marvell.com"
    local marvell_name="Marvell"
    open_web_app $marvell_link $marvell_id $marvell_name
  }

  # this alias to open DhIWise Web App
  # N.B. this is an app that have templates
  # for web and mobile app ready for production
  # 08-16-2024 19:11
  alias dhiwise="dhiwise"

  # this function for dhiwise alias
  function dhiwise(){
    local dhiwise_id="dcinmcknnkhikonobhpniddjnehmnkac"
    local dhiwise_link="app.dhiwise.com"
    local dhiwise_name="DhiWise"
    open_web_app $dhiwise_link $dhiwise_id $dhiwise_name
  }

  # this alias to open Quora Forum Web App
  alias quora="quora"

  # this function for quora alias
  function quora(){
    local quora_id="cechoboadpfjgoaooidphlandgelehhi"
    local quora_link="quora.com"
    local quora_name="Quora"
    open_web_app $quora_link $quora_id $quora_name
  }

  # this alias to open npmjs Web App
  alias npmjs="npmjs"

  # this function for npmjs alias
  function npmjs(){
    local npmjs_id="foijodnoknckfliaajfnihbonnniljbe"
    local npmjs_link="npmjs.com"
    local npmjs_name="Npm JS"
    open_web_app $npmjs_link $npmjs_id $npmjs_name
  }

  # this alias to open LolBas Web App
  alias lolbas="lolbas"

  # this function for lolbas alias
  function lolbas(){
    local lolbas_id="jlhledfapfgaeockhmjniedihamlliga"
    local lolbas_link="lolbas-project.github.io"
    local lolbas_name="LolBas"
    open_web_app $lolbas_link $lolbas_id $lolbas_name
  }

  # this alias to open Loud Me Web App
  alias loudme="loudme"

  # this function for loudme alias
  function loudme(){
    local loudme_id="iancljhjkfkhobcfkijolghiieciilka"
    local loudme_link="loudme.ai"
    local loudme_name="LoudMe"
    open_web_app $loudme_link $loudme_id $loudme_name
  }

  # this alias to open Snap Save
  # Facebook Video Downloader Web App
  alias snap="snap"

  # this function for snap alias
  function snap(){
    local snap_id="caepnkackbfnijpgljjkjfjhoiodmdek"
    local snap_link="snapsave.app"
    local snap_name="Snap Save"
    open_web_app $snap_link $snap_id $snap_name
  }

  # this alias to open Suno Web App
  alias suno="suno"

  # this function for suno alias
  function suno(){
    local suno_id="poemkolicenobkfdpoibhjjbgmjnlnpj"
    local suno_link="suno.com"
    local suno_name="Suno"
    open_web_app $suno_link $suno_id $suno_name
  }

  # this alias to open itch games Web App
  alias itch="itch"

  # this function for itch alias
  function itch(){
    local itch_id="bhgdfnaojobmidmdmdipcadlijbopndi"
    local itch_link="itch.io"
    local itch_name="Itch Games"
    open_web_app $itch_link $itch_id $itch_name
  }

  # this alias to open BitLy Web App
  alias bitly="bitly"

  # this function for bitly alias
  function bitly(){
    local bitly_id="iojpgkodflboefdoklfpbegdhbhmcjhe"
    local bitly_link="app.bitly.com"
    local bitly_name="BitLy"
    open_web_app $bitly_link $bitly_id $bitly_name
  }

  # this alias to open Binance Web App
  # NOTE : Binance is used for
  # Cryptocurrency Exchange for Bitcoin,
  # Ethereum & Altcoins
  alias binance="binance"

  # this function for binance alias
  function binance(){
    local binance_id="cnncjkiomekpjaednmgfcfiommnjogjo"
    local binance_link="binance.com"
    local binance_name="Binance"
    open_web_app $binance_link $binance_id $binance_name
  }

  # this alias to open Wikipedia Web App
  alias wiki="wiki"

  # this function for wiki alias
  function wiki(){
    local wiki_id="mabbogacohpoeacebobbecclmpanobce"
    local wiki_link="wikipedia.org"
    local wiki_name="Wikipedia"
    open_web_app $wiki_link $wiki_id $wiki_name
  }

  # this alias to open Flux AI Web App
  alias fluxai="fluxai"

  # this function for fluxai alias
  function fluxai(){
    local fluxai_id="mlmnaccmlmoihcobbmciddblmpjjaacp"
    local fluxai_link="www.fluxpro.ai"
    local fluxai_name="Flux AI"
    open_web_app $fluxai_link $fluxai_id $fluxai_name
  }

  # this alias to open W3SCHOOLS Offline Web App
  alias wscl="allow_sudo && wscl"

  # this function for wscl alias
  function wscl(){
    local wscl_id="lcmlmpinhhipbaifakfjccanpehnglei"
    local wscl_link="localhost"
    local wscl_name="W3Schools"

    if [[ ! $(pgrep apache2) ]]; then
      echo -ne "${BOLD}[${GREEN}+${WHITE}]${WHITE} Starting Apache Server ...";
      sudo service apache2 start &>/dev/null;
    fi

    open_web_app $wscl_link $wscl_id $wscl_name
  }

  # this alias to open Cyber Chef Web App
  alias cbr="allow_sudo && cbr"

  # this function for cbr alias
  function cbr(){
    local github_reachable="sudo ping -c 1 -W 5 github.com"
    if eval $github_reachable; then
      local cbr_id="laoalcpgflnjimblmgmjfhdfheldnmeo"
      local cbr_link="gchq.github.io"
      local cbr_name="Cyber Chef"
      open_web_app $cbr_link $cbr_id $cbr_name
    else
      cd /mnt/d/NTSOA/dev/github_repo/forks/cyber_chef
      bwsop CyberChef_v10.18.8.html
      cd -&>/dev/null
    fi
  }

  # this alias to open fast.com
  alias fast="open_web_app fast.com"

  # this alias to recharge the router
  alias rtr="rtr"

  # this function for rtr alias
  function rtr(){
    local airtel_id="phkfjlcmjmnindcbhfmnmlikainlhodg"
    local airtel_link="www.airtel.mg"
    local airtel_name="Airtel Router"
    open_web_app $airtel_link $airtel_id $airtel_name
  }

  # this alias to view the HTX_AP dashboard
  alias htx="htx"

  # this function for htx alias
  function htx(){
    local router_id="mgnpfopekbaehajaakfppclfjmcpceke"
    local router_IP="192.168.8.1"
    local router_name="h471x Router"

    # start apache server if not running
    if ! pgrep apache2 > /dev/null; then
      sudo service apache2 start &>/dev/null;
    fi

    # open clock PWA or Progressive Web App
    open_web_app $router_IP $router_id $router_name;

    # stop apache server
    sudo service apache2 stop &>/dev/null;
  }

  #######################################################################
  ```
</details>

<details>
  <summary><strong> WSL Programs Aliases</strong></summary>

  ```sh
  ### WSL Programs Aliases

  # this alias to run an executable file or a script
  alias rn="rn"

  # this function for rn alias
  function rn(){
    # this will look the extension of the file
    # use of ${1%.*} to retrieve the file name
    # explanation :
    # ${file%pattern} ==> this will remove the matched
    # pattern from the file from the end of the file
    #
    # use of ${1##*.} to retrieve extension
    # explanation :
    # ${file##*.} ==> this will remove the longest
    # matched string from the beginning of the file
    # 2024-02-12 00:27
    case "${1##*.}" in
      py)
        # all "$1" && c && echo -e && py "$1" && echo -e;;
        python "$@" && return 0;;
      c || cpp) # update 07/28/2023
        file="$1";
        out="${file%.*}"

        # Condition 1: Check if the file extension is c
        extension='[[ "${file##*.}" == "c" ]]';

        # Condition 2: Check if the file contains math library
        math='grep -E "^#include <math.h>" "$file" >/dev/null';

        # Ternary expressions to determine compiler and flags
        compiler=$(eval "$extension" && echo "gcc" || echo "g++");
        flags=$(eval "$math" && echo "-lm" || echo "");

        # check if an old executable exists
        if [[ -f "$out" ]]; then
          dlf "$out";
        fi

        # Compile the C file
        "$compiler" "$file" -o "$out" $flags;

        # Execute the resulting executable
        all "$out";
        clear && br;
        ./"$out";
        br;;
      js)
        c && br 2 && node "$1" && br
        ;;
      com)
        open_web_app "$1";
        ;;
      bat)
        cmd.exe /c "$1";
        ;;
      html || pdf)
        bwsop "$1"
        ;;
      *)
        all "$1" && c && ./"$1";;
  esac
  }

  # this alias to view inside a file
  alias vf="vf"

  # this function for vf alias
  function vf() {
    if [[ -f "$1" ]]; then
      case "${1##*.}" in
        db|sqlite*|xlsx|docx|pptx|ppt|wmv|pcapng|pdf|jpg|png|JPG|PNG|lnk|docx|xslsx|pptx|mp*|zip|rar|gns3) 
          explorer.exe "$1"
          ;;
        # open all files that have default app with windows explorer
        html)
          if [[ "$PWD" == "/mnt/"* ]]; then
            explorer.exe "$1"
          else
            bwsop "$1"
          fi
          ;;
        fxml)
          cmd.exe /c start SceneBuilder.exe "$@"
          ;;
        *) nvim "$1" ;;
      esac
      return 0
    elif [[ -d "$1" ]]; then
      op "$1"
    fi
  }

  # this alias to call the sqlite3.Exe file
  alias sqlite="sqlite"

  # this function for ssqlite alias
  function sqlite(){
    if [[ $# -eq 0 ]]; then
      echo "■■▶ Please specify a file.db  ";
    else
      if [[ $# -eq 1 && "${1##*.}" -eq "db" ]]; then
        c && br;
        sqlite3.exe $@;
        cv;
      else
        sqlite3.exe $@;
      fi
    fi
  }

  # this alias to call the windows nodeJS Program
  alias node="node"

  # this function for node alias
  function node(){
    node.exe $@;
  }

  # this alias to launch eclipse IDE
  alias eclipse="eclipse"

  # this function for eclipse alias
  function eclipse(){
    if [[ "$PWD" == "/mnt/"* ]]; then
      cmd.exe /c start eclipse.exe ${@:-.}
    else
      cd /mnt/c
      cmd.exe /c start eclipse.exe ${@:-.}
      cd - &>/dev/null
    fi
  }

  # this alias to launch Apache NetBeans IDE
  alias beans="beans"

  # this function for beans alias
  function beans(){
    if [[ "$PWD" == "/mnt/"* ]]; then
      cmd.exe /c start netbeans64.exe ${@:-.}
    else
      cd /mnt/c
      cmd.exe /c start netbeans64.exe ${@:-.}
      cd - &>/dev/null
    fi
  }

  # this alias to launch intelijieda
  alias idea="idea"

  # this function for idea alias
  function idea(){
    if [[ "$PWD" == "/mnt/"* ]]; then
      cmd.exe /c start idea64.exe ${@:-.}
    else
      cd /mnt/c
      cmd.exe /c start idea64.exe ${@:-.}
      cd - &>/dev/null
    fi
  }

  # this alias to open PyCharm
  alias charm="charm"

  # this function for charm alias
  function charm(){
    if [[ "$PWD" == "/mnt/"* ]]; then
      cmd.exe /c start pycharm64.exe ${@:-.}
    else
      cd /mnt/c
      cmd.exe /c start pycharm64.exe ${@:-.}
      cd - &>/dev/null
    fi
  }

  # this alias to launch ppsspp
  alias psp="psp"

  # this function for psp alias
  function psp(){
    if [[ "$PWD" == "/mnt/"* ]]; then
      cmd.exe /c start PPSSPPWindows.exe $@
    else
      cd /mnt/c
      cmd.exe /c start PPSSPPWindows.exe $@
      cd - &>/dev/null
    fi
  }

  # this alias to open tor browser
  alias tor="tor"

  # this function for tor alias
  function tor(){
    if [[ "$PWD" == "/mnt/"* ]]; then
      cmd.exe /c start tor.exe $@
    else
      cd /mnt/c
      cmd.exe /c start tor.exe $@
      cd - &>/dev/null
    fi
  }

  # this alias for windows ngrok
  alias ngrok="ngrok"

  # this function for ngrok alias
  # IMPROVED: 05-29-2024 10:25
  function ngrok(){
    # default ngrok command that redirects
    # to a new terminal so the current one
    # is available for other commands
    local ngrok_cmd='cmd.exe /c start ngrok "$@"'

    # check for dashes then do not
    # redirect to another terminal
    for arg in "$@"; do
      if [[ "$arg" == -* || "$arg" == --* ]]; then
        local ngrok_cmd='cmd.exe /c ngrok "$@"'
        break
      fi
    done

    # Check the current directory
    # because ngrok will work only
    # on windows'directory rather
    # than WSL's one so we move
    if [[ "$PWD" == "/mnt/"* ]]; then
      eval $ngrok_cmd
    else
      cd /mnt/c
      eval $ngrok_cmd
      cd - &>/dev/null
    fi
  }

  # Completion function for ngrok
  _ngrok_completion() {
    local cur
    cur="${COMP_WORDS[COMP_CWORD]}"

    # Define the list of possible completions
    local commands="api completion config credits diagnose help http service start tcp tls tunnel update version"

    # Provide completion options based on the current word being completed
    COMPREPLY=($(compgen -W "${commands}" -- "$cur"))
  }

  # Register the completion function for ngrok
  complete -F _ngrok_completion ngrok

  # this alias to launch process explorer
  alias prex="prex"

  # this function for prex alias
  function prex(){
    if [[ "$PWD" == "/mnt/"* ]]; then
      cmd.exe /c start procexp64
    else
      cd /mnt/c
      cmd.exe /c start procexp64
      cd - &>/dev/null
    fi
  }

  # Alias to call the windows npm
  alias npm="npm"

  # Function for npm alias
  function npm() {
    local npm_cmd='cmd.exe /c start npm "$@"'
    for arg in "$@"; do
      if [[ ("$arg" != "--verbose" || "$arg" != "-g") && ("$arg" == -* || "$arg" == --*) ]]; then
        local npm_cmd='cmd.exe /c npm "$@"'
        break
      fi
    done

    if [[ "$PWD" == "/mnt/"* ]]; then
      eval $npm_cmd
    else
      echo "${BOLD}${RED}Please execute this command inside Windows directory!"
    fi
  }

  # Alias to call the windows npx
  alias npx="npx"

  # Function for npx alias
  function npx() {
    local npx_cmd='cmd.exe /c start npx "$@"'
    for arg in "$@"; do
      if [[ "$arg" != "--verbose" && ("$arg" == -* || "$arg" == --*) ]]; then
        local npx_cmd='cmd.exe /c npx "$@"'
        break
      fi
    done

    if [[ "$PWD" == "/mnt/"* ]]; then
      eval $npx_cmd
    else
      echo "${BOLD}${RED}Please execute this command inside Windows directory!"
    fi
  }

  # Alias to call the windows vue
  alias vue="vue"

  # Function for vue alias
  function vue() {
    local vue_cmd='cmd.exe /c start vue "$@"'
    for arg in "$@"; do
      if [[ "$arg" != "--verbose" && ("$arg" == -* || "$arg" == --*) ]]; then
        local vue_cmd='cmd.exe /c vue "$@"'
        break
      fi
    done

    if [[ "$PWD" == "/mnt/"* ]]; then
      eval $vue_cmd
    else
      echo "${BOLD}${RED}Please execute this command inside Windows directory!"
    fi
  }

  # this alias to open apple music
  alias music="music"

  # this function for music alias
  function music(){
    if [[ "$PWD" == "/mnt/"* ]]; then
      cmd.exe /c start AppleMusic.exe
    else
      cd /mnt/c
      cmd.exe /c start AppleMusic.exe
      cd - &>/dev/null;
    fi
  }

  # this alias to launch xampp
  alias xampp="xampp"

  # this function for xampp alias
  function xampp(){
    if [[ "$PWD" == "/mnt/"* ]]; then
      cmd.exe /c start xampp-control.exe
    else
      cd /mnt/c
      cmd.exe /c start xampp-control.exe
      cd - &>/dev/null;
    fi
  }

  # this alias to open notepad
  alias ntp="ntp"

  # this function for ntp alias
  function ntp(){
    if [[ $# -eq 0 ]]; then
      cmd.exe /c start notepad.exe 2>/dev/null
    elif [[ $# -eq 1 ]]; then
      local formatted_path=$(wslpath -w .)
      cmd.exe /c start notepad.exe "$formatted_path\\$1" 2>/dev/null
    else
      echo "${BOLD} ■■▶ Usage : ntp file_to_open" && br;
    fi
  }

  # this alias to open VirtualBox
  alias vm="vm"

  # this function for vm alias
  function vm(){
    if [[ "$PWD" == "/mnt/"* ]]; then
      cmd.exe /c start VirtualBox.exe
    else
      cd /mnt/c
      cmd.exe /c start VirtualBox.exe
      cd - &>/dev/null;
    fi
  }

  # this alias to open wireshark
  alias wsh="wsh"

  # this alias for wsh alias
  function wsh(){
    if [[ "$PWD" == "/mnt/"* ]]; then
      cmd.exe /c start wireshark.exe
    else
      cd /mnt/c
      cmd.exe /c start wireshark.exe
      cd - &>/dev/null;
    fi
  }

  # this alias to open total commander
  alias tcmd="TOTALCMD64.exe && cv"

  # this alias to launch windows python
  alias python="python.exe"

  # this alias to launch windows go
  alias go="go"

  # this function for go alias
  function go(){
    # check if we are inside wsl directory
    # or inside a symbolic link
    if [[ "$PWD" == "/mnt/"* || -L "$PWD" ]]; then
      cmd.exe /c go $@
    else
      echo "${BOLD}${RED}Please execute this command inside Windows (/mnt/*) directory!"
    fi
  }

  # this alias to run rustc
  alias rustc="rustc"

  # this function for rustc alias
  function rustc(){
    # check if we are inside wsl directory
    # or inside a symbolic link
    if [[ "$PWD" == "/mnt/"* || -L "$PWD" ]]; then
      cmd.exe /c rustc $@
    else
      echo "${BOLD}${RED}Please execute this command inside Windows (/mnt/*) directory!"
    fi
  }

  # this alias to run cargo
  alias cargo="cargo"

  # this function for cargo alias
  function cargo(){
    # check if we are inside wsl directory
    # or inside a symbolic link
    if [[ "$PWD" == "/mnt/"* || -L "$PWD" ]]; then
      cmd.exe /c cargo $@
    else
      echo "${BOLD}${RED}Please execute this command inside Windows (/mnt/*) directory!"
    fi
  }

  # this alias to launch windows java
  alias java="java.exe"

  # this alias to launch javac windows
  alias javac="javac.exe"

  # this alias to launch jar windows
  alias jar="jar.exe"

  # Alias to call the windows pip
  alias pip="pip"

  # Function for pip alias
  function pip() {
    # check if we are inside wsl directory
    # or inside a symbolic link
    if [[ "$PWD" == "/mnt/"* || -L "$PWD" ]]; then
      cmd.exe /c pip "$@"
    else
      cd /mnt/c
      cmd.exe /c pip "$@"
      cd - &>/dev/null;
    fi
  }

  # this alias to use windows nslookup
  alias nslookup="nslookup"

  # this function for nslookup alias
  function nslookup(){
    if [[ "$PWD" == "/mnt/"* ]]; then
      cmd.exe /c nslookup "$@"
    else
      cd /mnt/c
      cmd.exe /c nslookup "$@"
      cd - &>/dev/null;
    fi
  }

  # this alias to use windows arp
  alias arp="arp"

  # this function for arp alias
  function arp(){
    if [[ "$PWD" == "/mnt/"* ]]; then
      cmd.exe /c arp "$@"
    else
      cd /mnt/c
      cmd.exe /c arp "$@"
      cd - &>/dev/null;
    fi
  }

  # this alias to run jupyter notebook
  alias jptr="jptr"

  # this function for jptr alias
  function jptr(){
    # check if we are inside wsl directory
    # or inside a symbolic link
    if [[ "$PWD" == "/mnt/"* || -L "$PWD" ]]; then
      cmd.exe /c start jupyter notebook
    else
      echo "${BOLD}${RED}Please execute this command inside Windows (/mnt/*) directory!"
    fi
  }

  # this alias to launch gta san andreas
  alias gta="gta"

  # this function for gta alias
  function gta(){
    cd /mnt/d/NTSOA/INSTALLED/GTA\ SAN\ ANDREAS
    cmd.exe /c start /affinity 2 gta_sa.exe
    cd - &>/dev/null
  }

  # this alias to open visual paradigm
  alias paradigm="paradigm"

  # this function for paradigm alias
  function paradigm(){
    cd /mnt/d/NTSOA/INSTALLED/VISUAL\ PARADIGM/Visual\ Paradigm\ CE\ 17.2/bin
    explorer.exe visual.lnk
    cd - &>/dev/null
  }

  # this alias open Bluestacks
  alias android="android"

  # this function for android alias
  function android(){
    cd /mnt/c/Program\ Files/BlueStacks_nxt
    cmd.exe /c start HD-Player.exe
    cd - &>/dev/null
  }

  #######################################################################
  ```
</details>

<details>
  <summary><strong> P10k Config</strong></summary>

  ```sh
  ### p10k Config

  # To customize prompt, run `p10k configure` or edit ~/.p10k.zsh.
  [[ ! -f ~/.p10k.zsh ]] || source ~/.p10k.zsh

  #######################################################################
  ```
</details>

<hr style="border: 0; height: 1px; background: #21262d;">