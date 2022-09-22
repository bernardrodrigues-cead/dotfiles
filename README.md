# dotfiles para configuração do ambiente de desenvolvimento

---

## Configuração

Instalar:
```bash
apt install python3-virtualenv && apt install python3-virtualenvwrapper
```

Incluir ao final do arquivo .bashrc da seguinte forma:

```bash
if [ -f "$HOME/Documents/dotfiles/include" ]; then
        source "$HOME/Documents/dotfiles/include";
fi
```

### Observação:

* É sempre importante criar o caminho da variável **PROJECT_HOME**: nesse caso, **$HOME/Documents/projects/python**.
* É importante verificar o caminho para **virtualenvwrapper.sh** e **virtualenvwrapper_lazy.sh** (uma dica é utilizar **which**). As localizações serão utilizadas na variável **VIRTUALENVWRAPPER_SCRIPT** e no comando **source** do arquivo **venv**.
* Verificar se o terminal está configurado como **login** (/bin/bash, /bin/sh, etc...) ou somente **shell** ($SHELL). 

### Observação (Django):

* É importante adaptar as variáveis **PORT, DB_USER, DATABASE, PROJECT e SRC** para o projeto em questão, conforme as definições da porta utilizada, do banco de dados e caminho do projeto e aplicação.

---
