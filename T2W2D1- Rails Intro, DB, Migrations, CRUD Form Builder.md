# Term 2 Week2 Day1

* Rails Intro
* Routes
* Db
* Migration
* schema
* C.R of CRUD
* Form Builder.

---
##HTTP verbs.

* GET
* POST
* PATCH/PUT
* DELETE


create new rails app

```
rails new blog -d postgresql
```

-d : database

cd into directory.

```
git add .
git commit -m 'initial'
```

```
rails s
```

```
rails db:create
rails s
```

```
rails db:drop
```
to drop database


inside config/database.yml

```
#line 24
development:
 <<: *default
 database: blog_development <-- name of database (can change name).
 
 test:
 
 
 production:
 
```
database.yml is called when 
```
rails db:create is called
```

## Routes

cmd+p

###routes.rb

```
Rails.application.routes.draw do
	get 'articles', to: 'articles#index'
end
```

if we want to get articles, we go TO 'articles#index' articles_controller#method_index

```
tldr <--- help with command line
```

```
rails generate controller articles index
#rails generate controller name_of_controller method
```
create articles controller. <- PLURAL


### articles_controller.rb

```
class ArticlesController < ApplicationController
	def index <-- insert
	end <-- insert
end
```

create inside views/articles/

```
index.html.erb
```

erb -> embedded ruby.
