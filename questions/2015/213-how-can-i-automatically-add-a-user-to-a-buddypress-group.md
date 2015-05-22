---
title: Can I automatically add users to BuddyPress Groups whenever they complete registration/checkout?
categories: questions
tags: buddypress, api-scripting, mu-plugins-hacks
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/213
toc-enable: false
---

Yes, but this requires a small bit of custom code. You can use the example below and configure it to automatically add users who register at specific s2Member Levels to BuddyPress Groups of your choosing.

## Installation Instructions

- Create this directory and file (using code below): `/wp-content/mu-plugins/s2-bp-groups.php`

- Configure the `$s2member_bp_groups_map` array as seen in the code sample.

```php
<?php
add_action('ws_plugin__s2member_during_configure_user_registration', function (array $vars) {
    extract($vars); // Variables from registration context.

    # Configuration. Array keys are s2Member Role names.
    # See: <https://s2member.com/kb-article/s2member-rolescapabilities/>
    # Each Role can be added to an array of one (or more) BuddyPress Groups, by slug.
    # A BuddyPress Group slug can be acquired by inspecting its Permalink in WordPress.
    $s2member_bp_groups_map = array(
      'subscribe' => array(), // Free Subscribers are not added to any BP Groups.
      's2member_level1' => array('test-group'), // Add Members who register at Level 1 to this BG Group.
      's2member_level2' => array('test-group', 'another-group'), // Add Members who register at Level 2 to these two groups.
      's2member_level3' => array(), // Members who register at Level 3 are not added to any BP Groups.
      's2member_level4' => array(), // Members who register at Level 4 are not added to any BP Groups.
    );

    # Do NOT edit anything below this line.
    if (bp_is_active('groups')) {
        if (!empty($s2member_bp_groups_map[$role])) {
            foreach ($s2member_bp_groups_map[$role] as $_group_slug) {
                if (($_group_id = BP_Groups_Group::group_exists($_group_slug))) {
                    groups_join_group($_group_id, $user->ID);
                }
            }
        }
    }
});
```
