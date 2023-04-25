# Configuration changes

Peak changes the default Statamic config. The following is different:

| File | Default | Peak |
| --- | --- | --- |
| `.env.example` |  | Add more default Statamic and Redis settings by default.
| `app/Console/Kernel.php` |  | Add a schedule you can invoke via a cron to warm all caches.
| `app/providers/AppServiceProvider.php` |  | Link to the Peak SEO addon when a 404 hits.
| `config/filesystems.php` |  | Filesystems for the Images, Files, Favicon and Social Images asset containers. |
| `config/ignition.php` | `'editor' => env('IGNITION_EDITOR', 'phpstorm')` | `'editor' => env('IGNITION_EDITOR', 'vscode')` |
| `config/ignition.php` | `'theme' => env('IGNITION_THEME', 'light')` | `'theme' => env('IGNITION_THEME', 'auto')` |
| `config/statamic/assets.php` | `driver' => 'gd'` | `'driver' => env('IMAGE_MANIPULATION_DRIVER', 'gd')` |
| `config/statamic/assets.php` | `'cache' => false` | `'cache' => env('SAVE_CACHED_IMAGES', true),` |
| `config/statamic/assets.php` |  | Add a default replacement preset. |
| `config/statamic/cp.php` | A getting started widget | Add alt text and page collection widgets. |
| `config/statamic/cp.php` | `'link_to_docs' => true` | `'link_to_docs' => false` |
| `config/statamic/editions.php` | `'pro' -> false` | `'pro' -> true` |
| `config/statamic/git.php` |  | Add `[BOT]` to git commit message. |
| `config/statamic/git.php` |  | Add `favicons` and `social_images` paths to Git tracking. |
| `config/statamic/live_preview.php` | Three breakpoints | All tailwinds breakpoints defined in `tailwind.config.js` |
| `config/statamic/search.php` | `title` in search index | `title`, and `page_builder` in search index |
| `config/statamic/stache.php` | `'watcher' => true` | `'watcher' => env('STATAMIC_STACHE_WATCHER', true)` |
| `config/statamic/static_caching.php` | `'rules' => [ // ]` | `'rules' => 'all'` |
| `config/statamic/static_caching.php` | `'exclude' => [ // ]` | `'exclude' => '/sitemap.xml'` |
| `config/statamic/users.php` | `'avatars' => 'initials'` | `'avatars' => 'gravatar'` |
