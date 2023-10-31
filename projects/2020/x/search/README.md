# About

It is Project 0 for the [CS50’s Web Programming with Python and JavaScript](https://cs50.harvard.edu/web/2020/).

Deployed to Netlify: [Zephyr search live](https://zephyr-search.netlify.app/)

## Functionality

* user is able to type in a query and gets redirected to the Google Search results for the given query.
* "I'm feeling lucky" button redirects the user directly to the first link on the results page.
* Image search redirects the user to the Google Images search results page for the given query.
* advaced search lets the user use advanced search parameters, similar to the Google advanced search.

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

### Advanced search
After figuring out the image search, this one was easy. Upon closer inspection of advanced search string parameters I noticede that Google uses:
* `as_q` for the search using all the words, e.g. `as_q=funny+cat+videos` (it combines the words)
* `as_epq` for the exact search, e.g. `as_epq=rat+terrier`, which shows up in the search input field as `"rat terrier"`` (it looks up the exact phrase)
* `as_oq` to include any of the words, which results in the `OR` operator between the input words
* `as_eq` to exclude the words from the search, which shows in the saerch input fields with each word preceded with a minus sign.

Setting each of those parameters as the `name` attribute of the input field in the form allows to combine them into an advanced search string.

example:
```html
<input type="text" name="as_eq">
```

## Specification
(copied from CS50's web)

Your website must meet the following requirements:

1. Your website should have at least three pages: one for regular Google Search (which must be called index.html), one for Google Image Search, and one for Google Advanced Search.

2. On the Google Search page, there should be links in the upper-right of the page to go to Image Search or Advanced Search. On each of the other two pages, there should be a link in the upper-right to go back to Google Search.
3. On the Google Search page, the user should be able to type in a query, click “Google Search”, and be taken to the Google search results for that page.
    * Like Google’s own, your search bar should be centered with rounded corners. 
    * The search button should also be centered, and should be beneath the search bar.
4. On the Google Image Search page, the user should be able to type in a query, click a search button, and be taken to the Google Image search results for that page.
5. On the Google Advanced Search page, the user should be able to provide input for the following four fields (taken from Google’s own advanced search options)
    * Find pages with… “all these words:”
    * Find pages with… “this exact word or phrase:”
    * Find pages with… “any of these words:”
    * Find pages with… “none of these words:”
6. Like Google’s own Advanced Search page, the four options should be stacked vertically, and all of the text fields should be left aligned.
7. Consistent with Google’s own CSS, the “Advanced Search” button should be blue with white text.
8. When the “Advanced Search” button is clicked, the user should be taken to the search results page for their given query.
9. Add an “I’m Feeling Lucky” button to the main Google Search page. Consistent with Google’s own behavior, clicking this link should take users directly to the first Google search result for the query, bypassing the normal results page.
>You may encounter a redirect notice when using the “I’m Feeling Lucky” button. Not to worry! This is an expected consequence of a security feature implemented by Google.
10. The CSS you write should resemble Google’s own aesthetics.

## Helpful resources
* [StackOverflow: "I'm feeling lucky"](https://stackoverflow.com/questions/62869308/how-implement-im-feeling-lucky-in-html)
* [StackOverflow: Google Image search](https://stackoverflow.com/questions/63040965/how-do-i-create-a-link-to-google-image-search-via-html-form)
* [Article: Google search URL request parameters](https://stenevang.wordpress.com/2013/02/22/google-advanced-power-search-url-request-parameters/)
* Close inspection of the [Google Advanced search](https://www.google.com/advanced_search)