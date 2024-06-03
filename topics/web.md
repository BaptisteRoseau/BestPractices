# Web

There are plenty of best practices to follow on the web to make your website more accessible or having a higher rank on search engines, hence more traffic. Here is a non-exhaustive list to help you in that regard.

## Accessibility

### WEBA001 - Contrast Checkers

Most Navigators today offer accessibility checkers to make your website components's contrast and colors allow everyone to be able to use it.

When developing a component, make sure your contrast is high enough. For example, here is how to do so using Firefox: <https://firefox-source-docs.mozilla.org/devtools-user/accessibility_inspector/#highlighting-of-ui-items>.

If possible, automatically check the accessibility of your website within your CI/CD pipeline using dedicated tools.

## SEO

### WEBS001 - robots.txt

Search engines use crawlers to map the web and find websites. You can guide them through yours using a `robots.txt` file at the root of your website.

See the [documentation](https://developers.google.com/search/docs/crawling-indexing/robots/intro).

### WEBS002 - sitemaps.txt

Similar to [robots.txt](#webs001---robotstxt), it allows to guide search engine crawlers on your website, hence improving your rank.

See the [documentation](https://developers.google.com/search/docs/crawling-indexing/sitemaps/overview).

Next: [Personal Improvement](topics/personal_improvement.md)
