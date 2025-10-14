# Commands

Peak comes with an optional Paid addon containing a set of CLI commands to make tedious recurring tasks a lot easier. This addon requires an active license during development.

## Make Collection
This command creates a new collection and scaffolds out all needed files with some sane default markup containing the various Peak utilities we use.

Run `php please peak:make:collection` to:

* Create a collection in `content/collections/{handle}.yaml` with the variables you defined in the CLI.
* Create a blueprint for collection in `resources/blueprints/collections/pages/{handle}.yaml` containing the page builder fieldset and the SEO tab when your collection has a public route defined.
* Optionally create an index partial in `resources/views/{handle}/index.antlers.html` with default Peak markup.
* Optionally set the index template to the entry you chose to mount the collection on.
* Optionally create a show partial in `resources/views/{handle}/show.antlers.html` with default Peak markup.
* Optionally add permissions to the `editor` role in `resources/users/roles.yaml`.

## Make Page Builder Block
This command adds a block to the Peak Page Builder and generates the files needed.

Run `php please peak:make:block` to:

* Pick a group to add the block to.
* Add a set to the Page Builder replicator in `resources/fieldsets/page_builder.yaml`.
* Create a fieldset for your block in `resources/fieldsets/{filepath}/{filename}.yaml`.
* Create a partial with default markup and IDE hinting in `resources/views/page_builder/{filepath}/_{filename}.antlers.html`.

## Make Article (Bard) Set
This command adds a set to the Peak Page Builder Article (Bard) block and generates the files needed.

Run `php please peak:make:set` to:

* Pick a group to add the set to.
* Add a set to the Article Bard in `resources/fieldsets/article.yaml`.
* Create a fieldset for your set in `resources/fieldsets/{filepath}/{filename}.yaml`.
* Create a component partial with default markup and IDE hinting in `resources/views/components/{filepath}/_{filename}.antlers.html`.

## Make Partial
With this command you can choose a type (component, layout, snippet or typography) and add a name and description. It will generate a partial with the proper IDE hinting and location comments.

Run `php please peak:make:partial`.

## Make Global
With this command you can generate a global with a blueprint and optionally grant edit permissions to the editor.

Run `php please peak:make:global`.

## Make Taxonomy
With this command you can generate a taxonomy, term blueprint, attach it to multiple collections and optionally grant edit permissions to the editor.

Run `php please peak:make:taxonomy`.

## Make Nav
With this command you can generate a navigation, navigation blueprint, attach collections and optionally grant edit permissions to the editor.

Run `php please peak:make:nav`.

## Clear site
This command clears the default Peak content.

Run `php please peak:clear-site` to:

* Delete all assets from the default asset container.
* Delete all entries but `home`.
* Clear the pagebuilder for the homepage.
* Clear the social media globals.
* Clear caches.

## Install Page Builder Block
This command installs premade blocks to the Peak Page Builder and generates the files needed.

Run `php please peak:install:block` to pick a block and:

* Add a set to the Page Builder replicator in `resources/fieldsets/page_builder.yaml`.
* Create a fieldset for the installed block in `resources/fieldsets/{filename}.yaml`.
* Create a partial with bespoke markup in `resources/views/page_builder/_{filename}.antlers.html`.

These are the page builder blocks available:
* **Call to action**: Show a call to action.
* **Collection**: Show collection entries.
* **Columns**: Text columns with optional images and buttons.
* **Divider**: A visual divider between blocks.
* **Full width image**: A full width image with optional text and button(s).[full_width_image]
* **Index content**: Render the currently mounted entries if available.
* **Image and text**: An image and text side by side.
* **Images grid**: A multi row image grid.
* **Link blocks**: Blocks that link using the button fieldset.
* **Text columns**: Text wrapping in two columns.

## Install Preset
This command installs full presets into Peak. A preset can be anything. A collection that installs the relevant blueprints, templates, configuration, pages and page builder blocks into your site or a simple navigation pattern or dark mode.

Run `php please peak:install:preset` to pick a set.

These are the presets available:
* **Availability**: A global and availability component.
* **Banner**: A banner on top of your site users can click to hide.
* **Breadcrumbs**: A breadcrumbs partial.
* **Business hours**: A business hours global and a list and call component that shows the business hours and if the business is currently open / available.
* **Clients**: A routeless renamable client/partner collection with a logo cloud page builder block.
* **Default blocks**: Reusable page builder blocks that can be placed globally.
* **Events**: A dated events collection with index and show templates (including JSON-ld) and a page builder block.
* **FAQ**: A FAQ collection with a page builder block (including JSON-ld).
* **Footer**: A mega footer with multiple navs.
* **Hero**: A hero layout component.
* **Horizon**: Installs Laravel Horizon configured for Peak.
* **Image credits**: An asset blueprint and page builder block that lists images with credits.
* **Intranet**: Intranet with frontend users and email verification. Uses page builder blocks for account management and automatically excludes pages featuring those blocks from static caching. 
* **Language picker**: A language picker for when you use multisite.
* **Links**: A LinkTree type blueprint and template.
* **Lottie player**: A Lottie animation player.
* **Mega Menu**: A three level deep mega dropdown menu.
* **Modal**: A modal that only has to be rendered once but can be used multiple times with different content.
* **News**: A dated news collection with index and show templates (including JSON-ld) and a page builder block.
* **Password protection**: Protect pages with a password.
* **Pricing tiers & features**: Create and list prcicing tiers and a composable feature matrix.
* **Search**: A search form component and a styled search results template.
* **Secure downloads**: Offer secure downloads.
* **Team members**: A renamable team member collection with a page builder block.
* **Testimonials**: A renamable testimonial collection.
* **Theme toggle**: A theme toggle typically used for a Tailwind class based dark mode.
* **Vacancies**: A dated renamable vacancies collection with index and show templates (including JSON-ld).

