# Upstream dependency PR drafts

The implementation is committed in four independent branches. Upstream submission
through the GitHub integration returned HTTP 403 (Resource not accessible by
integration); no upstream pull request was created.

The earlier `chore/content-collections-0.15.3` and
`experiment/mdx-gray-matter-successor` WIP branches are superseded by
`chore/content-maintenance`.

Combined merge and validation:
https://github.com/TyceHerrman/tailnext/actions/runs/39499886361

Full branch and Node minimum validation:
https://github.com/TyceHerrman/tailnext/actions/runs/39498956600

The combined full audit still reports 10 alerts (2 moderate, 8 high), including
braces, brace-expansion, fast-uri, source-map-js and Vite/launch-editor.
No braces mitigation was included. These targeted changes do not claim to
resolve every dependency advisory.

## chore(deps): update Next.js to 16.4.2 and Sharp to 0.35.5

Branch: `chore/next-16.4.2`

[Open prefilled upstream PR form](https://github.com/arthelokyo/tailnext/compare/main...TyceHerrman:chore/next-16.4.2?expand=1&title=chore(deps)%3A%20update%20Next.js%20to%2016.4.2%20and%20Sharp%20to%200.35.5&body=Update%20Next.js%20and%20eslint-config-next%20together%20from%2016.3.4%20to%2016.4.2%2C%20and%20Sharp%20from%200.35.4%20to%200.35.5.%20Regenerate%20the%20npm%20lockfile%20without%20changing%20the%20root%20React%2C%20TypeScript%20or%20ESLint%20major%20versions.%0A%0AValidation%20passed%20in%20the%20fork%3A%20clean%20npm%20installation%2C%20type%20generation%2C%20lint%2C%20typecheck%2C%20formatting%2C%20Storybook%20browser%2Faccessibility%20tests%2C%20production%20build%20and%20Storybook%20build.%20See%20https%3A%2F%2Fgithub.com%2FTyceHerrman%2Ftailnext%2Factions%2Fruns%2F39498956600.%20All%20four%20proposals%20also%20merged%20cleanly%20and%20passed%20combined%20validation%3A%20https%3A%2F%2Fgithub.com%2FTyceHerrman%2Ftailnext%2Factions%2Fruns%2F39499886361.%0A%0AThis%20is%20a%20scoped%20update%2C%20not%20a%20claim%20that%20the%20full%20dependency%20audit%20is%20clean.%20Other%20dependency%20maintenance%20is%20proposed%20separately.)

Update Next.js and eslint-config-next together from 16.3.4 to 16.4.2, and Sharp from 0.35.4 to 0.35.5. Regenerate the npm lockfile without changing the root React, TypeScript or ESLint major versions.

Validation passed in the fork: clean npm installation, type generation, lint, typecheck, formatting, Storybook browser/accessibility tests, production build and Storybook build. See https://github.com/TyceHerrman/tailnext/actions/runs/39498956600. All four proposals also merged cleanly and passed combined validation: https://github.com/TyceHerrman/tailnext/actions/runs/39499886361.

This is a scoped update, not a claim that the full dependency audit is clean. Other dependency maintenance is proposed separately.

## chore(deps): maintain Content Collections and MDX frontmatter together

Branch: `chore/content-maintenance`

[Open prefilled upstream PR form](https://github.com/arthelokyo/tailnext/compare/main...TyceHerrman:chore/content-maintenance?expand=1&title=chore(deps)%3A%20maintain%20Content%20Collections%20and%20MDX%20frontmatter%20together&body=Update%20Content%20Collections%20core%20to%200.15.3%20and%20scope%20an%20npm%20alias%20from%20mdx-bundler's%20gray-matter%20dependency%20to%20%4011ty%2Fgray-matter%203.0.0.%20This%20removes%20the%20remaining%20legacy%20frontmatter%20chain%20without%20overriding%20YAML%20parsers%20globally.%0A%0AAdd%20explicit%20parser%2FMDX%20tests%20and%20a%20separate%20CI%20workflow.%20Tests%20cover%20YAML%20scalars%2C%20Unicode%2C%20folded%20text%2C%20BOM%2FCRLF%2C%20absent%2Fempty%20metadata%2C%20malformed%20YAML%2C%20compilation%20from%20source%20and%20files%2C%20and%20every%20current%20blog%2Flegal%20document.%20A%20separately%20installed%20legacy%20parser%20checks%20supported%20YAML%20against%20the%20previous%20behavior%20without%20reintroducing%20it%20into%20the%20application's%20lockfile.%0A%0ACompatibility%20changes%20are%20documented%3A%20executable%20JavaScript%20frontmatter%20is%20unsupported%2C%20and%20unquoted%20YAML%20timestamps%20remain%20strings%20instead%20of%20legacy%20Date%20objects.%20Tests%20assert%20the%20timestamp%20difference%20explicitly.%20Existing%20publishDate%20fixtures%20remain%20quoted%20and%20match%20the%20string%20schema.%0A%0ARefresh%20serialize-javascript%20to%20patched%207.1.2%20within%20core's%20declared%20range.%0A%0ACorrect%20SECURITY.md's%20stale%20clean-audit%20claim%20and%20document%20the%20remaining%20braces%20dependency%20without%20adding%20a%20braces%20override%20or%20suppressing%20alerts.%0A%0AValidation%20passed%20in%20the%20fork%2C%20including%20all%20seven%20parser%2FMDX%20tests%20and%20the%20separate%20legacy%20comparison%20on%20Node%2022%20and%2024%3A%20https%3A%2F%2Fgithub.com%2FTyceHerrman%2Ftailnext%2Factions%2Fruns%2F39499993441.%20Combined%20validation%20with%20the%20framework%2C%20Typography%20and%20Node%20proposals%20also%20passed%3A%20https%3A%2F%2Fgithub.com%2FTyceHerrman%2Ftailnext%2Factions%2Fruns%2F39499886361.%20Full%20dependency%20audit%20results%20are%20not%20represented%20as%20clean.)

Update Content Collections core to 0.15.3 and scope an npm alias from mdx-bundler's gray-matter dependency to @11ty/gray-matter 3.0.0. This removes the remaining legacy frontmatter chain without overriding YAML parsers globally.

Add explicit parser/MDX tests and a separate CI workflow. Tests cover YAML scalars, Unicode, folded text, BOM/CRLF, absent/empty metadata, malformed YAML, compilation from source and files, and every current blog/legal document. A separately installed legacy parser checks supported YAML against the previous behavior without reintroducing it into the application's lockfile.

Compatibility changes are documented: executable JavaScript frontmatter is unsupported, and unquoted YAML timestamps remain strings instead of legacy Date objects. Tests assert the timestamp difference explicitly. Existing publishDate fixtures remain quoted and match the string schema.

Refresh serialize-javascript to patched 7.1.2 within core's declared range.

Correct SECURITY.md's stale clean-audit claim and document the remaining braces dependency without adding a braces override or suppressing alerts.

Validation passed in the fork, including all seven parser/MDX tests and the separate legacy comparison on Node 22 and 24: https://github.com/TyceHerrman/tailnext/actions/runs/39499993441. Combined validation with the framework, Typography and Node proposals also passed: https://github.com/TyceHerrman/tailnext/actions/runs/39499886361. Full dependency audit results are not represented as clean.

## fix(deps): scope Typography selector-parser upgrade with regression checks

Branch: `experiment/typography-selector-parser-7`

[Open prefilled upstream PR form](https://github.com/arthelokyo/tailnext/compare/main...TyceHerrman:experiment/typography-selector-parser-7?expand=1&title=fix(deps)%3A%20scope%20Typography%20selector-parser%20upgrade%20with%20regression%20checks&body=Override%20postcss-selector-parser%20to%207.1.7%20only%20under%20%40tailwindcss%2Ftypography%2C%20replacing%20its%20pinned%206.0.10%20parser.%0A%0AAdd%20selector%20compatibility%20tests%20and%20compare%20complete%20generated%20Tailwind%20Typography%20CSS%20with%20a%20separately%20installed%20Typography%200.5.20%20using%20its%20original%20parser.%20Add%20production-browser%20checks%20for%20every%20current%20blog%20post%20and%20both%20legal%20pages%20at%20390px%20and%201440px%3A%20prose%20sizing%2C%20heading%20hierarchy%2C%20link%20underlines%2C%20list%20markers%20and%20horizontal%20overflow.%20The%20separate%20CI%20workflow%20runs%20the%20comparisons%20and%20rendered%20checks%20explicitly.%0A%0AThe%20fork's%20first%20preparation%20run%20passed%20the%20CSS%20comparison%2C%20browser%20checks%20and%20full%20project%20validation%3A%20https%3A%2F%2Fgithub.com%2FTyceHerrman%2Ftailnext%2Factions%2Fruns%2F39498497902.%20Portable%20npm%2010%2F11%20lockfiles%20and%20the%20follow-up%20validation%20passed.%20Dedicated%20Node%2022%2F24%20selector%20comparisons%20and%20production-browser%20checks%20passed%3A%20https%3A%2F%2Fgithub.com%2FTyceHerrman%2Ftailnext%2Factions%2Fruns%2F39500000683.%20Combined%20validation%20passed%3A%20https%3A%2F%2Fgithub.com%2FTyceHerrman%2Ftailnext%2Factions%2Fruns%2F39499886361.%0A%0ADocument%20the%20override's%20scope%20and%20removal%20condition.%20No%20unrelated%20parser%20consumers%20or%20braces%20overrides%20are%20changed.)

Override postcss-selector-parser to 7.1.7 only under @tailwindcss/typography, replacing its pinned 6.0.10 parser.

Add selector compatibility tests and compare complete generated Tailwind Typography CSS with a separately installed Typography 0.5.20 using its original parser. Add production-browser checks for every current blog post and both legal pages at 390px and 1440px: prose sizing, heading hierarchy, link underlines, list markers and horizontal overflow. The separate CI workflow runs the comparisons and rendered checks explicitly.

The fork's first preparation run passed the CSS comparison, browser checks and full project validation: https://github.com/TyceHerrman/tailnext/actions/runs/39498497902. Portable npm 10/11 lockfiles and the follow-up validation passed. Dedicated Node 22/24 selector comparisons and production-browser checks passed: https://github.com/TyceHerrman/tailnext/actions/runs/39500000683. Combined validation passed: https://github.com/TyceHerrman/tailnext/actions/runs/39499886361.

Document the override's scope and removal condition. No unrelated parser consumers or braces overrides are changed.

## fix(tooling): align Node support with locked dependency requirements

Branch: `fix/node-support-documentation`

[Open prefilled upstream PR form](https://github.com/arthelokyo/tailnext/compare/main...TyceHerrman:fix/node-support-documentation?expand=1&title=fix(tooling)%3A%20align%20Node%20support%20with%20locked%20dependency%20requirements&body=Replace%20the%20advertised%20Node%20%3E%3D20.9.0%20range%20with%20%5E20.19.0%20%7C%7C%20%5E22.13.0%20%7C%7C%20%3E%3D24.0.0.%20Locked%20Chokidar%2FVite%20require%20Node%2020.19%2B%2C%20and%20eslint-visitor-keys%20requires%20Node%2022.13%2B%20on%20the%20Node%2022%20line.%20Odd%20Node%2021%2F23%20versions%20are%20excluded%20by%20the%20locked%20test%20tooling.%0A%0ARetain%20Node%2024%20as%20the%20development%20target%20and%20preserve%20support%20for%20Node%2022.%20Update%20README%20and%20CONTRIBUTING%2C%20align%20the%20lockfile%20metadata%2C%20and%20test%20the%20exact%20Node%2020.19.0%2F22.13.0%20minimums%20plus%20current%20Node%2022%2F24%20in%20CI.%0A%0ARegenerate%20peer-dependency%20entries%20with%20npm%2010%20so%20npm%20ci%20remains%20usable%20with%20the%20npm%20bundled%20in%20Node%2020%2F22%2C%20as%20well%20as%20npm%2011%20on%20Node%2024.%20The%20root%20TypeScript%20remains%206.0.3%3B%20dependency-local%20TypeScript%205%20peers%20do%20not%20replace%20it.%0A%0AValidation%20covers%20clean%20npm%20ci%2C%20type%20generation%2C%20lint%2C%20types%2C%20formatting%2C%20browser%2Faccessibility%20tests%2C%20production%20and%20Storybook%20builds%20on%20the%20exact%20declared%20minimums%20and%20current%20Node%2022%2F24.%20Results%3A%20https%3A%2F%2Fgithub.com%2FTyceHerrman%2Ftailnext%2Factions%2Fruns%2F39498956600.%20No%20Node-24-only%20restriction%20or%20braces%20mitigation%20is%20introduced.)

Replace the advertised Node >=20.9.0 range with ^20.19.0 || ^22.13.0 || >=24.0.0. Locked Chokidar/Vite require Node 20.19+, and eslint-visitor-keys requires Node 22.13+ on the Node 22 line. Odd Node 21/23 versions are excluded by the locked test tooling.

Retain Node 24 as the development target and preserve support for Node 22. Update README and CONTRIBUTING, align the lockfile metadata, and test the exact Node 20.19.0/22.13.0 minimums plus current Node 22/24 in CI.

Regenerate peer-dependency entries with npm 10 so npm ci remains usable with the npm bundled in Node 20/22, as well as npm 11 on Node 24. The root TypeScript remains 6.0.3; dependency-local TypeScript 5 peers do not replace it.

Validation covers clean npm ci, type generation, lint, types, formatting, browser/accessibility tests, production and Storybook builds on the exact declared minimums and current Node 22/24. Results: https://github.com/TyceHerrman/tailnext/actions/runs/39498956600. No Node-24-only restriction or braces mitigation is introduced.
