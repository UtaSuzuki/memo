# Django

## 目次

- [チュートリアル](#tutor)
- [migrate](#migrate)

## <a id="tutor"></a> チュートリアル

### 参考

- [Django Girls のチュートリアル](https://tutorial.djangogirls.org/ja)
- Qiita: [Djangoチュートリアル - 汎用業務Webアプリを最速で作る](https://qiita.com/okoppe8/items/54eb105c9c94c0960f14)

## <a id="migrate"></a> migrate

- migrate 状況確認
```sh
$ python manage.py showmigrations
```
- migrate 実行
```sh
$ python manage.py migrate
```
- 項目ごとに migrate  
項目: admin, auth, contenttypes, sessions
```sh
$ python manage.py migrate 項目
```
