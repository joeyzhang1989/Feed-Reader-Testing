# Project Overview

This project using [Jasmine](http://jasmine.github.io/) test framework to write testing suites to a given web-based application that reads RSS feeds. Exploiting Jasmine to write a number of tests against a pre-existing application. Test the underlying business logic of the application as well as the event handling and DOM manipulation.

# Getting started
## live
https://joeyzhang1989.github.io/Feed-Reader-Testing/
## Locally

**1.** Clone this repo:

```
$ git clone https://github.com/joeyzhang1989/Feed-Reader-Testing.git
````
**2.** Clone this repo:
Open the index.html to see the result
# Code walkthrough
## Structure
1.Test suites
	*RSS Feeds
	*The menu
	*Initial Entries
	*New Feed Selection
## Specific Test suites
1.RSS Feeds
```js
it('are defined', function() {
            expect(allFeeds).toBeDefined();
            expect(allFeeds.length).not.toBe(0);
        });

        it('allfeeds URL are defined', function() {
            allFeeds.forEach(function(feed) {
                expect(feed.url).toBeDefined();
                expect(feed.url.length).not.toBe(0);
            });

        });

        it('allfeeds name are defined', function() {
            allFeeds.forEach(function(feed) {
                expect(feed.name).toBeDefined();
                expect(feed.name.length).not.toBe(0);
            });

        });
```
2.The menu
```js
		var body = $("body");
        var menuIcon = $('.menu-icon-link');

        it('is hidden by defaul', function() {
            expect(body.hasClass('menu-hidden')).toBe(true);
        });


        it('is clicked with proper change', function() {
            //first click
            menuIcon.click();
            expect(body.hasClass('menu-hidden')).toBe(false);
            //second click
            menuIcon.click();
            expect(body.hasClass('menu-hidden')).toBe(true);
        });
```
3.Initial Entries
```js
 beforeEach(function(done) {
            loadFeed(0, function() {
                done();
            });
        });

        it('are loaded and completed', function(done) {
            expect($('.feed .entry').length).toBeGreaterThan(0);
            done();
        });
    });
```
4.New Feed Selection
```js
		var container = $('.feed');
        var firstFeed = container.html();
        var secondFeed;
        beforeEach(function(done) {
            loadFeed(1, function() {
                secondFeed = container.html();
                done();
            });
        });

        it('is loaded and changed', function(done) {
            expect(firstFeed).not.toEqual(secondFeed);
            done();
        });
```
#License
This project is a public domain work, dedicated using
[MIT](https://opensource.org/licenses/MIT). Feel free to do
whatever you want with it.