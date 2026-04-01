# Important information - please read

> [!WARNING]  
> **Not in active development.**

[Chrome installation instructions.](https://github.com/ara303/twMediaDownloader/issues/3#issuecomment-2119328940) Firefox support is [likely broken](https://github.com/ara303/twMediaDownloader/issues/1).

When the service formerly known as Twitter changed its primary domain name to X.com, the API was also moved (`api.x.com`) which broke this extension entirely.

This fork attempts to patch the extension to restore the basics that functioned prior to that domain name change. That is all this is.

Features relying on the public API, which was shut down _before_ the domain name change, will not be restored. If you use this, expect your browser's dev console to show errors as functions of the plugin try to contact since-shutdown endpoints. Please don't open issues asking for broken functionality to be restored (but you can open PRs...! 😉).

This is a pet project, made for myself primarily. Despite the partial breakages, there was enough working here I found useful. It was the only extension I found that provided a one-click method to extract the URL of a video hosted on Twitter's servers, which I find much easier to work with and share around.

> [!TIP]
> **Bulk downloading is broken.** If you must bulk download media, instead try [`twmd`](https://github.com/mmpx12/twitter-media-downloader).
>
> Installation is unintuitive but achievable. First, [download your relevant binary](https://github.com/mmpx12/twitter-media-downloader/releases/tag/v1.14.2). Once you've extracted it, try running `twmd -u=<username> -a -L`. It will return an error to you at first, but then let you provide the `auth_token` and `ct0` values it needs to actually work the next time you re-run that command. In Chrome/Chromium, open a new X.com tab where you're logged in and let your timeline finish loading. Then right-click, go to Inspect > Application > Cookies > https://x.com, and copy the values for `auth_token` and `ct0` in here.
> 
------

**From this point onwards, the readme is outdated!** The original author removed the extension from the Chrome/Firefox extension sites so those links won't work.

--------

--------

--------

Twitter メディアダウンローダ (twMediaDownloader)
================================================

- License: The MIT license  
- Copyright (c) 2016 風柳(furyu)  
- 対象ブラウザ： Google Chrome、Firefox

[Web 版公式 Twitter](https://x.com/) のメディア（画像／動画）を、原寸サイズでダウンロードするためのスクリプト。  
※個別ツイートのメディアダウンロードについては、[TweetDeck](https://tweetdeck.x.com/) でも対応。  


■ インストール方法 
---
### Chrome 拡張機能版  
Google Chrome で、  

> [Twitter メディアダウンローダ― - Chrome ウェブストア](https://chrome.google.com/webstore/detail/twitter-media-downloader/cblpjenafgeohmnjknfhpdbdljfkndig?hl=ja)  

より拡張機能を追加する。  


### Firefox Quantum (WebExtentions)版  
Firefox Quantum で、  

> [Twitter メディアダウンローダ – Firefox 向けアドオン](https://addons.mozilla.org/ja/firefox/addon/tw-media-downloader/)  

よりアドオンを追加する。  


### ユーザースクリプト版
Firefox＋<s>[Greasemonkey](https://addons.mozilla.org/ja/firefox/addon/greasemonkey/)</s>[Tampermonkey](https://addons.mozilla.org/ja/firefox/addon/tampermonkey/)、Google Chrome＋[Tampermonkey](https://chrome.google.com/webstore/detail/tampermonkey/dhdgffkkebhmkfjojejmpbldmpobfkfo?hl=ja) の環境で、  

> [Twitter Media Downloader for new x.com 2019](http://furyutei.github.io/twMediaDownloader/src/js/main_react.user.js)  

> [Twitter Media Downloader for TweetDeck](http://furyutei.github.io/twMediaDownloader/src/js/main_tweetdeck.user.js)  

> [Twitter Media Downloader for old x.com (twMediaDownloader.user.js)](https://furyutei.work/userjs/furyutei/twMediaDownloader.user.js)  
                                
をクリックし、指示に従ってインストール。  
※ Firefox では Quantum(57) + Greasemonkey 4 より動作しなくなった（代わりに Tampermonkey を使用すること）。  


■ 使い方
---
[Web 版公式 Twitter](https://x.com/) 上で、ユーザータイムラインや検索タイムラインを開くと、「メディア↓」のようなリンクが挿入される。  
![下向き矢印のリンク](https://cdn-ak.f.st-hatena.com/images/fotolife/f/furyu-tei/20160723/20160723224518.jpg)  

これをクリックするとダイアログが表示されるので、[開始]ボタンをクリックすると、原寸画像/動画の ZIP 化が開始される。  
※ ZIP 化の進捗は、下部にログ出力される。  
![ダイアログ](https://cdn-ak2.f.st-hatena.com/images/fotolife/f/furyu-tei/20171029/20171029090641.png)  

ZIP 化が完了するか、もしくは[停止]を押すと、対象となる画像/動画ファイルをまとめた ZIP ファイルがダウンロードされる。  
※ ログの内容も ZIP の中に保存される。

必要に応じて、保存対象となるツイートの Tweet ID 範囲、および、ツイートの制限数を指定可能。  
※デフォルト(範囲空白)の状態では、Tweet ID 範囲は全てで、ツイートの制限数にのみ制限される。  

また、各メディア付ツイートにもダウンロード用のリンクが追加され、個別にダウンロードすることも可能。  
※ Chrome 拡張機能の場合、この機能は ON/OFF できる。  


■ 外部ライブラリなど
---
- [jQuery](https://jquery.com/), [jquery/jquery: jQuery JavaScript Library](https://github.com/jquery/jquery)  
    [License | jQuery Foundation](https://jquery.org/license/)  
    [The MIT License](https://tldrlegal.com/license/mit-license)  

- [JSZip](https://stuk.github.io/jszip/)  
    Copyright (c) 2009-2014 Stuart Knightley, David Duponchel, Franz Buchinger, António Afonso  
    [The MIT License](https://github.com/Stuk/jszip/blob/master/LICENSE.markdown)  

- [MikeMcl/decimal.js: An arbitrary-precision Decimal type for JavaScript](https://github.com/MikeMcl/decimal.js)  
    Copyright (c) 2016, 2017 Michael Mclaughlin  
    [The MIT Licence](https://github.com/MikeMcl/decimal.js/blob/master/LICENCE.md)  

- [lambtron/chrome-extension-twitter-oauth-example: Chrome Extension Twitter Oauth Example](https://github.com/lambtron/chrome-extension-twitter-oauth-example)  
    Copyright (c) 2017 Andy Jiang  
    [The MIT Licence](https://github.com/lambtron/chrome-extension-twitter-oauth-example/blob/master/LICENSE)  

- [sha1.js](http://pajhome.org.uk/crypt/md5/sha1.html)  
    Copyright Paul Johnston 2000 - 2009
    The BSD License

- [oauth.js](http://code.google.com/p/oauth/source/browse/code/javascript/oauth.js)(^1)  
    Copyright 2008 Netflix, Inc.
    [The Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0)  
    (^1) archived: [oauth.js](https://web.archive.org/web/20130921042751/http://code.google.com/p/oauth/source/browse/code/javascript/oauth.js)  

- [jsTwitterOAuth/twitter-api.js](https://github.com/furyutei/jsTwitterOAuth/blob/master/src/js/twitter-oauth/twitter-api.js)  
    Copyright (c) 2018 風柳 (furyu)  
    [MIT License](https://github.com/furyutei/jsTwitterOAuth/blob/master/LICENSE)  


■ 関連記事
---
- [Twitter メディアダウンローダ：ユーザータイムラインの原寸画像をまとめてダウンロードするユーザースクリプト(PC用Google Chrome・Firefox等対応) - 風柳メモ](http://furyu.hatenablog.com/entry/20160723/1469282864)
- [Twitter 原寸びゅー：Twitterの原寸画像を開くGoogle Chrome拡張機能＆ユーザースクリプト公開 - 風柳メモ](http://furyu.hatenablog.com/entry/20160116/1452871567)  
