# Youtube- Image Uploads With Rails and Active Storage- Jesus Castello



```
rails active_storage:install
```

- create a file in db/migrate
- allow you to store information of your file.


```
rails db:migrate
```

- runs the migration


#### inside cat.rb model

```
class Cat < ApplicationRecord
	has_one_attached :image <-- pass a symbol to refer to the attached
end
```

#### form view

```
<%= if cat.image.attached? %>
	<%= image_tag cat.image, style: "width: 200px; display: block" %>
<% end %>

<%= form.label :image %>
<%= form.file_field :image, class: "form-control" %>
```