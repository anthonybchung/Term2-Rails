# T2W3D1 - Git, DSL, Documentation dicussion, Views, partials, Yield.

```
git add remote upstream
```

inside view layouts
application.html.erb


```
<!DOCTYPE html>
...
<%= stylesheet_link_tag 'application', media <- inside stylesheets/application.css
...

<body>
	<%= yield %>   <--- every html.erb page is injected here.
</body>
```

rename

### application.css to application.scss

inside application.scss

```
/****

*= require_tree .   <- require all file within the directory or sub directory.
*= require_self   <- requiring itself
*/

h1{
 color: red;
 font-family: sans-serifs;
}
```

inside application layout.

```
<head>
	<link rel="stylesheet" href="https://cdn.simplecss.org/simeple.min.css">
</head>
```


show.html.erb

```
<%= link_to "Go Home", home_path %>
<%= link_to "Edit this article", edit_article_path %>

```

routes.rb

```
root 'articles#index', as: "home" <-- provide an aliase.
```

inside index.html.erb

```
<% @article.each do |article| %>
 <li> <%= link_to article.title,  article_path(article.id) %> </li>
<% end %>
```

rails docs

api.rubyonrails.org

1:59






