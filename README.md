# TutGit
Thuc hanh GIT

---------------------------Lenh Git HUB(Cau truc: working-stage-head->reposerver)------------------------------------

git config -l

git config --global user.name "vfaTrungnh"

git config --global user.email "vfa.trungnh@gmail.com"

git lg:xem log ngan gon,xuc tich hon

git log:xem tat ca cac log

git reflog:xem tat ca cac log(bao gom log tam,commit behind .....)

gitk


-Git checkout:

git checkout tenfile :delete 1 file khi lam tren local nhung chua commit

git checkout -- . :Bỏ tất cả những thay đổi ở local chưa được commit (những file mới vẫn còn tồn tại trong source sau lệnh này)

git checkout HEAD~1 :quay ve truoc 1 commit,nhung You are in 'detached HEAD' state

git checkout HEAD~1 tenfile ::un commit 1 file cho 1 commit(tuong tu cho 2 commit...),van giu code da sua,quay ve nam o stage

git checkout -t origin/branch_name : lay 1 remote branch tren repo,chua co tren local(cua 1 nguoi khac dang lam,minh lam tiep)

git checkout -b feature/72328 :Tao branch(hoac git branch <new_branch>

git checkout master           :chuyen ve branch master


git pull		      :get source moi nhat ve

git merge feature/72328       :merge branch master vao branch72328(truoc tien phai chuyen qua branch master truoc,cay history sau khi merge se theo thu tu commit)

git add name_of_file          :add file moi vao

git rm name_of_file           :remove file 

git commit -a -m "Ghi chú Commit":Commit thay doi vao branh local

git commit --amend -m "Merge 3 ex6 branch 'develop' of https://github.com/nguyenhuutrung/TutGit into develop" : thay doi message vua commit

git push origin feature/72328 :Push to remote branch

git stash(luu trang thai dang lam viec hien tai vo stash va quay ve luc dau,chua sua gi,chuyen qua nhanh khac de lam viec,sau do chuyen ve nhanh do,lay code da dua vao stash lai:git stash pop)

git branch -a                 : xem cac nhanh dang co

git branch new_branch_name 9a2e560..: tao 1 branch tu commit

git cherry-pick 9a2e560 :Lệnh "cherry-pick" sẽ sao chép một "commit", tạo một "commit" mới trên nhánh hiện tại với nội dung giống hệt và "patch" thành một "commit" khác.

git show 62c01ee974dd4983f172413e8881eb9bd6297235 L xem cac file da commit cua 1 note trong git log

git rebase master             :lay commit cuoi cung tren master,roi noi nhanh hien tai vao(dang dung o nhanh feature),commit rebase o tren cung

git remote -v

git remote set-url origin git@github.com:nguyenhuutrung/TutGit.git : thay doi remote cua github

git credential-cache exit : xoa cache


-GIT FETCH(git pull does a git fetch,followed by a git merge)

git fetch origin develop :se tao 1 nhanh tam FETCH_HEAD

git diff FETCH_HEAD :so sanh nhanh dang dung voi nhanh FETCH_HEAD

git checkout FETCH_HEAD  :xem du lieu nhanh tam do

git merge FETCH_HEAD :neu muon merge vao nhanh dang dung


-Git reset:
git reset HEAD~1	:undo(xoa) 1 commit(tuong tu cho 2 commit...),van giu code da sua,nam o working dir

git reset --hard HEAD~1 :undo(xoa) 1 commit(tuong tu cho 2 commit...),remove code da sua(git reset --hard ORIG_HEAD:lay lai commit vua reset)

git reset --hard e3ccedc034d86ace49673085caf161e36720e720 : remove 1 comit va tro ve 1 commit khac tren local

git reset --hard <remote_branch> :Undo mọi thay đổi và commits trên local (chưa push lên remote) và đưa local branch về giống với remote branch

git reset HEAD tenfile :un"add,update" 1 file to stage

git reset HEAD~1 tenfile :(ko nen dung vi dung se tao ra 1 file da add tren stg,1 file tren stg) uncommit 1 file cho 1 commit(tuong tu cho 2 commit...),van giu code da sua,quay ve nam o stage



-Undo (delete) commit cuối trên remote branch

$ git pull # Lấy source mới nhất từ remote

$ git reset --hard HEAD\^ :sau khi reset,chua dua len server repo co the dung "pull origin origin/branchname" de lay lai source truoc khi reset tren server)

$ git push -f


-Revert 1 commit trên remote branch (tạo 1 commit để thực hiện việc undo):

$ git revert <commit> (git revert HEAD~1) :sau khi revert,co the dung reset de lay lai source truoc khi revert

$ git push


-Delete local branch,remote branch

git push origin --delete 2345_create_live  =>remove remote branch(fai remove remote truoc,sau do remove local)

git branch -d 2345_create_live  =>remove branch

git branch -r -d origin/feature3/2  =>remove remote branch(chi thay tren local ko co hieu luc tren server repo).Neu muon thay lai: git fetch -p origin (khi con tren server repo)


-Cau hinh git log PRO hon

git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"

-------------------------------------------------------------------

ssh-add ~/.ssh/id_rsa
ssh-add -D  :delete id_rsa key
ssh-add -l   :list id_rsa key

------------------QUY TRINH LAM VIEC GITHUB-------------------------

Khi push bi loi thi nen chay cau lenh: git credential-cache exit

1.Tai branch master pull suorce moi nhat ve

git checkout master

git pull

2.Tao 1 branch moi tu branch master moi nhat

git checkout -b feature/72328

3.Sau khi lam xong add file,commit file

git add name_of_file

git commit -m "Done Trungnh add API  ticket 72328"

4.Push len server

git push origin feature/72328

5.Neu co xung dot thi sua file do,sau do add,commit lai

git add name_of_file

git commit -a -m "Ghi chú Commit"

6.Reset cac commit cuc bo

git fetch origin

git reset --hard origin/master

7.Tao pull request:

comment : Please merge this pull request ticket xxxx
