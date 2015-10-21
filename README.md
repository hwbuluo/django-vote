# django-vote
A simple API for vote any model,fork from [Beeblio/django-vote](https://github.com/Beeblio/django-vote). It includes needed migration for django 1.7,and change test to py.test.



## Quick start

* Install ``django-vote`` by pip::
```
pip install git+ssh://git@github.com/hwbuluo/django-vote.git
```
* Add vote to your INSTALLED_APPS setting like this:

```python
    INSTALLED_APPS = (
    ...
    'vote',
    )
```
* Run 
```python 
python manage.py migrate
``` 
to create the vote models.
* Declare vote field to the model you want to vote:
```python

    from vote.managers import VotableManager

    class ArticleReview(models.Model):
        ...
        votes = VotableManager()
```
* Use vote API::
```python
    >>> review = ArticleReview.objects.get(pk=1)
    >>> review.votes.up(user)
    >>> review.votes.down(user)
```

## API

### Adds a new vote to the object
```python
up(user)
```
### Removes vote to the object
```python
down(user)
```
### Check if the user already voted the object
```python
exists(user)
```

### Returns the number of votes for the object
```python
count()
```

### Returns a list of users who voted and their voting date
```python
users()
```

### add extra info to original queryset
```python
filter()
```

## 运行测试(Run tests)

You can test the app:

1. setup a virtualenv,and activate it.
``
virtualenv --distribute venv & source venv/bin/activate
``
2. install the dependency
``
pip install -r test-requirements.py
``
3. test it use py.test
``
py.test vote/tests.py
``

## About Contribution 

贡献代码指南

我们非常欢迎大家来贡献代码，我们会向贡献者致以最诚挚的敬意,让我们一起创造出好用的开源云消息接入服务产品。

一般可以通过在Github上提交[Pull Request](https://github.com/hwbuluo/django-vote)来贡献代码。

## Pull Request要求

- **代码规范** 遵从pep8，pythonic。

- **代码格式** 提交前 请按 pep8 进行格式化。

- **必须添加测试！** - 如果没有测试，那么提交的补丁是不会通过的。

- **创建feature分支** - 最好不要从你的master分支提交 pull request。

- **一个feature提交一个pull请求** - 如果你的代码变更了多个操作，那就提交多个pull请求吧。

- **清晰的commit历史** - 保证你的pull请求的每次commit操作都是有意义的。如果你开发中需要执行多次的即时commit操作，那么请把它们放到一起再提交pull请求。

## 运行测试(Run tests)

You can test the app:

1. setup a virtualenv,and activate it.
``
virtualenv --distribute venv & source venv/bin/activate
``
2. install the dependency
``
pip install -r test-requirements.py
``
3. test it use py.test
``
py.test sms/tests.py
``
