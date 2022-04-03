# Introduction

The main goal of Univalidate is to create a common language that
any programming environment can make use of to validate data.

For example, if you create a website with a form for inputting data, 
you would probably want to validate that on the client, to make sure
people aren't sending bogus data to your endpoints, then validate it
again on the serverside, as the data received from the client can never truly 
be trusted.

If your frontend is written using [SvelteJS](https://github.com/sveltejs/svelte),
you will more than likely be validating the form input using a JavaScript library. 
If the backend is also running in a JavaScript environment, you could use the same library 
used for the frontend for the backend too.

This isn't always the case however, you could have a Java, PHP or Ruby backend. And as such,
the idea of Univalidate was born.

A write-once, validate-anywhere solution.

[Next - Specification](./2--specification.md)
