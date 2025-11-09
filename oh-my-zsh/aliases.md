function develop {
git checkout develop;
git pull origin develop;
git fetch -ap;
git checkout -;
}
function describe {
kubectl describe pod ${1} -n develop
}
alias gdev='develop'
alias describe='describe'
alias monit='watch "ps xufgc -y --headers -U ${USER}"'
alias docom='docker-compose'
alias g="git"
alias gt="g status -bs"
alias gc="g checkout"
alias gb="g checkout -b"
alias gc="g checkout"
alias gp="g pull"
alias gbase="g rebase develop"
alias gst="g stash"
alias gpop="g stash pop"
alias gadd="g add -p"
branch_name=$(git branch | grep -e "^\*" | cut -d " " -f 2)
alias gpush="git push origin ${branch_name}"
alias gmit="g commit -m"
alias dup="docker-compose up --build"
alias down="docker-compose down -v"
alias drest="docker-compose restart ${1}"
alias pip=/usr/local/bin/pip3
alias python=/usr/bin/python3
alias l="exa -bFlaHhim --icons --group-directories-first --time-style long-iso --git --git-ignore"
alias tree="exa -TbFlahim --icons --group-directories-first --time-style long-iso --git --git-ignore"
