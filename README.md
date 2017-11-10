# Phonetic Spelling
## NATO, LAPD and lots more

Papa - Hotel - Oscar - November - Echo - Tango - India - Charlie  
Sierra - Papa - Echo - Lima - Lima - India - November - Golf

---

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'phonetic'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install phonetic

## Usage

```ruby
msg = Phonetic::Speller.new.spell('WTF')
puts msg.join(' - ') # 'Whiskey - Tango - Foxtrot'

msg = Phonetic::Speller.new(Phonetic::Alphabet::DE).spell('ABC')
puts msg.join(', ') # 'Anton, Berta, Cäsar'
```

### Make your own Alphabet
```ruby
binary_alphabet = ('A'..'Z').map { |a| [a.downcase, a.ord.to_s(2)] }.to_h
Phonetic::Speller.new(binary_alphabet).spell('ABC').join # "100000110000101000011"
```

### Say it! (macOS only)
For a list of Voices on macOS see voices.csv

```ruby
Phonetic::Speaker.new('Anna').say(msg)

dutch_speakers = %w(Xander Ellen).map { |v| Phonetic::Speaker.new(v) }.cycle
Phonetic::Alphabet::NL.each_value { |word| dutch_speakers.next.say(word) }

spanish_speakers = %w(Diego Jorge Juan Monica Paulina).map { |v| Phonetic::Speaker.new(v) }
Phonetic::Alphabet::ES.each_value { |word| spanish_speakers.sample.say(word) }
```
