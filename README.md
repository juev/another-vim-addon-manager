# another VIM Addon Manager

## English

### Installing

The installation process to clone this repository to the directory where the files should be located configuration VIM, usually the directory `~/.vim`:

    $ git clone https://github.com/Juev/another-vim-addon-manager.git ~/.vim

After that, just go to the directory and run the command:

    ~/.vim $ rake

This will set the extension `vim-pathogen`, which is required for the manager.

### About

Presented Rakefile makes it quite easy to manage additions to the editor vim. To work, the system must be installed `ruby`, `rake` and `git`.

The basic principle is to change the yaml-file `plugins.yaml`, which is automatically created in the current directory. To add an extension to the editor vim is enough to specify the address of his git-repository, and to remove -- accordingly, remove the description of the repository from the specified file. After that, you simply call the command `rake` to one of the arguments:

    $ rake -T

    rake clean # Remove excess plugins in bundle directory
    rake default # Install new and remove excess plugins in bundle directory
    rake install # Install new plugins in bundle directory
    rake list # List plugins in bundle directory
    rake update # Update plugins in bundle directory

When you run `rake` no arguments clears the bundle directory and then install new extensions, if they were specified in the configuration file.

By default, if the configuration file was not created in advance, during the first start a new file, which specifies only one extension - `vim-pathogen`, which is required to operate the system.

The minimum required file `vimrc` submit to the repository. It contains the line to activate the extension `vim-pathogen`.

    runtime bundle/vim-pathogen/autoload/pathogen.vim

    call pathogen#infect()
    syntax on
    filetype plugin indent on

If necessary, you can add the necessary options at the end of the file `vimrc`.

### TODO

 - Add an exception directory `bundle/config` for the files the user configuration

## Russian

### Установка

Для установки достатоно клонировать данный репозиторий в директорию, где должны располагаться файлы конфигурации VIM, обычно это директория `~/.vim`:

    $ git clone https://github.com/Juev/another-vim-addon-manager.git ~/.vim

После чего достаточно перейти в указанную директорию и выполнить команду:

    ~/.vim $ rake

Будет установлено расширение `vim-pathogen`, которое требуется для работы менеджера.

### Описание

Представленный Rakefile позволяет довольно просто управлять дополнениями в редакторе vim. Для работы в системе должны быть устновлены `ruby`, `rake` и `git`.

Основной принцип заключается в изменении yaml-файла `plugins.yaml`, который автоматически создается в текущей директории. Для добавления расширения в редактор vim достаточно указать адрес его git-репозитория, а для удаления -- соответственно, удалить описание данного репозитория из указанного файла. После чего достаточно вызвать команду `rake` с одним из аргументов:

    $ rake -T

    rake clean    # Remove excess plugins in bundle directory
    rake default  # Install new and remove excess plugins in bundle directory
    rake install  # Install new plugins in bundle directory
    rake list     # List plugins in bundle directory
    rake update   # Update plugins in bundle directory

При запуске `rake` без аргументов производится очистка директории bundle и последующая установка новых расширений, если они были указаны в файле конфигурации.

По умолчанию, если файл конфигурации не был создан заранее, во время первого запуска создается новый файл, в котором указывается только одно расширение -- `vim-pathogen`, которое требуется для работы всей системы.

Минимально необходимый файл `vimrc` представен в репозитории. Он содержит в себе строки для активизации расширения `vim-pathogen`.

    runtime bundle/vim-pathogen/autoload/pathogen.vim

    call pathogen#infect()
    syntax on
    filetype plugin indent on

При необходимости, можно добавлять необходимые опции в конце файла `vimrc`.

### TODO

 - добавить в исключения директорию `bundle/config` для размещения файлов конфигурации пользователя
