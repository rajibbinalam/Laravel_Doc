### Windows Bash Aliases

1. goto: ```C:\User\<username>\.bashrc``` (Edit / Make file) this code and save
  ```sh
  if [ -f ~/.bash_aliases ]; then
  . ~/.bash_aliases
  fi
  ```
2. Make ```.bash_aliases``` file and Edit => 
  ```sh
  alias pa="php artisan"
  alias ser="php artisan ser"
  alias art="php artisan tinker"
  alias pa:seed="php artisan db:seed"
  alias pa:clr="php artisan optimize:clear"
  alias pam='php artisan migrate'
  alias pam:r='php artisan migrate:rollback'
  alias pam:s='php artisan migrate:status'
  alias pam:rs='php artisan migrate:refresh --seed'
  alias pam:fs='php artisan migrate:fresh --seed'
  alias cu='composer update'
  alias ci='composer install'
  alias pcu='php composer.phar update'
  alias pci='php composer.phar install'
  alias cdu='composer dump-autoload -o'
  alias ser1="php artisan ser --port=8001"
  alias ser2="php artisan ser --port=8002"
  alias ser3="php artisan ser --port=8003"
  alias ser4="php artisan ser --port=8004"
  alias ser5="php artisan ser --port=8005"
  alias ser6="php artisan ser --port=8006"
  alias ser7="php artisan ser --port=8007"
  alias ser8="php artisan ser --port=8008"
  alias ser9="php artisan ser --port=8009"
  alias ser10="php artisan ser --port=80010"
  alias ser11="php artisan ser --port=80011"
  alias ser12="php artisan ser --port=80012"
  alias ser13="php artisan ser --port=80013"
  alias ser14="php artisan ser --port=80014"
  alias ser15="php artisan ser --port=80015"
  ```
  
  
  
  #### NB: It'll work using GitBash not in powerShell
  More Resources: https://laravel-news.com/bash-aliases


### Linux or Mac OS Bash Alias
```sh
# For bash
nano ~/.bashrc
# For zsh
nano ~/.zshrc
```
#### Then Past the Alias code in the editor and then ctl+X to save and ext
#### If want to Moduler (separate file):
__1. in__ .bashrc:
```sh
  if [ -f ~/.bash_aliases ]; then
  . ~/.bash_aliases
  fi
```
__2. in__ .bash_aliases (or make any name of the file)
```sh
# past the alias CODE
```
