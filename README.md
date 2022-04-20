# Actor - OSINT Scraper

## OSINT scraper

This actor should help you to retrieve sensitive data from many websites which might leak the data out from..

The OSINT data scraper supports the following features:

-   Search any keyword - You can search any keyword you would like to have and get the results

-   Scrape multiple websites - Scrape Codepad, Dumpz, Github Gist, Ideone, Pastebin, Pasteorg, Textbin and many more websites.

-   Customizable - Create a custom scraping function that will run on the results within your needs.

## Bugs, fixes, updates and changelog

This scraper is under active development. If you have any feature requests you can create an issue from [here](https://github.com/tugkan/osint-scraper/issues).

## Input Parameters

The input of this scraper should be JSON containing the list of pages on OSINT that should be visited. Required fields are:

| Field                | Type    | Description                                                                                                                                                                                                    |
| -------------------- | ------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| searchKeywords               | Array  | (required) Keyword array that you want to search on the websites.                                                                                                                                                       |
| codepad       | Boolean | (optional) This will enable the `codepad` module which will going to scrape http://codepad.org/. |
| dumpz       | Boolean | (optional) This will enable the `dumpz` module which will going to scrape https://dumpz.org/. |
| githubgist       | Boolean | (optional) This will enable the `Github Gist` module which will going to scrape https://gist.github.com/. |
| ideone       | Boolean | (optional) This will enable the `ideone` module which will going to scrape https://ideone.com/. |
| pastebin       | Boolean | (optional) This will enable the `pastebin` module which will going to scrape https://pastebin.com/. |
| pasteorg       | Boolean | (optional) This will enable the `pasteorg` module which will going to scrape https://www.paste.org/. |
| textbin       | Boolean | (optional) This will enable the `textbin` module which will going to scrape https://textbin.net/. |
| proxy                | Object  | Proxy configuration                                                                                                                                                                                            |
| extendOutputFunction | String  | (optional) Function that takes a JQuery handle ($) as argument and returns object with data                                                                                                                    |

This solution requires the use of **Proxy servers**, either your own proxy servers or you can use [Apify Proxy](https://www.apify.com/docs/proxy).

##### Tip

When you want to have a scrape only couple of modules, you can set `true` on the module flags and the actor will initiate to scrape only these websites.

If you want to scrape Pastebin, please try to use US-based proxies because Pastebin is restricted in many countires.

### Compute Unit Consumption

The actor optimized to run blazing fast and scrape many as listings as possible. Therefore, it forefronts all listing detail requests. If actor doesn't block very often run consume ~0.01-0.03 compute units per 100 pages.

### OSINT Scraper Input example

```json
{
  "searchKeywords":[
    "@gmail",
    "db_pass"
  ],
  "codepad": true,
  "dumpz": true,
  "githubgist": true,
  "ideone": true,
  "pastebin": true,
  "pasteorg": true,
  "textbin": true,
  "proxy": {
    "useApifyProxy": true
  }
}

```

## During the Run

During the run, the actor will output messages letting you know what is going on. Each message always contains a short label specifying which page from the provided list is currently specified.
When items are loaded from the page, you should see a message about this event with a loaded item count and total item count for each page.

If you provide incorrect input to the actor, it will immediately stop with failure state and output an explanation of what is wrong.

## OSINT Export

During the run, the actor stores results into a dataset. Each item is a separate item in the dataset.

You can manage the results in any languague (Python, PHP, Node JS/NPM). See the FAQ or <a href="https://www.apify.com/docs/api" target="blank">our API reference</a> to learn more about getting results from this OSINT actor.

## Scraped Output

The structure of each item in OSINT Scraper looks like this:

### Item Detail

```json
{
  "keyword": "@gmail",
  "url": "https://dumpz.org/bmwhk2yRt45M"
}
```
