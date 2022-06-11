#Active Storage - Image Uploads.

```
rails g scaffold pin title

rails active_storage:install <- to generate migration

rails db:migrate <- migrate to database

rails g action_text:install <- to take a look at action text

rails db:migrate

rails s
```

inside gemfile

```
line 50

gem "image_processing", "~> 1.2" <-- uncomment
```

Gemfile.lock

if you want to switch to mini_magick

/config/environments/development.rb

```
config.active_storage.variant_processor = :mini_magick
```

to use image_magick

```
sudo apt install imagemagick
```

to use vips


```
sudo apt install libvips
```

the 2 above will allow to resize images.

create the ability to upload images.

model/Pin

```
class Pin < ApplicationRecord
	has_one_attached :image 
	has_many_attached :pictures
	has_rich_text :body
end
```

inside controller


```
private
	def pin_params
		params.require(:pin).permit(:title, :body, :image, pictures: [])
	end
```

form

```


```

```
<%= image_tag(pin.image) %>
```


active storage. 
can resize the image.

```
pin.image_as_thumbnail
```

```
def image_as_thumbnail
	image.variant(resize_to
end
```
