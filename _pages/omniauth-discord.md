---
layout: default
title: Discord OAuth2 Strategy for OmniAuth
permalink: omniauth-discord.html
---

# OmniAuth Discord [![GitHub stars](https://img.shields.io/github/stars/adaoraul/omniauth-discord.svg?style=social&label=Star&maxAge=2592000)](https://github.com/adaoraul/omniauth-discord)

Discord OAuth2 Strategy for OmniAuth.

Read the Discord API documentation for more details: https://discordapp.com/developers/docs/topics/oauth2

## Installing

Add to your `Gemfile`:

```ruby
gem 'omniauth-discord'
```

Then `bundle install`.

## Usage

`OmniAuth::Strategies::Discord` is simply a Rack middleware. Read the OmniAuth docs for detailed instructions: https://github.com/intridea/omniauth.

Here's a quick example, adding the middleware to a Rails app in `config/initializers/omniauth.rb`:

```ruby
Rails.application.config.middleware.use OmniAuth::Builder do
  provider :discord, ENV['DISCORD_APPID'], ENV['DISCORD_SECRET']
end
```

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/adaoraul/omniauth-discord.


## License

The gem is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).
