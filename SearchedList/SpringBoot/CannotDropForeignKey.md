### JPAが生成する外部キーを自動で削除できない
JPAでEntity間のリレーションを定義して、再ビルドすると以下のようなエラーが発生することがある

```
ERROR : HHH000389: Unsuccessful: alter table xxxxx_table drop foreign key xxxxxxx_foreign_key
ERROR : Can't DROP 'xxxxxxx_foreign_key'; check that column/key exists
```

[こちら](https://stackoverflow.com/questions/36766848/how-does-hibernate-generate-foreign-key-constraint-names/36767157#36767157)にある通り、JPAはテーブル名とプロパティ名をMD5でハッシュ化して生成している
どちらかの情報が変わってしまうと、以前生成した外部キーと食い違ってしまい削除できないと思われる