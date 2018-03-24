# Configure category groupings & taxonomies

## About

### Principal entities

IMPACT OSS data model contains the following principal entities:
- Recommendations: the Recommendations and Treaty Body Observations a State receives from the different UN Human Rights Mechanisms (or Bodies)
- Actions: the Implementing actions a State defines to address the Recommendations
- SDG Targets (optional): the targets set by the UN for the 17 Sustainable Development Goals (SDGs)
- Users: the application users

### Taxonomies

These entities can be classified according to multiple category groupings, also called taxonomies that need to be set up on the server - taxonomies cannot currently be managed through the UI.

Taxonomies can include universal classifications of recommendations used by the UN such as
- Human Rights Mechanisms (or Bodies)
- Reporting Cycles
- Human Rights Issues (or Themes)
- Affected Persons
- Recommending States (applicable to UPR (Universal Periodic Review) recommendations only)

... and State-specific classifications of recommendations and actions (and users) such as
- Recommendation Clusters (for clustering overlapping recommendations and assign actions to clusters)
- Organisations (for identifying Government agencies responsible for implementation of actions, and application users).

Finally, also the SDGs are regarded as taxonomies, classifying the SDG Targets (and optionally also recommendations or actions if desired).

## Initialise taxonomies & categories

Taxonomies should and categories could be defined in the basic "Seeds" file [/db/seeds.rb](https://github.com/impactoss/impactoss-server/blob/master/db/seeds.rb) that allows initialising the database with default content during installation and many common taxonomies and categories are included by default. Note: in addition to the basic default Seeds file there is also an advanced Seeds file [/db/advanced_seeds.rb](https://github.com/impactoss/impactoss-server/blob/master/db/advanced_seeds.rb) that only contains the most basic taxonomies and categories - to use the basic version, delete or rename the default Seeds file and rename the basic Seeds file to `seeds.rb`.

While categories can easily be added through the UI after the initial, installation, taxonomies can not be managed using the UI but must be updated in the database, e.g. using the Rails CLI (Command Line Interface).

### Initialise taxonomies

Here is an example for how a taxonomy can be set up in the Seeds file:

```
body = Taxonomy.new(
    title: 'Human Rights Mechanism',
    tags_recommendations: true,      
    tags_measures: false,
    tags_sdgtargets: false,
    tags_users: false,
    allow_multiple: false,
    has_manager: true,
    priority: 1,
    is_smart: false,
    groups_recommendations_default: 1,
  )
body.save!
```

For each taxonomy the following attributes can be specified (see also [/db/schema](https://github.com/impactoss/impactoss-server/blob/master/db/schema.rb)):

| Attribute | Type | Required | Description |
|---|---|---|---|
| `title` | text | ✔️ | the taxonomy title (not currently used and overridden by client configuration) |
| `tags_recommendations` | boolean || classifies Recommendations? |
| `tags_measures` | boolean || classifies Actions? |
| `tags_sdgtargets` | boolean || classifies SDG Targets? |
| `tags_users` | boolean || classifies Users? |
| `allow_multiple` | boolean || false: categories are exclusive, true: multiple categories allowed |
| `has_manager` | boolean || if user can be assigned and made responsible for category (will recive email reminders for overdue indicator status updates) |
| `priority` | integer || display order of taxonomy (can also be used for taxonomy groups defined by client config, e.g. priority 1-10 for universal and 11-20 for national taxonomies) |
| `is_smart` | boolean || if categories are SMART criteria - determines UI presentation |
| `groups_measures_default` | integer || if Actions are grouped (or subgrouped) by category in Action lists. 1: primary group, 2: subgroup |
| `groups_recommendations_default` | integer || if Recommendations are grouped (or subgrouped) by category in Recommendation lists. 1: primary group, 2: subgroup |
| `groups_sdgtargets_default` | integer || if SDG Targets are grouped (or subgrouped) by category in SDG Target lists. 1: primary group, 2: subgroup |



## Initialise categories

Here an example how categories can be initialised using FactoryGirl:
```
FactoryGirl.create(
    :category,
    taxonomy:body,
    title:'Universal Periodic Review',
    short_title:'UPR',
  )
```

> Note: the taxonomy attribute must reference a taxonomy previously defined in the Seeds file (here: `taxonomy:body`)

For each category the following attributes can be specified (see also [/db/schema](https://github.com/impactoss/impactoss-server/blob/master/db/schema.rb)):

> Remember: opposed to taxonomies, categories can also be created, updated and deleted through the UI

| Attribute | Type | Required | Description |
|---|---|---|---|
| `title` | text | ✔️ | the category title |
| `short_title` | string | ✔️ | the category short title, used for tags|
| `reference` | string || the category reference, should be unique, can be used for sorting |
| `description` | text || the category decsription (supports markdown) |
| `url` | string || a category URL if relevant |
| `draft` | boolean || if category is draft (`true`) or public (`false`) |
| `user_only` | boolean || if category can only tag users (`true` or `false`), relevant only for categories of taxonomy where `tags_users:true` |
| `taxonomy_id` | integer || the taxonomy id (note: in the Seeds file use previously defined taxonomy variable instead, eg `taxonomy:body`) |
| 'manager_id' | integer || a user id (not to be specified in Seeds file but using UI only)
