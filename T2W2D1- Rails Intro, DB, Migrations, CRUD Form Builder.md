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

```
<h1>toast!</h1>
<%= @time %>
```

inside controller

```
def index
	@time = Time.now
end
```

## Do something with data.
## Generate a model.

```
rails generate model Article title:string body:text importance:integer
```

undo rails generate model

```
rails d model Article title:string body:text importance:integer
```

file /db/migrate.... time_stamp_create_articles.rb a file to change something in the database.

go into database

```
psql
\l <- list database
\c <- change database
\dt <- display tables.
```

run migration
```
rails db:migration
```

we can modify file in /db/migrate/time_stamp_create_articles.rb

```
schema.rb
```
dont change file directly, use db:migrate

```
rails console
or
rails c
```

```
Article.all
#create a new Article

article = Article.new(title: "Hey there", body: "Isn't this a nice article', importance: 5);

article.save
```

inside articles_controller.rb

```
def index
	@articles = Article.all
end
```

inside index.html.erb

```
<ul>
	<% articles.each do article %>
		<li> <%= article.title %> </li>
	<% end %>
</ul>
```

better than psql because it places you straight into the database the app is linked to.

```
rails db
```

### Create new article

routes.

```
get 'article/new, to: 'articles#new'
```

controller.

```
#new method: 
def new
	@article = Article.new
	
end

def create
	@article = Article.new(title: "This is a great lesson", body: "breakfast meal", importance: 5)
	@article.save
end
```

views: new.html.erb

```
<h1> New Article </h1>

<%= form_with model: @article do |form| %>
	<div>
		<%= form.label :title %>
		<%= form.text_field :title %>
	</div>
	
	<div>
		<%= form.label :body %>
		<%= form.text_area :body %>
	</div>
	
	<div>
		<%= form.label :importance %>
		<%= form.number_field :importance %>
	</div>
	
	<div>
		<%= form.submit %>
	</div>
<% end %>
```

all the routes we need

```
resources :articles

```

controller

```
def create
	@article = Article.new(title: "hello", body: "body is good", importance: 5
	if @article.save
		redirect_to @articles_path
	else
		render :new
	end

end
```

inside controller

```
	def index
		console
	end
```

inside console

```
params
```

inside controller

```
def create
	@article = Article.new(article_params)
	
	if @article.save
		redirect_to articles_parth
	else
		render :new
	end
end

private

def article_params
	params.require(:article).permit(:title,:body,:importance)
end
```







