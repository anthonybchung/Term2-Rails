# T2W2D2: More Rails, R, U of CRUD, Params PGCLI overview.

article controller

```
def show
	@article = Article.find(params[:id])
	
end
```

an error will occur if no id is found. so put a safety net.


```
Article.find(1).class
```

view: show.html.erb

```
<h1> <%= @article.title %> </h1>
<p> <%= @article.body %> </p>
<p> <%= @article.importance %> </p>
```

###Update.

edit_ _article_ _path

add action

```
def edit
	@article = Article.find(params[:id])
end

def update
	@article = Article.find(params[:id])
	
	if @article.update(article_params)
		redirect_to articles_path
	else
		render :edit
	end
end
```

view: edit.html.erb

```
<h1> Edit Article </h1>

<%= form_with model: @article do |form| %>

<% end %>
```

### pgcli
