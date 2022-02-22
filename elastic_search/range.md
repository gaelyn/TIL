[filter range date elasticsearch](https://stackoverflow.com/questions/25671150/filter-range-date-elasticsearch)
- gte = greater than or equal to
- gt = greater than
- lte = less than or equal to
- lt = less than
```
range.gte(Date.today) && range.lt(Date.today.next_year)
```