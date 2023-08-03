---
description: Designing a Tabbed UI
---

# Tabs

A component to provide a tabbed UI should provide an easy to use API that offers escape hatches for exceptional scenarios.

The anatomy of a tabbed UI:
- The Tab List - list of Tabs
- Tab - the thing you click on to select a Tab Panel
- Tab Panel - content associated with a specific Tab

The ARIA spec details how to do tabs: https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles/tab_role


# Important Considerations

1. Should the inactive Tab Panel be rendered when its associated Tab is not selected and simply hidden with CSS (e.g., `display: none;`)?
2. Or should inactive Tab Panels be conditionally rendered with an `{{#if` block?
3. Can I bind the selected tab to a route or URL query parameter without much fuss?
4. Can I add my own widgets in the Tab (e.g., error indicators, counters, loading indicators, a dots menu with options)?
5. Can I render the TabList using data from an API response? Can users dynamically create, remove, edit tab titles?

There are tradeoffs for each one:
- When using some third-party componens, if you render the content for inactive tabs (case number one), those components may not function correctly because of the `display: none`.
- It can be more performant to not render content that isn't visible. If there were lots and lots of tabs (there usually are not many tabs unless you're making a web browser), then you'd want to go down this path. You would also want to choose this option if the contents of the panel were expensive to render.

## Hypothetical Tablist Component API

```hbs
<TabList @label='My tabs' @selected={{this.selectedTab}} @onChange={{this.onSelectTab}} as |tabs|>
  <tabs.tab @key='foo' @title='Tab 1'>
    foo content
  </tabs.tab>
  <tabs.tab @key='bar' @title='Tab 2' @skipRenderWhenInactive={{true}}>
    bar content
  </tabs.tab>
  <tabs.tab @key='zoo'>
    <:title>
      <CustomThing />
    </:title>
    <:default>
      Zoo stuff!!!
    </:default>
  </tabs.tab>
</TabList>
```

## Example Implementation

This [Limber Example] contains an implementation of this pattern (without any styles / CSS) but includes all of the aria behaviors mentioned in the MDN document.

