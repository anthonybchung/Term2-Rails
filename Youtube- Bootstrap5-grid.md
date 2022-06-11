# Bootstrap - grid system

docs/grid

- 12 columns


get started/ introduction

starter template

boot5 grid system uses flex box

```
<div class = "container">
	<div class = "row">
		<div class = "col" style = "border: 1px solid red;">
			Column
		</div>
		<div class = "col" style = "border: 1px solid red;">
			Column
		</div>
		<div class = "col" style = "border: 1px solid red;">
			Column
		</div>
	</div>
</div
```

col-4 means use 4 columns of the 12 columns.

```
<div class = "container">
	<div class = "row">
		<div class = "col-sm-3" style = "border: 1px solid red;">
			Column
		</div>
		<div class = "col-lg-9" style = "border: 1px solid red;">
			Column
		</div>
	</div>
</div>

```

auto: variable width

```
<div class = "container">
	<div class = "row">
		<div class = "col-sm-auto" style = "border: 1px solid red;">
			Column
		</div>
		<div class = "col-lg-auto" style = "border: 1px solid red;">
			Column
		</div>
	</div>
</div>

```

center it, add extra class to row container
md means md-viewport only.
to have it on different view port, remove md

```
<div class = "container">
	<div class = "row justify-contrent-md-center">
		<div class = "col-sm-auto" style = "border: 1px solid red;">
			Column
		</div>
		<div class = "col-lg-auto" style = "border: 1px solid red;">
			Column
		</div>
	</div>
</div>

```

at sm-viewport 6 columns
at md-viewport 4 columns

```
<div class = "container">
	<div class = "row justify-contrent-md-center">
		<div class = "col-sm-6 col-md-4"  style = "border: 1px solid red;">
			Column
		</div>
		<div class = "col-sm-6 col-md-4" style = "border: 1px solid red;">
			Column
		</div>
	</div>
</div>

```

maximum of 2 columns in the row.


```
<div class = "container">
	<div class = "row rol-cols-sm-2 rol-cols-md-4">
		<div class = "col"  style = "border: 1px solid blue;">
			Column
		</div>
		<div class = "col" style = "border: 1px solid blue;">
			Column
		</div>
		<div class = "col" style = "border: 1px solid blue;">
			Column
		</div>
	</div>
</div>

```



```
<div class = "container">
	<div class = "row rol-cols-sm-2 rol-cols-md-4">
		<div class = "col"  style = "border: 1px solid blue;">
			Column
		</div>
		<div class = "col" style = "border: 1px solid blue;">
			Column
		</div>
	</div>
</div>







