# php-auto-indent

**Fail-safe php auto indent**

`php-auto-indent` is a command line tool you can use to format php code using [PEAR](http://pear.php.net/manual/en/standards.php), [PSR-1](http://www.php-fig.org/psr/psr-1/) and [PSR-2](http://www.php-fig.org/psr/psr-2/) coding standards.

It checks the resulting code for syntax errors, just to keep things safe...

## Requirements

`php-auto-indent` relies on well known tools :
- https://github.com/clbustos/PHP_Beautifier
- https://github.com/FriendsOfPHP/PHP-CS-Fixer

## Install

You can install it in your `~/bin` directory. Please ensure it's in your `$PATH`.

```bash
mkdir ~/bin 2>/dev/null && echo 'export PATH="~/bin:$PATH"' >> ~/.bashrc
```

Then clone the repository and symlink the script:
```bash
git clone https://github.com/pa-de-solminihac/php-auto-indent ~/bin/php-auto-indent-git && ln -s ~/bin/php-auto-indent-git/php-auto-indent ~/bin/php-auto-indent
```


## Usage

**Format any PHP file**

```bash
php-auto-indent [FILE]
```

You can use it with stdin too : 
```bash
cat [FILE] | php-auto-indent - > [NEWFILE]
```

For recursive use, try :
```bash
php-auto-indent -r *
```


## Goodies

### Vim integration

Paste this in your `.vimrc`, and format your code using `CTRL`+`b`

```vim
" format PHP code with php-auto-indent using <c-b>
func! PHPAutoIndent(mode) range
    :set ff=unix
    if (a:mode == 'visual')
        :exe "'<,'>!php-auto-indent -"
    else
        :exe "%!php-auto-indent -"
    endif
endfunc
noremap <c-b> :call PHPAutoIndent('normal')<CR>
vnoremap <c-b> :call PHPAutoIndent('visual')<CR>
```

### Rest of the world

Being a command line tool able to work with standard input, `php-auto-indent` should be easy to integrate with your favorite tools.
