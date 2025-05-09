# Front End Tech Test

We would like you to demonstrate your Vue skills along with using Vue store and API calls.

The test itself is not elaborate, but tests a wide reaching area of skills, making use of a production Salesfire API.

## What to create

We want you to create a simple search box which displays some results from a Salesfire API. We have outlined the steps you need to carry out below - we will be observing how you implement these steps, the way you write and format code, and the way you make use of Vuex to keep a central and organised state.

For this test you may use the browser's native fetch function to call the API.

What you need to do:

- Create a new public Git repo and push to Github so we can review - you can optionally use GitHub pages or Netlify to host your app.
- Create a new Vue project, https://vuejs.org/guide/quick-start.
- Install Pinia for the store and central state.
- Create two components, a SearchBar and a ResultsSet.
- When the user carries out a search triggering an onInput event, you need to call the store, which calls the API and updates the state - make use of actions and mutations.
- You can then show results from the state in the results component using Vuex getters.


## API Spec

GET https://aix.salesfire.co.uk/api/searcha
Query Params:
client_id | Uuid | the site ID, you can use 'dbf1dbc9-a940-48c2-b44b-0bb6dc63924e' for this test
query | String | the query
limit | Int | the number of results to show
page | Int | the page number

Common queries could include "rado", "omega".

## Typical Time

Anyone competent with Vue can achieve this in roughly 30 minutes. A person less experienced with Vue may be required to spend longer.

This is also an opportunity to show off any other skills :-)

## Notes and Tips

You will need to prevent results showing from previous pending API calls.
Components should follow modern standards, be semantic, and be mindful accessibility practices.
Usability is key, think about how the user might interact, and what to display if there's no results returned.
Code should be clean, and understandable, and be error free.
