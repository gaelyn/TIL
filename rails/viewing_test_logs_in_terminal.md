Was doing some googling on testing Rails logs and found this [Stack Overflow](https://stackoverflow.com/questions/11770552/how-to-get-rails-logger-printing-to-the-console-stdout-when-running-rspec) with a useful command.  

`$ tail -f log/test.log`   

If you run this in one terminal tab and then run your tests in another, you should see your test logs output in the terminal.