[Limber Example]: https://limber.glimdown.com/edit?c=MQAgKghgRlCmAmICqBJEBRAHhAtgBwBtYAoYgAwoHMArAZxAIEsA3WEPAJ1mcdgHdijfAHsOAFxABhYSIB2sWRIBmHGSADkAAUpMcOWBwD0AYxl5h8xeoDcgkeJABvEGI4RjAawQAaEMfcAFgggAL4gKmpaOkL6Rq7uHoyylDZ25g7OFqHhqjgamrA4cEY4wvCMSrwcqULpEs4BELQBvrAAjr5KstkReVqFxYZBBHgGNfb1IKXllQY9uRoDBgC00xVV43VOIJQArozwAGKi85EFRQaGwlDUsMZihkliBrIQBLSpxIaGIACyZRU5mJhDtYBIICAuEoDApjGxgSAIQARADyvxAsCI%2BkUfi4EGeiCSiJchUI%2BNgtm%2BIBQ3QheIIiLwhEY-jEjAsvgAnsJdupEEwvAROSBdrQ2BBafB4FkBWwAmIxHhaAAub6URhiAK7KAAOlMOEMTGhEHEhiWHGWUNWANmHGIplktAkUJAAF4pjaqgAKJS7WT3dndKH-GbezGFBRiXwAbX8BAIUASAF0AJROYggPxvBMJL3h7FiFO2TNcMS7DjdL1p10APiz8cTni9sl28aLxBC7ftFidIBO7q9OqHDvKbJ71brjgzIAqIC9AEIRxrA7QdURkpq01PMyWweXuq5dhTpyFp6X934LKOVzraDJYF6AELCYRECXt08O3uyYQSAdLsdZAnEBFyvZcLFsbtHQkMRoAAGUYJ0AEEOFUPgAGVdiZUQ-w9UMDB9P0AwsPMsUjGNYKgWhU3THcGDBFxoGOYxRTdEAAAZix3L8JEaWR4CIDg2LzYDtzomclDnSjV3XShNTdV13XYtNzwrLi6Kpf5WEhRhKHlac6NnPMdS8YVFPdAAiFC0IAJV0%2BULJAAAfJyMRM2AzMUkArNQ4Q%2BDg2AlDECytwM8Tvmk6NKOY0Uk1vMEkIVDhGCgXZni9CzKKSeBYEwCzfGWABGdtxJ3IzYHczzLOsvy7L04LQtKujouEFjaAAana9SmqpFBJL4WB1C4REYKCDF%2BN8SgQQRTU2CdE0xDC0qjJatqQBrd1pLXBQ5ICRqmuapjWtYpTutK08DszTThG0oggqWncwkxMUJLnCrTIU6rfP8wKGtoy7VtFZZljO8Kfj6kABqG8VRrm2DxF8UptJmsaFHgB7DMkr1AfoAAeDj9suxioBi%2BhNugGSdvk5YQEK0G6IuprGYx4naCio62risUxES1wUrSh9MugbLcvygn6dZ9mSeO6idSUGWq1BxnMxCSC6PzSMdQgKV0FYRQEKdBQCPUUzpT4WR1F8PiBIMLs6NUytgI1xQdS4JHYF1yMDeeeQOC9E2PLNi2rYlG2OBTE8I-tAgmnoSAoG9lBnjyXKffgehpDkSN-unTR4k8YJKJQRB3T2A5jj9zVEJKkBp0oBi8AlTFi6rf7dzLCsQDIRv5AIZYABJHCr1ci-gEIyC40864YxD0PDe4EFbsT24vYetY4ShVzFIgF5Lry15NTfKsn0hMwsSQ%2BPr4TgIPjfV3Py%2BH1vo-TLt0EYOgJgnXQAgl7Ch2XABEQuvI%2BlEv5iB-ifaeEhEIADlfxzx3gSP%2B9s9yd3nGvWe88CQn0zNOXGycyTPBrGFRwjhgBJGWM7UawCwGIQgQyJIYpxCPkCqIWAroWzxhCMrHcuNUoKgsCzEsr4OFCygBZYRiJkoQGWNvO4BJXQWTIZg2giCFEIB4ZIomJpGCyIdK4V8tBXQqKAauHuzcx68OWvAExQ8zE6lHjwqRWV%2BK5TsbOVR6jd7eXYo5CyRULLOKJvAfEsjTJ2M0KZYJl0yFZHUMYJgnh1CAOAQ-CU9cYkHTIS6TQFgbKBS4M0eOtAsniRIUTMhFCsaNFoMsKABBWoeA0GyMQRB1ApjKdkxwnJeAEEQMCV06hWntK6eJMhz1YBjNKmQvOGoiDTJ3GQx4ShFmZiqZ4hxWCkGaJCAAKmWRUMZuNDACOBLICpSzHCPFkFQsiigym43KMwGctjTHAIsQQYuPC-Ax1oMY4Zn96HLE%2BSk1QRAlGUU%2BY5VxOVMBKL8dIvRywY5wHjAgKAnI7FrycWEIBUoFDYq2bQeBYhvEEh4ZcuiGysYnC8dg4IzZfwgE0LQRIeACluI4AAdSCLIGk7g2SsBTJ06xVzemYisU4chmzgHbI0VYg51yjlisOas3hJznmXJOYQmOxCOykESbHcA8F6EYkwGnDOZgLDZzEnnNwBcBlAu-l8kuOx9hHFENjMxNd7UJELs6hhbEuEEC4n6x1rM2LRiTFxbm8dwE-2EtQ0SYUcWBsTe6ahuD34gHkbvFBO4AHPy3gy%2BA2b64SHSckB8hNIRoIPA4w%2B99ZAXwyceFW058mFNgMUim183STlTQ46SbE00NPoT-AA-DqNoR4OCcnJaIJC8Z-bRnBWIyiFkkwdJAJOydIBo1QMzAQ0kerYBUpALjVsryiW0PTa6n567IWBscjkwKqSS1iHjROggPyVGmuQt9TC2EHBjtKWEXRsjUWYkidB39IQawnNbBeshEr%2BlzlqQEKRO5KKui9PqcwlgJDYaavHROyda5EwOnmxRa8aPBBI6VKt9dXRr2YyQKjTU6EutY8O%2B9jHxJdpUD2gIJTeNpNkAU4TvaqICZ3BHTjCnHqMx1ae8kJCp5Gv%2BVIUUwIcBgCAckc1lqpDWqI-9E9%2BAz0Xq9GgXAuaQRtT0zqJTqmrPqYNcQXKWwcpKAgK2CQWn6BYFwIQNgqc0ZWqzjiO1%2BcvCIHo-AeObF1Dy2EKkPBZ9ZDkuSwOeQfB443wcYl3LIB8vxy4vg3VHm6K4zI2azQcGhm-GFNJFJrLS23pLTspL0Afl5JbY-LrOoLA5b6xB%2BgTlpJOQvceralEWURNSy%2BdrIyOHqGS4VdQs2dxpcvIoSMD0dUU0cdAHbBCTsLaiR5IZiZqgsrW0M5LAAmdrbLGAcrRgYXlCgBUBlYNijgR5KUszu-tn2i1SrHaoqdqA535vQEWzd9QAAvFbO3j3KjWxjvhkhdMyAM0kSgIBDA45OVj%2BZ56Wa42VL5-zBAxA48zAALRfLmssSglDzm59TwwtPAr08Z0dwwCO4dhROfVp02qRdqf1aeCgZBiBAA&format=glimdown
