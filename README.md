# trellis-backup-during-deploy

[![GitHub tag](https://img.shields.io/github/tag/ItinerisLtd/trellis-backup-during-deploy.svg)](https://github.com/ItinerisLtd/trellis-backup-during-deploy/tags)
[![license](https://img.shields.io/github/license/ItinerisLtd/trellis-backup-during-deploy.svg)](https://github.com/ItinerisLtd/trellis-backup-during-deploy/blob/master/LICENSE)

Backup WordPress database during [Trellis](https://github.com/roots/trellis) deploys.

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
- [Author Information](#author-information)
- [Feedback](#feedback)
- [Change log](#change-log)
- [License](#license)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Requirements

- Trellis [9dfddfd](https://github.com/roots/trellis/commit/9dfddfd0d5f7d10886d2f434c02d3bd23edb8684) or later
- Ansible v2.4 or later


## Installation

Add this role to `requirements.yml`:

```yaml
# requirements.yml
- src: https://github.com/ItinerisLtd/trellis-backup-during-deploy
  version: 0.1.2 # Check for latest version!
```

Add this role to the [`deploy_initialize_after` hook](https://roots.io/trellis/docs/deploys/#hooks):
```yaml
# group_vars/all/deploy-hooks.yml
# Learn more on https://roots.io/trellis/docs/deploys/#hooks
deploy_initialize_after:
  - "{{ playbook_dir }}/vendor/roles/trellis-backup-during-deploy/tasks/main.yml"
```

## Usage

[Deploy](https://roots.io/trellis/docs/deploys/#example) as usual. No special action needed.

[`$ wp db export`](https://developer.wordpress.org/cli/commands/db/export/) is invoked during deploy. You can find the database dump in `/srv/www/example.com/releases/2018XXXXXXXXXX/example_com_env-2018-XX-XX-XXXXXXX.sql` – be sure to check the pre-latest `release`-folder (e.g. the release before deploy) since `current` serves as alias to the latest release.

## Author Information

[trellis-backup-during-deploy](https://github.com/ItinerisLtd/trellis-backup-during-deploy) is a [Itineris Limited](https://www.itineris.co.uk/) project created by [Tang Rufus](https://typist.tech).

Special thanks to [the Roots team](https://roots.io/about/) whose [Trellis](https://github.com/roots/trellis) make this project possible.

Full list of contributors can be found [here](https://github.com/ItinerisLtd/trellis-backup-during-deploy/graphs/contributors).

## Feedback

**Please provide feedback!** We want to make this library useful in as many projects as possible.
Please submit an [issue](https://github.com/ItinerisLtd/trellis-backup-during-deploy/issues/new) and point out what you do and don't like, or fork the project and make suggestions.
**No issue is too small.**

## Change log

Please see [CHANGELOG](./CHANGELOG.md) for more information on what has changed recently.

## License

[trellis-backup-during-deploy](https://github.com/ItinerisLtd/trellis-backup-during-deploy) is released under the [MIT License](https://opensource.org/licenses/MIT).
