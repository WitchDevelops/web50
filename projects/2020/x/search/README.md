# About

It is Project 0 for the [CS50’s Web Programming with Python and JavaScript](https://cs50.harvard.edu/web/2020/).

## Functionality

* user is able to type in a query and gets redirected to the Google Search results for the given query.
* "I'm feeling lucky" button redirects the user directly to the first link on the results page.
* Image search redirects the user to the Google Images search results page for the given query.

## Design
I have decided to come up with a name, branding and favicon for the Google Search clone. Because it's quick and lighweight, I thought that Zephyr would be a fitting name, one of the four winds in Greek mythology (read more about Zephyr [here](https://en.wikipedia.org/wiki/Zephyr)). Then the obvius color palette was in light blue with a tint of green, paired with a thin and airy font. I have chosen Montserrat Light with increased tracking for the airy feel, and went for a linear gradient from Deep Ocean Blue #005EB8 to Fresh Aquamarine #00FFD1, like an ocean breeze. The favicon is a simple compass rose in gradient colors. I have completed the color palette with a set of greys.

## Tech
### Basic search
Basic search functionality was achieved with a `<form>` element with an action attribute set to `https://www.google.com/search`. User input was given the `name="q"`. This allows to take user input from this form, give it a query parameter `q` and submit it to the Google search. All those elements allow for a redirect to the Google search results with a given user input query.

The code:
```html
<form class="search__form" action="https://www.google.com/search" method="GET">
    <input class="search__input" type="text" name="q">
    <input class="search__button" type="submit" value="Google Search">
</form>
```

### "I'm feeling lucky"
To be honest, I've always been scared of this function so I never used it, until CS50 told me to. Turns out, it takes you to the first search result.
Implementing this feature is simple: all you need to do is adding a `name="btnI"` to the `submit` button.
Upon inspection you may notice that the "I'm feeling lucky" button on Google appends the `&btn1` at the end of the URL query, thus adding `name="btnI"` attribute on the submit button achieves that behavior.

### Image search
To be able to achieve this functionality, one of the search parameters has to be `tbm=isch`. To achieve this, I added a hidden input with the `name="tbm"` and `value="isch"`. This way the `tbm=isch` gets appended to the search query and redirects the user to Google image search results.

## Helpful resources
* [StackOverflow: "I'm feeling lucky"](https://stackoverflow.com/questions/62869308/how-implement-im-feeling-lucky-in-html)
* [StackOverflow: Google Image search](https://stackoverflow.com/questions/63040965/how-do-i-create-a-link-to-google-image-search-via-html-form)
* [Article: Google search URL request parameters](https://stenevang.wordpress.com/2013/02/22/google-advanced-power-search-url-request-parameters/)