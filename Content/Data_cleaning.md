# Data cleaning

Data cleaning process include only cleaning the NULL value.
The extraction script takes only specific keys.
- In first request: script collect only the repositories names and owners
- In second request: script collect commits (owner, date, massage) from the repositories which were collected in first request.
- In third request: script collect content from main tree in main repository page (name, path, size, type) from the repositories which were collected in first request.
If repository empty the script skip it.
