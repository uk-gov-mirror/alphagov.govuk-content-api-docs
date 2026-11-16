---
title: Retrieve and display GOV.UK content
description: Learn how to retrieve a piece of GOV.UK content and embed it in your HTML.
type: tutorial
audience: developer
product: content-api
weight: 40
---

# Retrieve and display GOV.UK content

This guide takes you through a complete example of getting a piece of content
from GOV.UK and adding it to your application or service.

You can use this guide if you are a developer working with Ruby, Python or
JavaScript.

## Before you start

Make sure you have:

- a code editor or IDE.
- a local development environment for your chosen programming language.
- an HTTP client library capable of making GET requests and parsing JSON
  (for example, the `requests` library for Python).
- a command line where you can run your code.

You should also complete the [Get started][get-started] guide, and have an
understanding of [How the GOV.UK Content API works][how-it-works] before you start.

## Retrieve and display a piece of content

In this section, you will learn how to:

- retrieve a piece of content using the GOV.UK Content API
- extract the content body from the API response
- cache the HTML from the content body
- add the HTML to a page in your application

### 1. Retrieve a piece of content from the API

TBC

### 2. Extract the content body from the response

TBC

### 3. Cache the HTML

TBC

### 4. Display the HTML in a web page

TBC

The example below illustrates utilising [Ruby on Rails](http://rubyonrails.org/)
with [Rest Client](https://github.com/rest-client/rest-client) to make use of
GOV.UK in your application.

<!-- markdownlint-disable MD013 -->
```ruby
require "rest-client"

tax_help = Rails.cache.fetch("govuk/tax-help", expires_in: 1.hour) do
  response = RestClient.get("https://www.gov.uk/api/content/tax-help", { content_type: "json" })
  JSON.parse(response.body).dig("details", "body")
end

content = "<h1>GOV.UK Tax Help</h1><div>#{tax_help}</div>"
```
<!-- markdownlint-enable MD013 -->

In this example we utilise the Rails cache layer so that we can infrequently
access the content without concerns of hitting the
[rate limit][rate-limiting].

We then use the API to access the content for
[Tax Help](https://www.gov.uk/tax-help). In the response we access the `body`
field from within the `details` object. We store this to a variable `tax_help`.

Finally we embed this in our own HTML and are ready to output to users.

## Summary

In this guide, you learned how to...

## Next steps

[rate-limiting]: /reference.html#rate-limiting
[get-started]: /get-started.html
[how-it-works]: /how-it-works.html
