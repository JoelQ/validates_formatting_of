F# validates_formatting_of [![Build Status](https://secure.travis-ci.org/mattdbridges/validates_formatting_of.png)](http://travis-ci.org/mattdbridges/validates_formatting_of)

The `validates_formatting_of` gem adds several convenient methods to validate things such as emails, urls, and phone numbers in a Rails application.

# Installation

To install `validates_formatting_of`, add the following to your `Gemfile`:

    gem 'validates_formatting_of'

Then bundle install:

    bundle install

# Usage

Using validates_formatting_of is as simple as using Rails' built-in validation methods in models.

    class User < ActiveRecord::Base
      validates_formatting_of :email, :using => :email
    end

This call will ensure that the user-provided email is a valid email. This way, you will not need to find or write your own regex to validate. All of that logic is contained within `validates_formatting_of`

# Rails validation options still available

You can still add the following options when using `validates_formatting_of`:

* `:allow_nil`
* `:allow_blank`
* `:message` for custom validation messages

# Available Formatting Validations

`validates_formatting_of` has support for the following validations:

### Email

    class User < ActiveRecord::Base
      validates_formatting_of :email, :using => :email
    end

A valid email consists of at least one alphanumeric or special character (!#$%^&*-_=+`~|), followed by an @ symbol, followed by at least one alphanumeric character or the - symbol, followed by a period (.) followed by two to four alphabetic characters. All characters are case-insensitive.
    
#### Examples

    person@example.net  #=> valid
    name-5@abc.co       #=> valid

### URL

    class Sites < ActiveRecord::Base
      validates_formatting_of :website, :using => :url
    end

### Alpha

    class Name < ActiveRecord::Base
      validates_formatting_of :first_name, :using => :alpha
    end

### Alphanumeric

    class Sites < ActiveRecord::Base
      validates_formatting_of :text, :using => :alphanum
    end

### Credit Card (Visa, Mastercard, Discover, and American Express)

    class Purchases < ActiveRecord::Base
      validates_formatting_of :cc, :using => :credit_card
    end
    
### US Zipcodes

    class Location < ActiveRecord::Base
      validates_formatting_of :zipcode, :using => :us_zip
    end
    
### US Phone numbers

    class Phones < ActiveRecord::Base
      validates_formatting_of :phone, :using => :us_phone
    end
    
### IP Address

    class Location < ActiveRecord::Base
      validates_formatting_of :website, :using => :ip_address
    end
### Social Security Number

    class User < ActiveRecord::Base
      validates_formatting_of :ssn, :using => :ssn
    end 
    
### Hex Colors

    class Color < ActiveRecord::Base
      validates_formatting_of :color, :using => :hex_color
    end

### Dollar Amount

    class Invoice < ActiveRecord::Base
      validates_formatting_of :amount, :using => :dollars
    end

# Customizable

If, for any reason, you want to use your own regex instead of Rail's built-in methods, you can specify what you want to use with the `:regex` option. For example,


    class Person < ActiveRecord::Base
      validates_formatting_of :first_name, :regex => /[A-Z]/i
    end

# Development and Contribution

It is very easy to contribute to this gem. Full documentation to do so will be added in the near future.

# Have Ideas?

Do you use a particular pattern on a regular basis that isn't here or you would like to contribute? For now, [create a new issue](https://github.com/mattdbridges/validates_formatting_of/issues/new) in the issue tracker. I would be more than happy to consider adding it to the project.
    