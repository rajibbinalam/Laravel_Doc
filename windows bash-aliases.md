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
  alias pam:r='php artisan migrate:refresh'
  alias pam:rs='php artisan migrate:refresh --seed'
  alias cu='composer update'
  alias ci='composer install'
  alias cda='composer dump-autoload -o'
  ```
  
  
  
  #### NB: It'll work using GitBash not in powerShell
  More Resources: https://laravel-news.com/bash-aliases
