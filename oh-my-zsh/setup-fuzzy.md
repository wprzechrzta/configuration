

# References
- https://kaliex.co/supercharge-your-zsh-terminal-with-fzf-a-simple-guide/



1. Add .oh-my-zsh/custom/fuzzy-commands.zsh

```shell
_join-lines() {
  local item
  while read item; do
    echo -n "${(q)item} "
  done
}

_cc() {
  cat $HOME/cmd/cmd* | sed '/^$/d'| grep -v '#'| fzf
}

eval "fzf-cc-widget() { local result=\$(_cc); zle reset-prompt; LBUFFER+=\$result }"
eval "zle -N fzf-cc-widget"
eval "bindkey '^g^u' fzf-cc-widget"
```