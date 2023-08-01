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

There are tradeoffs for each one:
- When using some third-party componens, if you render the content for inactive tabs (case number one), those components may not function correctly because of the `display: none`.
- It can be more performant to not render content that isn't visible. If there were lots and lots of tabs (there usually are not many tabs unless you're making a web browser), then you'd want to go down this path. You would also want to choose this option if the contents of the panel were expensive to render.

## Hypothetical Tablist Component API

```
<TabList @selected={{this.selected}} @onChange={{this.onChangeSelectedTab}} as |t|>
  <t.tab @key='tab-0' @title='Simple tab'>I am simple</t.tab>
  <t.tab @key='tab-1' @title='My Tab 1' as |tab|>
    <FancyChartComponent @hidden={{not tab.isActive}} />
  </t.tab>
  <t.tab @key='tab-2' as |tab|>
     <tab.button>
         My tab 2 {{#if this.isDoingSomethingAsync}}<Spinner />{{/if}}
     </tab.button>
     <tab.panel>
        My Content
     </tab.panel>
  </t.tab>
</TabList>
```

## Example Implementation

This [Limber Example] contains an implementation of this pattern (without any styles / CSS) but includes all of the aria behaviors mentioned in the MDN document.

[Limber Example]: https://limber.glimdown.com/edit?c=MQAgKghgRlCmAmICqBJEBRAHhAtgBwBtYAoYgAwoHMArAZxAIEsA3WEPAJ1mcdgHdijfAHsOAFxABhYSIB2sWRIBmHGSADkAAUpMcOWBwD0AYxl5h8xeoDcgkeJABvEGI4RjAawQAaEMfcAFgggAL4gKmpaOkL6Rq7uHoyylDZ25g7OFqHhqjgamrA4cEY4wvCMSrwcqULpEs4BELQBvrAAjr5KstkReVqFxYZBBHgGNfb1IKXllQY9uRoDBgC00xVV43VOIJQArozwAGKi85EFRQaGwlDUsMZihkliBrIQBLSpxIaGIACyZRU5mJhDtYBIICAuEoDApjGxgSAIQARADyvxAsCI%2BkUfi4EGeiCSiJchUI%2BNgtm%2BIBQ3QheIIiLwhEY-jEjAsvgAnsJdupEEwvAROSBdrQ2BBafB4FkBWwAmIxHhaAAub6URhiAK7KAAOlMOEMTGhEHEhiWHGWUNWANmHGIplktAkUJAAF4pjaqgAKJS7WT3dndKH-GbezGFBRiXwAbX8BAIUASAF0AJROYggPxvBMJL3h7FiFO2TNcMS7DjdL1p10APiz8cTni9sl28aLxBC7ftFidLmgABlGE6AIIcVR8ADKuyZogk7rWtp9foDFjzWMjMbE0FoqfTmczRAkW6gx2MordIAADMX9w7e41ZPAiBwL3nq3XHBn95mKiAvcfaB1Ihkk1N1XXdS801LctZBvb8qX%2BVhIUYSh5S-b9fzzHUvGFcD3QAIlHccACUUPlfCQAAH0ojFsNgXDwJAQix2EPh%2B1gJQxHwtNP2-eDDAA6Nj1PUUkx1MUxGHBUOEYKBdmeL18OPJJ4FgTB8N8ZYAEZ2z4-dMNgOiGIIojWNI1CuJ49C9L7E9hDPWgAGpHLgmyqRQJQQD4WB1C4REjyCDFH18SgQQRTU2CdE0xGsvTMOE%2Bzzxrd0AKAhRKE1KybL4hKHIva9Yr4kJCv4v5hCQohOJK7JMTFEADKMsCTJYtiOMsvdstskTaGWZZXL09zPO83zxQCyKt3EXxSiQ8LAoUeBqp-Tz-2gbqQAAHivLLOszXLzxS7c0pAgIQGWEAtP6orquKzNqsEvad3EsEpNcWT5NgRTlMfNSNK2y7du3ITVsSx6lBBqtLpu-cQlsaz80jHUICldBWEUQcnQUAwvXUHDpT4WR1F8B8nwMLtv2gis-3fDF10UHUuGm2AUcjdHnnkDhsdx1iCaJiUSY4FMv07UhjAIJp6EgKBWZQZ48jUtn4HoaQ5EjDqv00eJPGCY8UEQd09gOY4Oc1IddJAL9KDBdgJUxXWqw6kswRgkAyDwG2CGWAASRwTcAnX4BCMgb2Ki2raHCdw3uBB7d4-cKe6X3EY4ShALFIgo71xjE5NFOjOD0hMwsSQH0t19qez5PAKLkuPor3OcLJ0Ej2gJgnXQAgY%2Bs%2BOXACIck9z49W7Edv89DiQhwAOWEMQI-TglO-Jp3KYAQkT8PI4JfPbszdbZbJZ4a2sxxHGAJJlnhnFE8Hodh4ZJIxXEAAhDjRFgV0W3jEIoe-da5IVCxFqQmEEQV0SloD4UASaRgEBlhpzuASUBx8160FnvAhAX8IE7SgTAh0rhgG0FdEg3ugE3byAILrL%2BgCDiEJ9sQnU-tKE7S%2BqpTANDfzINQRnJil4KL4W0vhRhnV4D4hgThGhmgcKCOysfLI6hRYsg8OoHufdq4SktlImyx8XSaAsMRDiXBmiS1oBo78h8drHw1hqIgX8nAn3YXQ9ec90EhAAFTH0eEoExG1DB-2BLIMx%2B53FnwvmIDR61yjMHqvAGhidSG2wDmEUW4tXTqGvk6ZYcSCBKNUCAsBUBMkUWYWpUBPDEQyRgWLOA8YEBQE5DEuhDCwi9ylAoepfdJ7T04QSL%2BATvzH05LwAgCTbGn08hwjezi3GOA8WEwwESAnrQEqSMWB8OwizFrQCWA4b4YkwArJWZgLCq1jhrNwWtEBpNvrrC8BsjiiH-MQs2pyEjaxbjfduF4P4EBvM885tl6DumjEmG8ElJZDw%2Be6NcEZFDU1jrtBpby24MndCEreTcQBwIzgvOOS8E50JzqnCZ8A0WWwkKo5IH1tqOzLJTOuVdZDFzURSIWX5dH6NgIY7cZc3QfmslfLlKUEVQHBQQAA-DqNouwDCci6aIYc8ZsbRhyW-PJ%2BEkzqDTKK0VIAgWjx3nvFZsBekbVbFEtpftEVXOGcq0BlyKJaI4sowlYgwXvIIDYpB2yRwtSnDOBw-KoDGLCNg5YlTMTiLDe6kINZFmtmNf0wZiAvSNGaIA-cx5XRen1OYSwEg002UltLWW5sdrZUxQgxO5bgj5r0uSy2rpE51pIKWmylz24NqFSKmtfE2UqA5QEIxHaVGyD0X2zlgbu37kFi26d0MoaLINeSQ%2BIc1JbFUkoCArYJBJM2RgbA%2BAiC7P2VIQ5uaOq-K8IgKt8BJYXnUGDYQqRt4gAsF029kL5B8EluXOh1730gE-ZLG8X5d7LKXdZdahadmaEjSk34woAJKM0Ne81T0nE3ugDYnRDKa6odfRvSWNimhUQApRY1%2BrDrHhABI%2BiKSH1IbZGIEB6hb1aXUOR-cD6-AWDZjFPSC7KPQA47vQTUBqNiPUImao1HGPMdvQAJnY9VKT3HFCRkKgJwN9ChMQcMFBp0CylkHvA8VCgZBiBAA&format=glimdown
