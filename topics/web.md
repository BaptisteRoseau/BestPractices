# Web

There are plenty of best practices following on the web to make your website more accessible or having a higher rank on search engines, hence more traffic. Here is a non-exhaustive list to help you to do so.

## Accessibility

### WEBA001 - Contrast Checkers

Most Navigators today offer accessibility checkers to make your website components' contrast and colors allow everyone to be able to use it.

When developing a component, make sure your contrast is high enough. For example, here is how to do so using Firefox: <https://firefox-source-docs.mozilla.org/devtools-user/accessibility_inspector/#highlighting-of-ui-items>.

If possible, automatically check the accessibility of your website within your CI/CD pipeline using dedicated tools.

## SEO

### WEBS001 - robots.txt

Search engines use crawlers to map the web and find websites. You can guide them through yours using a `robots.txt` file at the root of your website, and prevent them going into unauthorized pages.

See the [documentation](https://developers.google.com/search/docs/crawling-indexing/robots/intro).

### WEBS002 - sitemaps.txt

Similar to [robots.txt](#webs001---robotstxt), it allows guiding search engine crawlers on your website, hence improving your rank.

See the [documentation](https://developers.google.com/search/docs/crawling-indexing/sitemaps/overview).

## Database

### WEBD001 - Transactions And Roll back

When doing an SQL query that is not read-only, always use a transaction to be able to roll back.

If in a script, use:

```sql
BEGIN TRANSACTION [Tran1]
  BEGIN TRY
    
    <your SQL query goes here>

    COMMIT TRANSACTION [Tran1]
  END TRY
  BEGIN CATCH
      ROLLBACK TRANSACTION [Tran1]
  END CATCH  
```

If manually writing the command, use:

```sql
BEGIN TRANSACTION;
<your SQL query goes here>
<your SELECT query to make sure everything is OK goes here>

-- If everything is OK
COMMIT TRANSACTION;

-- If you somehow screw up
ROLLBACK TRANSACTION;
```

Next: [Personal Improvement](./personal_improvement.md)
