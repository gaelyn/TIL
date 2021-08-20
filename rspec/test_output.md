Found [here](https://dev.to/shivashankarror/rspec-test-console-input-and-output-1jd3)

To test printed output in rspec:
1. Put expected output in block as below
2. format expectation to include output `.to_stdout`
```ruby
it 'can show files sorted by gender' do
      msg = <<~SORTED
      Smith Steve Male 3/3/1985 Red
      Seles Monica Female 12/2/1973 Black
      Kournikova Anna Female 6/3/1975 Red
      Kelly Sue Female 7/12/1959 Pink
      Hingis Martina Female 4/2/1979 Green
      Bouillon Francis Male 6/3/1975 Blue
      Bonk Radek Male 6/3/1975 Green
      Bishop Timothy Male 4/23/1967 Yellow
      Abercrombie Neil Male 2/13/1943 Tan
      SORTED

      expect { FileSorter.print_results(@sort_last_name) }.to output(msg).to_stdout
    end
    ```
    Formatting this way will not output text in test.
