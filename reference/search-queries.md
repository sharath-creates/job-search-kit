# Search queries

Read this in step 5, when building the query set, and again during tuning when
a query needs replacing.

---

## The domain tiers

Source quality varies more than query wording does. Weight the tiers.

### Tier 1: applicant tracking systems
Postings appear here first, and an application here reaches a human recruiter's
queue rather than an aggregator's.

```
job-boards.greenhouse.io
jobs.lever.co
jobs.ashbyhq.com
myworkdayjobs.com
jobs.smartrecruiters.com
apply.workable.com
jobs.jobvite.com
boards.greenhouse.io
recruitee.com
teamtailor.com
```

Use the first five as `{{BOARD_DOMAINS_PRIMARY}}` and the rest as
`{{BOARD_DOMAINS_SECONDARY}}`.

### Tier 2: regional boards
Pick the ones matching the person's target locations. Set
`{{REGIONAL_DOMAINS}}` from this.

| Region | Domains |
|---|---|
| India | `iimjobs.com`, `hirist.tech`, `instahyre.com`, `cutshort.io` |
| United States | `builtin.com`, `dice.com`, `angel.co` |
| United Kingdom | `otta.com`, `cord.co`, `workinstartups.com` |
| Europe | `welcometothejungle.com`, `jobs.eurobrussels.com`, `honeypot.io` |
| Australia and NZ | `seek.com.au`, `seek.co.nz` |
| Remote-first | `wellfound.com`, `remoteok.com`, `weworkremotely.com` |

### Tier 3: everything else
One uncapped call per sweep, with the noise list excluded. Set
`{{NOISE_DOMAINS}}` to:

```
instagram.com, facebook.com, msn.com, youtube.com, pinterest.com,
quora.com, reddit.com, indeed.com, glassdoor.com
```

Indeed and Glassdoor are excluded on purpose. They mirror postings that already
appear on tier 1 with the original link stripped out.

---

## Query construction

A query has four parts: the titles, the location, the qualifier, and the
freshness window.

```
"<exact title>" OR "<exact title>" <location> <location>
```

Rules that matter:

- **Quote exact titles.** Unquoted `product owner` matches any page containing
  both words.
- **At most three titles per query.** More and the search engine ranks the
  broadest one and the others disappear.
- **Never put a `site:` operator inside the query string.** Use the tool's
  domain filter parameter. A `site:` operator inside a filtered query returns
  nothing and costs a credit.
- **Never set an include list and an exclude list on the same call.** Most
  search APIs reject it.
- **Freshness belongs in the parameter, not the text.** Adding "2026" or
  "recent" to the string narrows against page content, not against date.

---

## A worked set

For a person targeting product and analysis plus customer-facing technical, in
Bangalore and Hyderabad, at standard intensity, ten calls:

| # | Domain filter | Freshness | Query |
|---|---|---|---|
| 1 | primary | 24h | `"Product Owner" OR "Product Manager" Bangalore Hyderabad` |
| 2 | primary | 24h | `"Business Analyst" OR "Product Analyst" Bangalore Hyderabad` |
| 3 | primary | 24h | `"Technical Account Manager" OR "Solutions Consultant" India` |
| 4 | primary | 24h | `"Implementation Consultant" OR "Solutions Engineer" India SaaS` |
| 5 | secondary | 24h | `"Product Owner" OR "Business Analyst" Bengaluru` |
| 6 | secondary | 24h | `"Technical Account Manager" Bengaluru Hyderabad` |
| 7 | regional | 7d | `product owner business analyst Hyderabad Bangalore` |
| 8 | regional | 7d | `solutions consultant technical account manager India` |
| 9 | none, noise excluded | 24h | `careers "product owner" Bangalore apply` |
| 10 | none, noise excluded | 24h | `careers "solutions consultant" Hyderabad apply` |

Calls 5 through 8 rotate their domain filter by weekday, so a fortnight covers
every secondary and regional source without paying for all of them daily.

---

## Retiring a query

The Queries tab records runs, roles surfaced, and applications. A query with
three or more runs and zero applications is dead. Replace it by changing one
variable at a time:

1. Swap a title for its nearest neighbour in the same family.
2. Drop the location and let the domain filter carry the geography.
3. Move it to a different tier.

Changing two variables at once means you learn nothing from the result.

---

## Using a tool other than Firecrawl

The queries above are portable. The parameters are not.

| Concept | Firecrawl | Adaptation |
|---|---|---|
| Domain include | `includeDomains: [...]` | Some tools accept only `site:` inside the query. If so, run one call per domain and cut the title count to keep the call budget. |
| Domain exclude | `excludeDomains: [...]` | Prefix terms with `-` inside the query where supported. |
| Freshness | `tbs: "qdr:d"` or `"qdr:w"` | Look for a date or recency parameter. Where none exists, fetch and filter on the posting date, and raise `{{FETCH_CAP}}` to compensate. |
| Result count | `limit: 10` | Keep it at 10. Beyond that, relevance falls faster than volume rises. |

A plain web search tool with no domain filter works, at roughly half the yield.
Compensate by widening the watchlist rather than by running more queries.
