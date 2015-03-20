<table>
<tr>
<td>
GTK+ 2.x 開發的自由 BBS 連線軟體 Copyright © 2005<br>
<br>
授權方式： <a href='http://www.gnu.org/copyleft/gpl.html'>GNU General Public License</a> (GPL)<br>
<br>
開發者:<br>
<br>
<ul><li><a href='http://pcman.ptt.cc/'>Hong Jen Yee 洪任諭 (pcman)</a> (原作者及主要開發者)<br>
</li><li><a href='http://about.me/jserv'>Jim Huang 黃敬群 (jserv)</a>
</li><li><a href='http://stu.csie.ncnu.edu.tw/~kanru.96/'>Kanru Chen 陳侃如 (kanru)</a>
</li><li>Chia I Wu 吳佳一 (olv)<br>
</li><li><a href='http://about.me/fourdollars'>Shih-Yuan Lee 李世元 (FourDollars)</a>
</li><li><a href='http://www.utcr.org/'>Youchen Lee 李宥辰 (copyleft)</a>
</li><li><a href='http://emfoxzhou.googlepages.com/'>Emfox Zhou 周玮 (emfox)</a>
</td>
<td>
<br>
</td>
</tr>
</table></li></ul>

# 取得方式 #

  * 發行版本：[按此處下載 PCMan X 1.0 以前的發行檔案](http://pcmanx-gtk2.googlecode.com/svn/website/release/)
    * 最新版本：
      * [pcmanx-gtk2-1.2.tar.xz](http://code.google.com/p/pcmanx-gtk2/downloads/detail?name=pcmanx-gtk2-1.2.tar.xz)
    * 新增功能：
      * Use consistent naming: PCManX
      * Allow users to search selected text through Web search engine
      * Handle malformed URL properly
      * Usability enhancement for Unity desktop envionment
      * Add new interface to show and hide toolbar
      * Remember maximized state
      * Improve the performance of cairo caret
    * 錯誤修正：
      * SegFault when $LANG is not set
      * Replace system() with execlp() for sake of security
      * Use g\_spawn\_async() instead of fork()/execlp() to prevent crash
      * Build failure when configured as --disable-docklet
      * Status bar appears in simple mode
      * FcFontSort() should no longer use `NULL' as the value of `result'
      * Change "class" and "name" hints for a window.
      * Add "StartupNotify=true"
      * Fix the invisible cursor issue
      * Fix a bug that NancyBot incorrect parsing the input string on 64bit OS.

  * 預先編譯版本：
    * [Debian](http://packages.qa.debian.org/p/pcmanx-gtk2.html)/[Ubuntu](http://packages.ubuntu.com/source/pcmanx-gtk2)
      * apt-get install pcmanx-gtk2
    * [Fedora](http://rpms.famillecollet.com/rpmphp/zoom.php?rpm=pcmanx-gtk2)
      * yum install pcmanx-gtk2
    * [openSUSE](http://software.opensuse.org/search?q=pcmanx-gtk2&baseproject=ALL&lang=zh_TW&include_home=true&exclude_debug=true)
      * zypper install pcmanx-gtk2
    * Mandriva
      * urpmi pcmanx-gtk2
  * 取得開發中的最新程式碼，請透過 [GitHub 存取](https://github.com/pcman-bbs/pcmanx)

# 編譯需求 #

  * GTK+ 2.4 以上，以 Debian 為例： apt-get install [libgtk2.0-dev](http://packages.debian.org/stable/libdevel/libgtk2.0-dev)
  * Xft 2.x，以 Debian 為例： apt-get install [libxft-dev](http://packages.debian.org/stable/libdevel/libxft-dev)
  * Intltool，以 Debian 為例： apt-get install [intltool](http://packages.debian.org/stable/devel/intltool) [intltool-debian](http://packages.debian.org/stable/devel/intltool-debian)
  * Automake 1.10，以 Debian 為例： apt-get install [automake](http://packages.debian.org/stable/devel/automake)
  * libtool，以 Debian 為例： apt-get install [libtool](http://packages.debian.org/stable/devel/libtool)

注意

  * 後兩者只有從 Git 取出的開發版本需要，一般的發行版本只需要前三者

# 編譯方式 #

  * 開發中的功能與選項，請閱讀 [README](https://pcmanx-gtk2.googlecode.com/git/README)
  * ./autogen.sh (只有從 Subversion 取出的開發版本需要)
  * ./configure --help 查看編譯選項，因為功能持續開發中，項目隨時可能增減
  * ./configure [編譯選項，請參閱上行]
  * make ; make install

# Nancy Bot 簡易使用說明 #

Nancy Bot 是用來自動回覆 BBS 水球的機器人。

開啟/關閉方式：
  * 在 view 選單中，可以針對本連線或所有的連線選擇開啟或關閉機器人。
  * 目前只提供一個機器人，您無法選用其他的機器人，我們將在未來的發行版本中提供多機器人支援。

設定方式：
  * 預設的 Bot 設定檔在 ~/.pcmanx/nancy\_bot/ 內的 default.conf, default\_msg.data和 default\_usages.data，設定方式請參考 /usr/share/pcmanx/nancy\_bot/ 內的 example files。
  * Bot 會將它看不懂的句子放到 default\_unknow.log，您可以將它修改後附加到 default\_msg.data 之後，使它學習到原先看不懂的句子。

# 「自動更新 BBS 站台列表」設定說明 #

自 2005.09.24 起，[FreeYM 陽明自由軟體站](http://free.ym.edu.tw/wiki/)提供用 Wiki 收集全球中文 BBS 站台列表的服務。該系統經過設定，每隔一小時會自動跑程式更新，把 Wiki 上收集到的資料整理成 PCMan X 使用的站台列表格式。這項服務，搭配 crontab 的設定，就可以達到自動更新 BBS 站台列表。
簡單的設定方式如下：
  * 先確定系統上有 crontab 和 wget 這兩個程式，沒有的話請安裝
  * 執行 crontab -e
  * 在開啟的設定檔裡面加入這行：40 20 `* * *` wget -O ~/.pcmanx/sitelist `http://free.ym.edu.tw/pcman/site_list.utf8`
  * 上面那行的 40 20 表示在每天的晚上 20:40 執行更新，這時間可以隨個人需要自己改。這只是簡單範例，詳細用法請自行查詢。

# Screenshots #

![http://pcmanx-gtk2.googlecode.com/svn/website/screenshots/1.png](http://pcmanx-gtk2.googlecode.com/svn/website/screenshots/1.png)

設定及操作介面都很簡單且直觀。

![http://pcmanx-gtk2.googlecode.com/svn/website/screenshots/2.png](http://pcmanx-gtk2.googlecode.com/svn/website/screenshots/2.png)

收到水球時連線標籤變色，並且可在右下角彈出類似 MSN 的小視窗，點擊後會切換到有來訊的連線。

此外，畫面右下角的系統列中多了一個圖示，點擊可以快速顯示或隱藏 PCMan X 視窗。

![http://pcmanx-gtk2.googlecode.com/svn/website/screenshots/4.png](http://pcmanx-gtk2.googlecode.com/svn/website/screenshots/4.png)

內建兩岸中文 BBS 站台列表，有大量站台位址可供快速查詢使用。

![http://pcmanx-gtk2.googlecode.com/svn/website/screenshots/6.png](http://pcmanx-gtk2.googlecode.com/svn/website/screenshots/6.png)

具有自動登入功能，只要簡單設定，就可以幫你代填帳號密碼，快速登入 BBS 站

![http://pcmanx-gtk2.googlecode.com/svn/website/screenshots/8.png](http://pcmanx-gtk2.googlecode.com/svn/website/screenshots/8.png)

內建多種豐富的 BBS 可愛表情符號，按下 Ctrl + Enter 即可叫出。

![http://pcmanx-gtk2.googlecode.com/svn/website/screenshots/3.png](http://pcmanx-gtk2.googlecode.com/svn/website/screenshots/3.png)

可以用相當簡單的方式編輯「我的最愛」，即可從選單當中快速連線常用站台。

![http://pcmanx-gtk2.googlecode.com/svn/website/screenshots/5.png](http://pcmanx-gtk2.googlecode.com/svn/website/screenshots/5.png)