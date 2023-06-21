# Redis Queue

To enable Redis as a queue driver make sure it's installed on your server. When you use Ploi or Forge this is done automatically.

Enable Redis by setting `QUEUE_CONNECTION=redis` in your `.env` file. By default Redis ships with 16 databases (0-15). Each site on your server should get it's own unique database number. Use the environment property `REDIS_DATABASE` for this.

Make sure you start a queue worker in Ploi or Forge for your current site. Got to the `Queue` tab for your site. Set `redis` as a connection instead of `database` and set the current `environment` to whatever your environment currently is: `staging` or `production` probably. Click `Add Queue` to start your worker.

Include `php artisan queue:restart` in your deploy script.