## Install Set
This command installs premade sets to the Article (Bard) field and generates the files needed.

Run `php please peak:install:set` to pick a set and:

* Add a set to the Page Builder Article Bard field in `resources/fieldsets/article.yaml`.
* Create a fieldset for the installed set in `resources/fieldsets/{filename}.yaml`.
* Create a partial with bespoke markup in `resources/views/components/_{filename}.antlers.html`.

These are the page builder blocks available:
* **Read more**: Link to a related article.
* **Video self hosted**: Add a self hosted video.

## Extending
You can register your own custom (private) content for `blocks`, `sets` and `presets`. This way you can install internal content onto your sites.

### Knowledge requirements
Behind the scenes, the commands run a bunch of `operations`. The addon ships with the following built-in operations:

- `attach_collections_to_navigation`
- `attach_taxonomy_to_collections`
- `copy`
- `notify`
- `operation`
- `rename`
- `run`
- `update_article_sets`
- `update_page_builder`
- `update_role`

The built-in operations all live in the pre-registered `namespace` (`\Studio1902\PeakCommands\Operations`). In case you need more than the listed operations above, you can register your own namespace and build out your custom operations there.

When building your own operation, make sure to extend the `Studio1902\PeakCommands\Operations\Operation` class, which ensures your operation gets picked up correctly by the commands.

### Register custom content
To install your custom content, follow these steps:

1. Publish the config file by running: `php artisan vendor:publish --tag=statamic-peak-commands-config`.
2. Add paths to the arrays in the config file for either `blocks`, `sets` or `presets`.
3. Make sure each block, set or preset is contained within a folder and contains a `config.php` using the following pattern (note, you can specify `type` as snake-cased or fully qualified class name).

```php
return [
    'handle' => 'pricing',
    'name' => 'Pricing tiers & features',
    'description' => 'Create and list pricing tiers and feature tables.',
    'operations' => [
        // Adds the ability to rename a collection handle. Use `{{ handle }}` in your files.
        [
            'type' => 'rename',
        ],
        // Runs a custom CLI command.
        [
            'type' => 'run',
            'command' => 'composer require vendor/package',
            'processing_message' => 'Installing vendor/package',
            'success_message' => 'Package installed.'
        ],
        // Copy a file, optionally add the option to skip the operation.
        [
            'type' => 'copy',
            'input' => 'source.file',
            'output' => 'destination.file',
            'skippable' => false // Default.
        ],
        // Update the page builder with a new block.
        [
            'type' => 'update_page_builder',
            'block' => [
                'name' => 'Title',
                'instructions' => 'Instructions',
                'icon' => 'icon',
                'handle' => 'handle',
            ]
        ],
        // Update Bard with a new set.
        [
            'type' => 'update_article_sets',
            'block' => [
                'name' => 'Title',
                'instructions' => 'Instructions',
                'icon' => 'icon',
                'handle' => 'handle',
            ]
        ],
        // Add permissions to a role. Use `{{ handle }}` when working with a renamable collection.
        [
            'type' => 'update_role',
            'role' => 'role_handle',
            'permissions' => ['view {{ handle }} entries', 'edit {{ handle }} entries', 'create {{ handle }} entries', 'delete {{ handle }} entries', 'publish {{ handle }} entries', 'reorder {{ handle }} entries', 'edit other authors {{ handle }} entries', 'publish other authors {{ handle }} entries', 'delete other authors {{ handle }} entries']
        ],
        // Attach collections to navigation.
        [
            'type' => 'attach_collections_to_navigation',
            'navigation' => 'handle',
            'collections' => ['collection_handle_1', 'collection_handle_2']
        ],
        // Attach taxonomy to collections.
        [
            'type' => 'attach_taxonomy_to_collections',
            'taxonomy' => 'handle',
            'collections' => ['collection_handle_1', 'collection_handle_2']
        ],
        // Notify the user with a message in the CLI. The user has to hit enter to continue.
        [
            'type' => 'notify',
            'content' => "All done."
        ],
    ]
];
```

### Programmatic configuration
In some scenarios, publishing the addon config might feel wrong. For example, you want to build your own suite of custom blocks, presets and sets and want to distribute those via an internal addon. Additionally, you might need to ship some custom operations that are used in one of your presets. In that case you can configure the commands addon with the `Registry` facade.

The available methods are:
- `Registry::getPaths()`
- `Registry::addPresetsPath(string $path)`
- `Registry::addBlocksPath(string $path)`
- `Registry::addSetsPath(string $path)`
- `Registry::removePresetsPath(string $path)`
- `Registry::removeBlocksPath(string $path)`
- `Registry::removeSetsPath(string $path)`
- `Registry::getNamespaces()`
- `Registry::appendNamespace(string $namespace)`
- `Registry::prependNamespace(string $namespace)`
- `Registry::removeNamespace(string $namespace)`
- `Registry::resolveOperation(string $class, array $config)`

As an example, you add this to your addons `ServiceProvider`:
```php
use \Studio1902\PeakCommands\Facades\Registry;

public fuction bootAddon(){
    // Registers the namespace for your own operations
    Registry::prependNamespace('\Acme\YourAddon\Operations');

    // Registers a path for your own presets
    Registry::addPresetsPath(base_path('vendor/acme/your_addon/resources/presets'));
}
```
