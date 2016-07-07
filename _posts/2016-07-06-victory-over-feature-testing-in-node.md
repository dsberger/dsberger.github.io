---
layout: post
title: Victory Over Feature Testing in Node
date: 2016-07-06 19:45:00 -0700
categories: node testing nightwatch
---

Today I had a major breakthrough on feature testing in Node.

### The Problem

I originally learned web development in Ruby on Rails. Rails has been around for a decade, and the community has a commitment to test-driven development, so the suite of testing tools is very robust and stable. This has two consequences for me, now, trying to learn Node.

One, where Rails tends to have one established solution that is very well documented, Node has many options with varying levels of usability. If you're writing feature tests for a Rails app, you're going to use Capybara inside Rspec. In the Node ecosystem, there is Zombie.js, Protractor, Intern, and the package I finally settled on, Nightwatch. (I probably missed some in that list!) There doesn't seem to be any consensus about which way is _the best_, which is what I want to know as a learner.

Two, everything is so turnkey in Rails that I didn't have to tangle with the details of testing. Figuring out how to create and maintain a separate test environment wasn't something I had ever done before. I think I got it right and my test suite will be easy to expand now, but who knows!

(Sidebar: There also seems to be a difference in terminology: What a Rails dev would call a "feature test", Node calls "end to end". I _think_ Node devs use "feature test" to mean something like what a Rubyist calls a "unit test" or "controller test".)

### My Solution

I played around with a bunch of options and decided that [Nightwatch.js](http://nightwatchjs.org/) seemed like the closest thing to Capybara I was going to find. I liked Zombie.js, but I couldn't figure out how to make it compatible with Angular. It would work as long as I was serving static HTML, then fall apart as soon as I started loading Angular templates. Nightwatch took some finagling to set up, but the error messages were readable (imagine that...) and the documentation was excellent.

One thing that took a while to figure out is that I still need to start my app in a test environment before Nightwatch will go to work with Selenium. That was not clear from the docs, and, again, I'm from Rails world where Rspec just does that for you. There's probably a way to get that automated too, but I'm not going to worry about it right now.

So now I'm really happy I have all this working, and I can set about writing some good feature tests and TDD the heck out of this app. Tomorrow's challenge is getting the database set up for the test environment, including a database cleaner, and trying to find a Devise-like solution for user authentication. I've looked before and I'm not hopeful, so it probably means [Passport](http://passportjs.org/).
