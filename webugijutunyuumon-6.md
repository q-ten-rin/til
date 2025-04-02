###Webセキュリティ
・SQLインジェクションについて
例　SELECT * FROM users WHERE username = '入力されるユーザー名' AND password = '入力されるパスワード';
この時入力されるユーザー名にadmin' --と入力すると
SELECT * FROM users WHERE username = 'admin' -- ' AND password = '';
となり、--以降の文は無効になるのでログインできてしまう
また、入力されるユーザー名に' OR '1'='1と入力すると
SELECT * FROM users WHERE username = '' OR '1'='1' AND password = '';
となり、'1'='1'は真なのでこのクエリは全てのユーザー情報を取得することが可能となってしまう

 ###対策
 ・SQL文を生成する際にユーザーからの入力を適切にエスケープする
 ・ORMを使用して、SQLを直接書かずにデータベースを操作する
