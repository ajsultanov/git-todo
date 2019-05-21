# rails generators

###a rails project
technically not a generator<br>
creates:
- a whole lot of shit	
format:
- `rails new name-of-my-app`

```ruby
rails generate GENERATOR [args] [options]
```

to undo a generate command: rails destroy x...
to not generate new tests: add --no-test-framework



migration
=========
creates: 
	migration file
	new tests
format: 	
	rails [g]enerate migration
		add_x attribute(s):data_type
		remove_x attribute(s):data_type
		add_ ... _to_x attribute(s):data_type
		remove_ ... _from_x attribute(s):data_type
		change_ ... _to_x attribute(s):data_type



model
=====
creates: 	
	migration file
	model file
	new tests
format: 	
	rails [g]enerate model
		Class attribute(s):data_type
		Class association(s):association_type



controller
=======================================
best for things that do not have models
=======================================
creates: 	
	controller file
	adds routes in config/routes
	view template directory
	view template files for each controller action specified
	view helper file
	Coffeescript file
	scss file
	new tests for everything
format:	
	rails [g]enerate controller
		name controller_action(s)



resource
========
creates:
	migration file
	model file
	resources call in config/routes
	controller file
	view template directory
	view helper file
	Coffeescript file
	scss file
	new tests for everything
format:
	rails [g]enerate resource
		Class attribute(s):data_type



scaffold
====================
seems pretty bloated
====================
creates:
	a huge amount of shit
	migration file
	model file
	resources call in config/routes
	controller file
	helper file
	view template directory
	view template files for each controller action specified
	json builder view files?
	Coffeescript file
	scss file	
	new tests for everything
format:
	rails [g]enerate scaffold
		Class attribute(s):data_type








