# このリポジトリについて

* GitHubを利用した集団での開発フローを確立・学習するためのリポジトリです。
* お試し用の**Public**リポジトリなので、**下手なことは書かないように**

# 共有リポジトリ構成について

## リポジトリ

以下の２つを自動同期して、共有リポジトリにします。

* 主: GitHub(プライベートリポジトリ)
* 副: 220のサーバ上のGitリポジトリ

## 役割

* 通常運営
    * GitHubに変更があれば、220に自動pushする構造。
    * 220のリポジトリはブランチを固定して、ステージング環境としても利用する。
* 非常時（GitHubでなにかあったとき)
    * 主リポジトリとして220サーバを使う

---

# ワークフロー

* こういう運用になる
    * [GitHub初心者はForkしない方のPull Requestから入門しよう // qnyp blog](http://blog.qnyp.com/2013/05/28/pull-request-for-github-beginners/)

---

# 現状での課題

## euc-jp が化ける

* サマリー画面では化ける  
* whole file を表示して、編集するときは化けない
    * 手元のGitHubアプリで開くときも化けない
        * ※使用するエディタに依存

* 対策
    * 何らかの自動処理で文字コードをutf-8に変換して共有リポジトリに収める。そして、本番やステージングではeuc-jpに変換する手があるが、少々リスキー
   * ブラウザの拡張機能で文字コードを変換する手もある。
       * GitHubアプリでの文字化けはどうしようもない。
   * EUC-JPなファイルをUTF-8なターミナルを通してgitで扱う場合
       * `git config --global core.pager “nkf -w | LESSCHARSET=utf-8 less”`
       * http://hideack.hatenablog.com/entry/2013/05/16/233407


---

# 懸念

* GitHubからpushするより、220がGitHubからpullする方がセキュリティ的には安心？
