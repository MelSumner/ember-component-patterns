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

1. Is my TabList accessible? Does it use ARIA or semantic HTML so that all users can use it?
2. Should the inactive Tab Panel be rendered when its associated Tab is not selected and simply hidden with CSS (e.g., `display: none;`)?
3. Or should inactive Tab Panels be conditionally rendered with an `{{#if` block?
4. Can I bind the selected tab to a route or URL query parameter without much fuss?
5. Can I add my own widgets in the Tab (e.g., error indicators, counters, loading indicators, a dots menu with options)?
6. Can I render the TabList using data from an API response? Can users dynamically create, remove, edit tab titles?

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
    {{#each this.dynamicTabs key='key' as |dt|}}
      <tabs.tab @key={{dt.key}} @title={{dt.title}}>
        {{dt.content}}
      </tabs.tab>
    {{/each}}
  </TabList>
```

## Example Implementation

This [Limber Example] contains an implementation of this pattern (without any styles / CSS) but includes all of the aria behaviors mentioned in the MDN document.

[Limber Example]: https://limber.glimdown.com/edit?c=MQAgKghgRlCmAmICqBJEBRAHhAtgBwBtYAoYgAwoHMArAZxAIEsA3WEPAJ1mcdgHdijfAHsOAFxABhYSIB2sWRIBmHGSADkAAUpMcOWBwD0AYxl5h8xeoDcgkeJABvEGI4RjAawQAaEMfcAFgggAL4gKmpaOkL6Rq7uHoyylDZ25g7OFqHhqjgamrA4cEY4wvCMSrwcqULpEs4BELQBvrAAjr5KstkReVqFxYZBBHgGNfb1IKXllQY9uRoDBgC00xVV43VOIJQArozwAGKi85EFRQaGwlDUsMZihkliBrIQBLSpxIaGIACyZRU5mJhDtYBIICAuEoDApjGxgSAIQARADyvxAsCI%2BkUfi4EGeiCSiJchUI%2BNgtm%2BIBQ3QheIIiLwhEY-jEjAsvgAnsJdupEEwvAROSBdrQ2BBafB4FkBWwAmIxHhaAAub6URhiAK7KAAOlMOEMTGhEHEhiWHGWUNWANmHGIplktAkUJAAF4pjaqgAKJS7WT3dndKH-GbezGFBRiXwAbX8BAIUASAF0AJROYggPxvBMJL3h7FiFO2TNcMS7DjdL1p10APiz8cTni9sl28aLxBC7ftFidIBO7q9OqHDvKbJ71brjgzIAqIC9AEIRxrA7QdURkpq01PMyWweXuq5dhTpyFp6X934LKOVzraDJYF6AELCYRECXt08O3uyYQSAdLsdZAnEBFyvZcLFsbtHQkMRoAAGUYJ0AEEOFUPgAGVdiZUQ-w9UMDB9P0AwsPMsUjGNYKgWhU3THcGDBFxoGOYxRTdEAAAZix3L8JEaWR4CIDg2LzYDtzomclDnSjV3XShNTdV13XYtNzwrLi6Kpf5WEhRhKHlac6NnPMdS8YVFPdAAiFC0IAJV0%2BULJAAAfJyMRM2AzMUkArNQ4Q%2BDg2AlDECytwM8Tvmk6NKOY0Uk1vMEkIVDhGCgXZni9CzKKSeBYEwCzfGWABGdtxJ3IzYHczzLOsvy7L04LQtKujouEFjaAAana9SmqpFBJL4WB1C4REYKCDF%2BN8SgQQRTU2CdE0xDC0qjJatqQBrd1pLXBQ5ICRqmuapjWtYpTutK08DszTThG0oggqWncwkxMUJLnCrTIU6rfP8wKGtoy7VtFZZljO8Kfj6kABqG8VRrm2DxF8UptJmsaFHgB7DMkr1AfoAAeDj9suxioBi%2BhNugGSdvk5YQEK0G6IuprGYx4naCio62risUxES1wUrSh9MugbLcvygn6dZ9mSeO6idSUGWq1BxnMxCSC6PzSMdQgKV0FYRQEKdBQCPUUzpT4WR1F8PiBIMLs6NUytgI1xQdS4JHYF1yMDeeeQOC9E2PLNi2rYlG2OBTE8I-tAgmnoSAoG9lBnjyXKffgehpDkSN-unTR4k8YJKJQRB3T2A5jj9zVEJKkBp0oBi8AlTFi6rf7dzLCsQDIRv5AIZYABJHCr1ci-gEIyC40864YxD0PDe4EFbsT24vYetY4ShVzFIgF5Lry15NTfKsn0hMwsSQ%2BPr4TgIPjfV3Py%2BH1vo-TLt0EYOgJgnXQAgl7Ch2XABEQuvI%2BlEv5iB-ifaeEhEIADlfxzx3gSP%2B9s9yd3nGvWe88CQn0zNOXGycyTPBrGFRwjhgBJGWM7UawCwGIQgQyJIYpxCPkCqIWAroWzxhCMrHcuNUoKgsCzEsr4OFCygBZYRiJkoQGWNvO4BJXQWTIZg2giCFEIB4ZIomJpGCyIdK4V8tBXQqKAauHuzcx68OWvAExQ8zE6lHjwqRWV%2BK5TsbOVR6jd7eXYo5CyRULLOKJvAfEsjTJ2M0KZYJl0yFZHUMYJgnh1CAOAQ-CU9cYkHTIS6TQFgbKBS4M0eOtAsniRIUTMhFCsaNFoMsKABBWoeA0GyMQRB1ApjKdkxwnJeAEEQMCV06hWntK6eJMhz1YBjNKmQvOGoiDTJ3GQx4Sgxm40MAI4EsgKlLMcI8WQVCyKKDKbjcozAZy2NMcAixBBi48L8DHWgxjhmf3ocsG5KTVBECUZRG5jlXE5UwEovx0i9HLBjnAeMCAoCcjsWvJxYQgFSgUHChxcCEHYM0SEHZdEqlGROF4zFiBmy-hAJoWgiQ8AFLcRwAA6kEWQNJ3BslYCmTp1jdm9MxFYh6yyKgnMMGcnZ6zCEx2IR2UgiTY7gHgvQjEmA04ZzMBYbOYk85uALgM1539bklx2PsI4ohsZmJruqhIhdtUMLYlwggXEzWatZmxaMSYuLc3juAn%2BwlqGiTCvCy1nr3TUNwe-EA8jd4oJ3AA5%2BW8iXBvrhIdJyQHyE0hGgg8DjD731kBfDJx4VbTnyYU2AxSKbXzdJOX1DjpJsT9Q0%2BhP8AD8Oo2hHg4JybxwIOBIXjP7aMXyxGUQskmDpIAG0NpAM6qBmYCGkjFbAHFIBcatguai2h-rdX3P7T8y1jkcmBVSTGsQ7r60EHuSo2VyFvqYWwg4WtpSwi6NkRCzEkTn2nuxes1sC6yFcv6XOWpAQpE7koq6L0%2BpzCWAkEBpq8dE7J1rkTA6YbFFr2Q8EaDpVE311dGvLDJBENNToTqnDVb10YfEoWlQxaAglJI2k2QBSqMlqouRncEcCPscerw3GTpOREAXZmPtoicPQCTNGR9ciiU4Y4EeJMbdxKNg8JQVQfp4DLFMI0jgypU3wAlhp0Q2m%2BBAOeErB6Qnvm-KbgQOTy8FOiBylp1JQZgjSgVAgCWjcpRJEoNpgATOxPAmBTOlXMxwojYgbMsxwIfShUBfzAhwNpziD1uOGF4-x-BhhRXkhIVPKVTypCigS2AIByR5WKqkMqyD-0Z34DnQur0aBcChpBG1BLOpOMitnTliVxBcpbBykoCArYJD5foFgXAhA2CpzRkqrOOI1X5y8IgND8B45sXUPLYQnxMz2uWyAeAnJXg4BZCUp1SZpwFtkB29bA55B8HjjfBxq3bsgHu-HNWIBrZEEwlAE7uE8x60LOW%2BT3BNacDB4oJEgVhsEDEIrMKPFwiiBwEiMJ1r%2BAgArqjsJgPNYsVQpGSAG8wQ10zEj0JsE2IohuAouWuR0CKGSsWn0KO0ewR1JGZntAqxk8vNBEAH13RkEO8dlkyxKID3scA0XuBTsU22huAI7VCrj26mvWXJ3jBnc2g4zX8uqJ6gsKyL00ZbOZlMtp0y3gHojNgNpynEBHHQDAPM2ANvSoGMjA7sJzuoDSEUJGMKIRUzBvwdl8VdFcbyw4DgUhjh4m0G1P9lJa9vuwF%2B-9nhC7cZvrrLAzH63XdtPw%2BJXGSQ8BpTe7gDhLyoDF-aSAQwOfDTQExCQsKue28EBrAXvgmZ1sB59otUqM6FUmlgBCY7tfKJD8jCk5vnfW%2BQo71HzZWQxCclGEMpPf2NTqBrEhKUMqoDrPX9szLMecCr74bBuVmg31DN%2BMKaSKTyVSauTGpBCB473Lydmx%2BVdLNG7aAe5JoZyaSJyATRdLaSiMlCJTbF8N-O3IZdbQqA-FmLbfnYfB6EVBXSiaAghfA6AeAjyIZRMaoMlFA9QdbXzN-ClRgKlNGAwelBQJlAMVgOFGTKZbFFmCg7AoPUfLLYgqAQg2AkgqJMg9QAALyQOgOnWVDt3kL4UkCKxkBK28yb2UPWUULd20OVEG1hzEGUMzAAC0XxQ0ywlAlB5xbCWYdDDCRtCDhDDcCDeVyFJ9jAAgD0dR9dtdS0EDTIUlwCnJ4AxAnJFkiDXCJCIkyEwjKo-8UC4ixBHE3ds8pFkijdA9jkOVp0XCR5oBoDllPCAgBU78nRhUstutxVTwKAyBiAgA&format=glimdown
