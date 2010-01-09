uk_postcode
===========

UK postcode parsing and validation for Ruby. I've checked it against every postcode I can get my hands on: that's about 1.8 million of them.

Usage
-----

    require "uk_postcode"

Validate and extract sections of a full postcode:

    pc = UKPostcode.new("W1A 2AB")
    pc.valid?   #=> true
    pc.full?    #=> true
    pc.outcode  #=> "W1A"
    pc.incode   #=> "2AB"
    pc.area     #=> "W"
    pc.district #=> "1A"
    pc.sector   #=> "2"
    pc.unit     #=> "AB"

Or of a partial postcode:

    pc = UKPostcode.new("W1A")
    pc.valid?   #=> true
    pc.full?    #=> false
    pc.outcode  #=> "W1A"
    pc.incode   #=> nil
    pc.area     #=> "W"
    pc.district #=> "1A"
    pc.sector   #=> nil
    pc.unit     #=> nil

Normalise postcodes:

    UKPostcode.new("w1a1aa").norm #=> "W1A 1AA"

Fix mistakes with IO/10:

    pc = UKPostcode.new("WIA OAA")
    pc.outcode #=> "W1A"
    pc.incode  #=> "0AA"

Gem?
----

    gem install uk_postcode
