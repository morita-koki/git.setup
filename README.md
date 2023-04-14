# git.setup

```bash
$ git --version
(gitが入ってなければ下のコマンドを実行)
($ sudo apt isntall git)

$ git --version
(versionがひょうじされればOK)

$ cd ~

$ mkdir .ssh

$ ssh-keygen -t rsa
(適当にEnter連打)

$ ls ./ssh
id_rsa id_rsa.pub

$ clip.exe < .ssh/id_rsa.pub
(※これをgithub -> setting -> SSH and GPG keyのところに追加する)

$  cat << EOT >> .ssh/config
Host github.com
	IdentityFile ~/.ssh/id_rsa
	User git
EOT

$ ssh -T github.com
Hi morita-koki! You've successfully authenticated, but GitHub does not provide shell access.
(こんなのが表示されればOK。初回は変なの表示されるかも。うまく行かないときは、ssh -vT github.com等でデバッグ）

$ git config --global user.name ${username} // githubのusername
$ git config --global user.email ${email} // githubのemail

$ git config --list
user.name=morita-koki
user.email=**********

(clone, push, pullできるか確認)
$ git clone git@github.com:morita-koki/git.setup.git
$ echo "this is the first commit from new PC" >> file.txt
$ git add .
$ git commit -m "this is from new PC"
$ git push origin main
$ git pull origin main

```

