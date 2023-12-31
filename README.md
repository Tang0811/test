# Github
Git是一個分散式的版本控制軟體，GitHub則是一個存放Git的空間，也就是讓你放置程式原始碼的地方。
## 版本控制
為了不會改了一個小蟲，然後整個程式不能跑。
或者想要回到過去的版本，但是忘記改了什麼，導致回不去的窘境。
### 集中式版控
所有專案都放在單一台伺服器，需要有網路連進伺服器才能開發。
### 分散式版控
專案檔案放在遠端儲存庫，沒有網路也可以開發新版本。
   ![](https://hackmd.io/_uploads/SyZRJNm22.png)


## 使用流程
1. 建立一個目錄，以及使用`git init`指令建立一個這個專案的儲存庫（Repository）。

        Repository :專案儲存庫
            committed file :已提交檔案
             modified file :未提交/已修改檔案
              staged  file :準備要提交的暫存檔案
2. 接著在專案目錄下新增或修改檔案等開發工作，工作完成告一階段，就會提交一個專案新版本到Git本地端儲存庫裡。              

3. 若要使用GitHub來和其他人共享專案，開發者則需進一步使用Push指令，將本地端儲存庫的特定版本專案，推到遠端儲存庫上整併。

4. 下一次要展開開發工作時，則可先從遠端儲存庫將新版程式碼取回本地端儲存庫（此動作稱為Pull），再從本地端儲存庫放入工作目錄中（此動作稱為Checkout），就可繼續展開下一輪開發。

### 開發分版觀念：Master、Branch和Merge
主幹（Master）與分支（Branch）是稱呼專案的主要版本和分支版本。
主幹（Master）與分支（Branch）都是等價關係，
一般習慣將穩定版本稱主幹，其餘的變動、開發中版本則都稱作分支。
而合併（Merge）指令剛好相反，則是把兩個不同的分支版本，合併到其中一個分支上。
\
Git則提供了一個視覺化的版本線圖（commit graph），來呈現出主幹與各分支連結形成的樹狀架構。
建議，可以善用合併指令整併不必要的分支，將版本線圖整理清楚。


### 專案分版手法：Clone和Fork
        Clone :複製A作者的專案儲存庫內容
        Fork  :複製B作者的專案儲存庫內容
如果在開發者在GitHub上看到有興趣的專案，
可以執行Fork指令，把別人專案的遠端儲存庫複製到自己的遠端儲存庫，
再執行Clone指令，把自己遠端儲存庫的整個專案的所有內容（包括各版本）複製到本機端儲存庫。

### 資料同步指令：Push、Pull、Pull Request
    Push :上傳到遠端儲存庫
    Pull :下載至自己的本機端，並將遠端分支合併到本地分支。
      (不過，Pull並不像Clone指令會下載完整專案各版本內容。)
    Pull Request :更**主動地要求**第三方開發者納入自己開發的程式，將本地端儲存庫上的程式碼，整併到對方的儲存庫上。
開發者可以執行Pull取得其他人開放授權的遠端儲存庫上的程式碼，
也可以將自己修改的程式碼Push到可存取的第三者遠端儲存庫上。
透過推（Push）跟拉（Pull）兩個指令，開發者就能互相分享原始碼

## 實際使用

1. 產生ssh公私鑰

        ssh-keygen -t ed25519 -C “your_email@example.com”
2. 尋找公鑰訊息

        cat ~/.ssh/id_ed25519.pub
3. 把公鑰訊息貼到github上面
> 前往setting 尋找SSH and GPG keys 選項，把公鑰訊息貼上以及自己想個title名稱方便管理
4. 更改遠端伺服器
> 請自行把後面的地址改成自己的ssh git 地址

    git remote set-url CHER git@github.com:Tang0811/CHER.git
    git remote -v
>**git remote** 指令，主要是跟遠端有關的操作。
**add** 指令是指要加入一個遠端的節點。
在這裡的 **CHER** 是一個「代名詞」，指的是後面那串 GitHub 伺服器的位置。

:::spoiler git新增內容
    git init
    git add .
    git commit -m "first commit"
:::
5. 上傳

        git push CHER master
>這樣就會把 master 分支推上 origin 這個遠端節點所代表的位置，並且在上面建立一個名為 cat 同名分支（或更新進度）。
>master可以用沒有建立的分支名稱他會自己創建!

## 參考資料
[Git達人教你搞懂GitHub基礎觀念 - iThome](https://www.ithome.com.tw/news/95283)
[jerry boy's note - HackMD](https://hackmd.io/@LlhJnoVKQRKEJ8uZnAy3vw/SJqssQXhn)
[使用ssh上傳github - pixnet](https://darren1231.pixnet.net/blog/post/354617500-%E4%BD%BF%E7%94%A8ssh%E4%B8%8A%E5%82%B3github)

[更多的技巧需要補充進來ex:Stash](https://www.maxlist.xyz/2018/11/02/git_tutorial/)
