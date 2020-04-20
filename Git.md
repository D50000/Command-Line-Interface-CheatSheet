==================  git bash  ==================
https://website-proxy.backlogtool.com/git-tutorial/tw/reference/

>> Customized script in ~/.git/config:
[alias]
	review = push origin HEAD:refs/for/master
	amend = commit -a --amend

>> For revert last commit
$git reset HEAD^

>> For updating source code:
$git pull --rebase

>> For save, show, load the current step:
$git stash save
$git stash list
$git stash pop