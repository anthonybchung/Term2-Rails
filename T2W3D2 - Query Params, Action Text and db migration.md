# T2W3D2 - Query Params, Action Text and db migration

## Query params

passing parameters using URL.

```
params
=> #<ActionController::Parameters {"controller"=>"articles", 
	"action"=>"show", 
	"id"=>"2"
	} permitted: false>
```

```
localhost:3000/articles/2?count=45
params
=> #<ActionController::Parameters {"count"=> 45, "controller"=>"articles ...}
```


controller
```
def show
	@article = Article.find(params[:id])
	
	@toast = params[:toast]

end
```

show.html.erb

```
<h2> <%= @toast %> </h2>
```

#### undo git commit

```
git add filename

git checkout .
git status

git restore --staged filename
```

inside views/articles/

#### edit.html.erb and new.html.erb

#### partials

create a new file

```
_form.html.erb
```

inside edit.html.erb or new.html.erb

```
<%= render "form", article: @article %> <---- going to use @article for article:
```

#### Got to home link

partial for navbar

_nav.html.erb

```
<p> <%= link_to_unless_current "Go to Home", home_path %> </p>
```

show.html.erb

```
 <%= render "shared/nav" %>
```

## new rails app

```
rails new pretty-blog -d postgresql
```

#### Trix-editor.org

```
rails generate scaffold Post title:string body:text
```

### Actiontext

```
rails action_storage:install
rails action_text:install
rails db:migrate
```

add images

gemfile

uncomment line 26

```
 gem 'image_processing', '~> 1.2'
```

```
bundle install
```

inside view

models

```
class Post <
	has_rich_text :body
end
```






