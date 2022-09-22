# dotfiles para configuração do ambiente de desenvolvimento

---

## Configuração

Incluir ao final do arquivo .bashrc da seguinte forma:

```bash
if [ -f "$HOME/Documents/dotfiles/include" ]; then
        source "$HOME/Documents/dotfiles/include";
fi
```

---
