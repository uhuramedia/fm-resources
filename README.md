Resources is a thin CMS app for Django.

Its main thing is a `Resource` class that inherits from `MPTTModel` and is thus
placed within a tree. It contains the main meta information that make a resource
like title, slug, creation dates and so on.

The next important class is `Page`. This is also a `Resource` and has additional
fields like text and meta summary. Every page can have a different template, which
is defined as string but can also be made as a ChoiceField by using the 
`RESOURCES_TEMPLATES` setting, that defines a list of `(template_path, template_name)`
tuples.

To use resources in your project, add it to INSTALLED_APPS and add the URL

    (r'^', include('resources.urls')),

This catches all URLs, parses them for slugs and tries to find the appropriate
page in the tree. The page is then rendered using the specific template.

Resources is a quick and simple way to have a tree of resources with configurable
templates, and have these rendered in the templates easily. If you have a use case
like that, you don't need to write models, views and admin classes. Just use
resources.