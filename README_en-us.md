# Complete Guide to Google Dorking: Operators, Syntax, Examples, and Security Applications
## What is Google Dorking?

> **Google Dorking** (also known as Google Hacking, or simply Dorking) is an advanced search technique that uses specific operators on Google to find information that is not usually accessible through common searches. It is frequently used in *OSINT* to capture sensitive data that may be exposed or unprotected.

---

This technique is widely used to:

* Find confidential files (passwords, backups, logs)
* Discover exposed directories and devices
* Perform security testing (pentesting)
* Collect information through OSINT
* Locate sensitive files (.sql, .txt, .xls, etc.)
* Identify open directory listings
* Find exposed IoT devices
* Detect misconfigurations
* Gather emails and metadata
* Conduct target footprinting during security audits

---

## Google Dorking Operator Table

| Operator          | Description                                            | Example                                                                                                                 |
| ----------------- | ------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------- |
| `site:`           | Restricts the search to a specific domain              | `site:gov.br`                                                                                                           |
| `inurl:`          | Searches for URLs containing the keyword               | `inurl:admin`                                                                                                           |
| `intitle:`        | Searches for pages with the term in the title          | `intitle:"index of"`                                                                                                    |
| `intext:`         | Searches for words in the page content                 | `intext:"confidential"`                                                                                                 |
| `filetype:`       | Searches for files with a specific extension           | `filetype:pdf "annual report"`                                                                                          |
| `ext:`            | Synonym for `filetype:`                                | `ext:xls site:example.com`                                                                                              |
| `cache:`          | Shows the Google cached version of the page            | `cache:example.com`                                                                                                     |
| `link:`           | Shows pages that link to a specific site               | `link:example.com`                                                                                                      |
| `related:`        | Searches for similar websites                          | `related:youtube.com`                                                                                                   |
| `allinurl:`       | All terms must be in the URL                           | `allinurl:admin login`                                                                                                  |
| `allintitle:`     | All terms must be in the page title                    | `allintitle:financial report 2024`                                                                                      |
| `allintext:`      | All terms must be in the body text                     | `allintext:password user`                                                                                               |
| `allinanchor:`    | Terms must appear in anchor text (links)               | `allinanchor:"private login"`                                                                                           |
| `"quotes"`        | Exact phrase search                                    | `"confidential information"`                                                                                            |
| `-word`           | Excludes results containing the term                   | `login -facebook`                                                                                                       |
| `OR` / \`         | \`                                                     | Combines terms (either/or)                                                                                              |
| `AND`             | All terms must be present                              | `filetype:pdf AND budget`                                                                                               |
| `*` (wildcard)    | Replaces any word                                      | `"password * root"`                                                                                                     |
| `( )`             | Groups terms or operators                              | `(login OR password) site:br`                                                                                           |
| I’m Feeling Lucky | Directly accesses the first result found in the search | `"wikipedia"` = wikipedia.org/wiki/Main\_page                                                                           |
| `define:`         | Returns definitions of the word                        | `define: world` /wər(ə)ld/, noun 1. the earth, together with all of its countries, peoples, and natural features. (etc) |           
| `ext:`            | Synonym for `filetype:`                                | `ext:xls site:example.com`                                                                                              |
| `cache:`          | Shows the Google cached version of the page            | `cache:example.com`                                                                                                     |
| `link:`           | Shows pages that link to a specific site               | `link:example.com`                                                                                                      |
| `related:`        | Searches for similar websites                          | `related:youtube.com`                                                                                                   |
| `allinurl:`       | All terms must be in the URL                           | `allinurl:admin login`                                                                                                  |    
| `allintitle:`     | All terms must be in the page title                    | `allintitle:financial report 2024`                                                                                      |
| `allintext:`      | All terms must be in the body text                     | `allintext:password user`                                                                                               |
| `allinanchor:`    | Terms must appear in anchor text (links)               | `allinanchor:"private login"`                                                                                           |

---

## Common Advanced Search Examples

##### - Search for confidential documents by type and content

`filetype:pdf | filetype:xls | filetype:doc "confidential" OR "internal"`

##### - Find files containing exposed passwords

`intitle:"index of" (passwords.txt | credentials.csv | config.php)`

##### - Collect corporate emails from a domain

`site:targetcompany.com intext:"@targetcompany.com"`

##### - Find backup directories and exports

`intitle:"index of" (backup | .sql | export)`

##### - Capture error messages revealing technology or versions

`intext:"Warning: mysql_fetch" | intext:"Deprecated: Function" site:.br`

##### - Locate publicly accessible IP cameras

`inurl:/view/index.shtml | inurl:top.htm intext:"camera"`

##### - Find admin login pages

`inurl:admin OR inurl:login intitle:"admin panel"`

##### - Locate configuration files (.env, .ini, .bak)

`inurl:.env | inurl:.ini | filetype:bak`

##### - Search for images with sensitive metadata

`site:imgur.com filetype:jpg OR filetype:png "confidential"`

##### - Detect CMS platforms and vulnerabilities

`inurl:wp-content OR inurl:joomla intitle:"index of"`

##### - Find open log files

`intitle:"index of" (log.txt | error.log | access.log)`

##### - Discover internal system links

`site:intranet.company.com inurl:dashboard OR inurl:status`

##### - Find HR documents and résumés

`filetype:pdf (résumé OR "curriculum vitae") site:company.com`

##### - List repositories and version files

`intitle:"index of" (.git | .svn | .hg)`

##### - Check for exposures in subdomains

`site:*.company.com -www`

##### - Combine multiple techniques for refined searches

`site:company.com filetype:xls intext:"password" inurl:restricted`

---

### For more ready-to-use queries:

The *Google Hacking Database (GHDB)* is maintained by Offensive Security and features a vast collection of categorized *dorks* tailored for specific results.

[Link to Dorks via ExploitDB](https://www.exploit-db.com/google-hacking-database)

---

⚠️ Legal Disclaimer
This content is provided solely for educational and controlled testing purposes.
Using it in unauthorized environments may constitute a cybercrime and carry serious legal consequences.

---

### Contribute with new dorks via Pull Request!

---

Would you like this exported as a `.md` file or in another format?
