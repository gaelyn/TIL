`ruby lib/night_writer.rb message.txt braille.txt` will create an array of two
ARGV arguments.
ARGV[0] = message.txt
ARGV[1] = braille.txt

`message = File.open(ARGV[0], "r")` - "r" for read mode
`braille = File.open(ARGV[1], "w")` - "w" for write mode
