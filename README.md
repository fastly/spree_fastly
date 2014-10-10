Spree Fastly
===========

Built with the wisdom that performant eCommerce stores generate more
revenue, this extension integrates Spree store installations with
Fastly's advanced edge-caching technologies. Cache invalidation is
performed by means of observing models and expiry via surrogate keys.

Integration
-----------

This extension does the following:

   1. Instruments the customer-facing parts of spree_frontend with
      correct cache headers
   1. Observers changes to key Spree models (and relations) for cache invalidation

As a consequence, you can expect to lower HTTP response times
drastically. Additionally, since the majority of requests are expected
to short-circuit at edge locations, the carrying capacity of your
hosting tier is effectively boosted.

Optimized Resources
-------------------

The following frontend controllers are optimised with cache-control
headers:

   * Spree::ContentController
   * Spree::HomeController
   * Spree::ProductsController
   * Spree::TaxonsController

Additionally, the following Spree API resources receive a boost:

   * Spree::ProductsController
   * Spree::TaxonomiesController
   * Spree::TaxonsController

Special Considerations
----------------------

Due to template and asset changes upon **deployment** it is wise to
invalidate the cached views in bulk.

TODO: Expand this section.

Installation
------------

Add spree_fastly to your Gemfile:

```ruby
gem 'spree_fastly'
```

Bundle your dependencies and run the installation generator:

```shell
bundle
bundle exec rails g spree_fastly:install
```

Testing
-------

First bundle your dependencies, then run `rake`. `rake` will default to building the dummy app if it does not exist, then it will run specs. The dummy app can be regenerated by using `rake test_app`.

```shell
bundle
bundle exec rake
```

When testing your applications integration with this extension you may use it's factories.
Simply add this require statement to your spec_helper:

```ruby
require 'spree_fastly/factories'
```

Copyright (c) 2014 Fastly, released under the New BSD License
