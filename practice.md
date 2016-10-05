## Practicing our open source policy

This document is meant to give specific team guidance on putting our [open source policy](policy.md) into practice.

* All team members should feel empowered to contribute back to outside open source projects.
* We [contribute software to the public](#creating-freely), while also [protecting sensitive information](#protecting-sensitive-information).
* There are [narrow, documented exceptions](#exceptions) where we may delay or withhold source code.

KnuEdge team members working on FOSS should work with the strong presumption that all of their code will be visible to the public.

### Contributing back to outside projects

KnuEdge staff are encouraged to contribute back any modifications or improvements they make to open source software projects outside KnuEdge in the course of their work. When KnuEdge staff begin modifications to outside work, they should plan with eventual upstream contribution in mind.

In terms of licensing: contributions by KnuEdge will fall under the same license as the project they modify and should not seek to change the overall license status of the outside project.

Much of the work done by KnuEdge for its core products and paid services are supported by or run on open source software. Just as our staff has benefited from the contributions of those around the world, we should seek to better the tools we use for others.

#### How to license KnuEdge repos

When creating a repo, add a [LICENSE](LICENSE_TEMPLATE) and [CONTRIBUTING.md](CONTRIBUTING_TEMPLATE.md) file, and add/edit the [README.md template](README_TEMPLATE.md).

The preceding links are to our standard boilerplates for each of those, so you can just copy and paste them. In some cases, you may need to customize them for your use -- for example, this project uses a more open license so that it can be more freely copied or modified without requiring attribution.

You may wish make the following shell aliases

```bash
alias insert-license="curl -s https://raw.githubusercontent.com/KnuEdge/open-source-policy/master/LICENSE_TEMPLATE -o LICENSE"
alias insert-contrib="curl -s https://raw.githubusercontent.com/KnuEdge/open-source-policy/master/CONTRIBUTING_TEMPLATE.md -o CONTRIBUTING.md"
alias repodocs-init="insert-license && insert-contrib && echo 'Licensed.'"
```

You can then initialize a new KnuEdge repository's license information with:

```bash
repodocs-init
```

Want to take it even further and create the repo at the same time?

```bash
alias create-repo="mkdir \!* && cd \!* && git init ."
alias create-readme="curl -s https://raw.githubusercontent.com/KnuEdge/open-source-policy/master/README_TEMPLATE.md -o README.md"
alias create-knu-repo="create-repo \!* && repodocs-init && create-readme && sed 's/[Repo Name]/$(/usr/bin/basename $(pwd))/' README.md && git add . && git commit -m 'initial commit'"
```

Then create a repo and license it with:

```bash
create-knu-repo new-project-name
```

Even if you don't create a repo, it's recommended to use [this README.md template](README_TEMPLATE.md) that sums up what's going on.

### Accepting contributions from the public

Any KnuEdge FOSS project can (and should!) accept open source contributions from the public.

Projects can **encourage public contributions** by:

* Creating open issues where public help would be especially welcome.
* Labeling those issues with `help wanted` so people can scan issues quickly.
* Asking for contributions, in the README and in other public writing about the project.
* Providing solid documentation for any project setup process.
* Being super nice when communicating with volunteers.

As in the [open source policy](policy.md), non-core KnuEdge projects are made FOSS whenever possible. In this situation, contributors must agree to release their contributions under whichever license the project itself is released. Projects can inform contributors of this agreement by copying the [`CONTRIBUTING.md` template](CONTRIBUTING_TEMPLATE.md) and [the README.md template](README_TEMPLATE.md) file from this repo into new project repos.

When an KnuEdge project has a non-standard license status (e.g. it's a fork of a previously licensed project, or is a module/plugin for a GPL project), then that project needs to figure out an appropriate contributing agreement.

### Protecting sensitive information

As part of responsibly working in the open, KnuEdge team members are expected to protect information that needs to be protected. We already receive training and guidance about information we can’t publish for [ethical](https://www.oge.gov/web/oge.nsf/Topics), legal, and security reasons — this section is a reminder about sensitive information (formally called “[controlled unclassified information](http://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-171.pdf)”) to carefully protect when working with our open source projects. Sensitive information can include code, configuration, content, or documentation.

If KnuEdge team members aren't sure whether they should make something public, they should ask a person on our KnuEdge IT team for advice _first_.

If KnuEdge team members inadvertently come into the possession of classified information (Secret, Top Secret, etc.), they should immediately follow our standard security incident process.

Sensitive information we need to protect includes, but is not limited to:

* Information an attacker could plausibly use to help them compromise a system. Examples:
    * **Secret keys:** Passwords, passcodes, access codes, access tokens, API keys, TLS keys, SSH keys, OAuth secrets, or any other “secret keys” that protect access to something.
    * **Undisclosed vulnerabilities:** If we know of a security problem or potential security problem with our code that isn’t already publicly-known (such as a vulnerability that isn’t easy to find with scanning tools), we shouldn’t write publicly about it until we fix it.
* Nonpublic information in general about vulnerabilities, including attribution/source information (such as how and when we learned about a vulnerability, if the disclosure to us was not public).
* We may wish to withhold some non-KnuEdge IP addresses. If something looks like an IP address, ask KnuEdge Infrastructure before publishing that info.
* Personally Identifiable Information (PII). Here’s [OMB's definition and GSA's policy](http://www.gsa.gov/portal/content/104256).
* Some kinds of procurement and acquisition information, which may include non-public cost or pricing data, contract information, trade secrets, indirect costs, and direct labor rates. If you’re an KnuEdge team member working with this kind of data, ask KnuEdge IT or your BU lead for help determining whether it can be public.
* Emergency procedures, such as evacuation plans.

There are more categories of controlled unclassified information to protect; those are just the kinds that we work with most often. [Here’s the complete list.](http://www.archives.gov/cui/registry/category-list.html)

### Managing KnuEdge resources

KnuEdge intends to produce great software. That means not just rushing through projects to get them working as fast as possible, but managing [technical debt](https://en.wikipedia.org/wiki/Technical_debt) with an eye towards usability and reusability.

If a refactoring or feature makes the tool easier for KnuEdge to use in its work, and the teammate doing it is otherwise meeting their duties, then that's time well spent for KnuEdge and the open source community.

Open source projects can &mdash; and hopefully do! &mdash; get use and uptake from outside KnuEdge. It's also okay for individual teammates to create projects they intend to use both at KnuEdge and in their personal capacity.

Teammates do not need permission to start new open source projects in the KnuEdge GitHub organization. However, generally speaking, these projects must have some work applicability.

When creating new open source projects:

* If you're creating a repo because it's primarily for your KnuEdge work, and the work you perform in it is primarily to benefit KnuEdge, start the repo's life in the KnuEdge organization. It's okay if you also think it'll be helpful in personal work.
* If you're creating a repo that isn't primarily for KnuEdge work, but you think will likely see use at KnuEdge, start it in your personal account. If you don't have strong feelings or concerns about ownership, consider releasing the project under the [MIT License](https://opensource.org/licenses/MIT) (or one more permissive) to save yourself even having to ever think about it.

As people open issues and request features (no matter whether the repo is in your account or KnuEdge's), continue to exercise professional judgment about how to spend KnuEdge time.

If you think something will benefit KnuEdge and is worth the time, then that's valuable KnuEdge work. If it won't benefit KnuEdge but makes the library better for other uses, that may best be done with personal time.

#### Exceptions

KnuEdge currently does not and has no plans to release the source code under a FOSS license for its core products and services, as these are the secret sauce that enable KnuEdge to pay its employees and give them opportunities to contribute to other open source projects. If you are not sure whether a project should be released as open source, be sure to check with KnuEdge IT or your BU lead _first_, before releasing the code.
