# T2W5D1: Heroku, Seedings, Faker.

## Heroku Account.

```
heroku login
```

bring up heroku dashboard.

terminal: 

create heroku app.

```
heroku create
```

it will take you to the app in the browser.

```
heroku open
```

pushing to github.

```
git push origin main
```

```
git remote
```

will give what we have for bridge.

```
git push heroku main
```

#### we're sorry something went wrong.

```
heroku logs --tail
```
press cmd-k to clear screen.

press refresh on browser.

check report.

```
git diff
git add .
git commit -m "remove 'console' "
git push
git push heroku main
```

```
... Error(PG::UndefinedTable: ERROR:)
```
have not setup database on heroku.

```
heroku run rails db:create
heroku run rails db:migrate
```

database.yml

production: database, heroku will handle it for us.


# rails db:seed
db folder have seeds.rb

```rails
articles = Article.create([
		{
		title: 'Star Wars',
		body: 'jfklasjfklasjfklasd flasjfkl;asdf',
		importance: 5
		},
		{
		title: 'Lord of the Rings',
		body: 'fjaklfaskl;fsajk afadksljfadls;',
		importance: 6
		}
])
```

to populate the database.

```
rails db:seed
```

if we rerun it will populate again.



```
10.times do |i|
	articles = Article.create([
		{
			title: "This is title #{i}",
			body: 'hello world',
			importance: rand(1..10) 
		}
	])
end
```
```
rails db:seed
```

##Faker

```
bundle add faker
```

go into github Faker and copy the following:

```
Faker::Quotes::Shakespeare.as_you_like_it_quote
```
paste into the seed.rb


```
10.times do |i|
	articles = Article.create([
		{
			title: "This is title #{i}",
			body: Faker::Quotes::Shakespeare.as_you_like_it_quote,
			importance: rand(1..10) 
		}
	])
end
```

```
rails db:seed
```

# move up and down the list.

inside show.html.erb

```rails
<%= link_to_unless_current "Go to next article", @article.next %> 
<%= link_to_unless_current "Go to previous article", @article.previous %>
```

article.rb (model)
```
def next
	Article.where("id> :id", id).first
end

def previous
	Article.where("id< :id",id).last
end
```

# action_text

```
rails active_storage:install && rails action_text:install
```

it gave us 2 files.

1. active storage
2. action text

uncomment line 26 in gemFile.

```
gem 'image_processing', '~> 1.2'
```

```
bundle install
```

go into views. and article model.

```
class Article < ApllicationRecord
	has_many :comments
	has_rich_text :body <---- insert this
end

```

views

```
<%= form.label :body %>
<%= form.rich_text_area :body %> 	<---- change from text_area
```




