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
  alias pa:seed="php artisan db:seed"
  ```
  
  
  
  #### NB: It'll work using GitBash not in powerShell
  More Resources: https://laravel-news.com/bash-aliases
