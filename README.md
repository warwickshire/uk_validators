# UK Validators

This library contains Rails 3 custom validators for the following UK-centric data:

 * National Insurance Number
 * Post Code


## Installation

Add this line to your application's Gemfile:

    gem 'uk_validators'

And then execute:

    $ bundle install


## National Insurance Number (Nino)
Validates the format of a UK National Insurance Number.

References: [HMRC](http://www.hmrc.gov.uk/manuals/nimmanual/nim39110.htm), [uk-osint.net](http://www.uk-osint.net/usefulbits.html#Understanding%20UK%20National%20Insurance%20Numbers), [Wikipedia](http://en.wikipedia.org/wiki/National_Insurance_number)

### Usage

```ruby
class User < ActiveRecord::Base
  validates :ni_number, nino: true
end
```

### I18n

The default error message is `is not a valid National Insurance No.`

This can be translated in the same was as any other Rails valiation message using the key **:nino**.

For the example User model above, the customised en.yml would be:

    en:
      activerecord:
        errors:
          models:
            user:
              attributes:
                ni_number:
                  nino: "is not valid"



## Post Code

Validates the format of a UK postal code. This does not check whether the post code actually exists as this would require a lookup against approx. 1.8 million postal codes.

References: [Royal Mail PAF Document](http://www.poweredbypaf.com/wp-content/themes/amu/paf_downloads/programmers_guide.pdf), [Wikipedia](http://en.wikipedia.org/wiki/Postcodes_in_the_United_Kingdom)

### Usage

```ruby
class Address < ActiveRecord::Base
  validates :postal_code, postcode: true
end
```

### I18n

The default error message is `is not a valid postcode`

This can be translated in the same was as any other Rails valiation message using the key **:postcode**.

For the example Address model above, the customised en.yml would be:

    en:
      activerecord:
        errors:
          models:
            address:
              attributes:
                postal_code:
                  postcode: "is not valid"




## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
