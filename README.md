jayzh1010.github.io
===================

### personal blog, edit file in branch[source], deploy into branch [master]


#### to ensure the history of master branch, i have do sth:

1. do `mv .deploy/_git .deploy/.git` after `git pull origin source`
2. do `mv .deploy/.git .deploy/_git` after deploy the post(`hexo d`).

#### totally step

1. git clone
2. git checkout source
3. mv .deploy/_git .deploy/.git
4. write sth
5. hexo g && hexo d
6. mv .deploy/.git .deploy/_git
7. git add . && git commit -a && git push origin source
8. git checkout master && git pull origin
