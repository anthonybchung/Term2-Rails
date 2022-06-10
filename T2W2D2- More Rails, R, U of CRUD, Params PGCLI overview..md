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
time 33:43