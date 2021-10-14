Was doing some googling on testing Rails logs and found this [Stack Overflow](https://stackoverflow.com/questions/1015739/how-can-we-watch-the-rails-development-log) with a useful command.  

`$ tail -f log/test.log`   

If you run this in one terminal tab and then run your tests in another, you should see your test logs output in the terminal.
