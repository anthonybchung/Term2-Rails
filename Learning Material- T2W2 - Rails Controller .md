#Learning Material T2W2- Rails Controller

Agenda

- Create controllers
- Controller connection to routes
- Defining a controller action
- Render
- Params

## Rails Controller - Index

```
rails new projects_management_app

cd projects_management_app

rails server
```

first thing is to create a single app.

inside routes.rb

```
get "/projects", to: "projects#index". <---- controller#action"
```

create projects controller

```
rails generate controller projects
```

inside projects controller

```
def index
#send back all of the resources to the cliend.
# i.e send back of all the projects.

	projects = [
		{
			id: 1,
			name: "rails project",
			github_status: false
		},
		{
			id: 2,
			name: "terminal app",
			github_status: false
		}
	]
	
	render json: { projects: projects } <-- key-value hash
	
#can just send back array of hashes
	render json: projects
end
```

## Rails Controllers - Show

Send back one project at a time.
Define a new route in routes.rb

```
#localhost:3000/projects/1
	get "/projects/:id", to: "projects#show"
```

inside controller

```
def show
# send 1 resource.

	projects = [
		{
			id: 1,
			name: "rails project",
			github_status: false
		},
		{
			id: 2,
			name: "terminal app",
			github_status: false
		}
	]

	found_project = projects.find do |project|
		project[:id] ==  params[:id].to_i <--- :id in params correlates to routes :id. if named :elephant in routes, here should be :elephant as well.
	end

	render json: found_project
end
```

## Rails Controllers - Using Files and Before Action

- Refactor
- Read data from a file
- before_action

inside directory public create projects.json

we can't use ruby symbols in json files.

```
{
	"id": 1,
	"name": "rails project",
	"github_status": false
},
{
	"id": 2,
	"name": "terminal app",
	"github_status": false
}
```

inside project controller

use file class and json class

```
before_action :read_projects <-- hook to a symbol.

def index
	render json: @projects
end

def show
	found_project = @projects.find do |project|
		project["id"] == params[:id].to_i <--- now working with string not symbol
	end
	
	render json: found_project
end

def read_projects <--- responsible for reading json file.
	@projects = JSON.parse(File.read(Rails.public_path.join("projects.json"))
end
```

## Rails Controller - Create

- create action
- POST request
- Postman
- CSRF

inside routes.rb

```
post "/projects", to: "projects#create"
```
 
 use Postman to create POST request.
 
```
http://locahost:3000/projects
```

controller

```
	skip_before_action :verify_authenticityj_token
	
	def create
		
	end
```

## Rails Controller - Query String

- Query string
- Create a new project
- Write to our JSON file 
- redirect_to
- private modifier

### Query String
Postman
POST: http://localhost:3000/projects?id=3&name=portfolio app&github_status=true

```
def create
	new_project = {id: params[:id].to_i, name: params[:name], github_status: params[:github_status].to_b}
	@projects << new_project
	write_projects(@projects)
	render plain: "successfully created"
end

private
def write_projects(projects)
	File.write(Rails.public_path.join("projects.json"),JSON.generate(projects))
end	

```

## Rails Controller - Redirect To

### redirect_to
```
def create
	new_project = {
					id: params[:id].to_i, 
					name: params[:name], 
					github_status: params[:github_status].to_b
					}
	@projects << new_project
	write_projects(@projects)
	redirect_to projects_path <---- prefix_path
end

```



