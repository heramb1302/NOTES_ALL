In [13]: from django.db import connection

In [14]: connection.queries
Out[14]: 
[{'sql': 'SELECT "models_posts"."id", "models_posts"."post_title", "models_posts"."post_content", "models_posts"."published_date" FROM "models_posts" WHERE "models_posts"."id" >= 2 LIMIT 21',
  'time': '0.000'},
 {'sql': 'SELECT "models_posts"."id", "models_posts"."post_title", "models_posts"."post_content", "models_posts"."published_date" FROM "models_posts" WHERE "models_posts"."id" >= 2 LIMIT 1',
  'time': '0.000'},
 {'sql': 'SELECT "models_posts"."id", "models_posts"."post_title", "models_posts"."post_content", "models_posts"."published_date" FROM "models_posts" WHERE "models_posts"."id" >= 2 LIMIT 1 OFFSET 1',
  'time': '0.000'},
 {'sql': 'SELECT "models_posts"."id", "models_posts"."post_title", "models_posts"."post_content", "models_posts"."published_date" FROM "models_posts" WHERE "models_posts"."post_title" LIKE \'s%\' ESCAPE \'\\\' LIMIT 21',
  'time': '0.009'}]