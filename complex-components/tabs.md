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
