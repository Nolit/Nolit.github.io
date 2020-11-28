### SpringBootでテーブル名の命名規則をキャメルケースに変更する
Version: SpringBoot 2.3.1

JPAもしくはHibernateではクラスからテーブル名を生成する際の命名規則を変更できる
Implicit Naming Strategyでクラス名や@Tableアノテーションから論理名を決める(Implicit Naming Strategy)
論理名から実際のテーブル名を決める(Physical Naming Strategy)
どちらもデフォルトの戦略を変更することができる
命名規則に関しては**Physical Naming Strategy**で対応できる

application.propertiesに以下を追記して対応
```
spring.jpa.hibernate.naming.physical-strategy=org.hibernate.boot.model.naming.PhysicalNamingStrategyStandardImpl
```