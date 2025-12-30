# Preston Issues

GitHub help facilitate open source development through git, a distributed revision control system. 

Aside from version control through git repositories, GitHub offers issue tracking. 

This repositories keeps track of issues for Preston, a biodiversity dataset tracker. The aim of this repository is to keep track of Preson related communication by making them available through ... a git repository. 

## Methods 

The github issues and their associated attachments are tracked by periodically executing the following command 

```bash
# optionally set token to increase api limits. 
export GITHUB_TOKEN=[your personal github token] 
preston track https://github.com/bio-guoda/preston/issues
```

## Results 

After tracking the issues, each issue and their associated comment is available in json format. 

The example below prints the content associated with [issue #1](https://github.com/bio-guoda/preston/issues/1) of [Preston](https://github.com/bio-guoda/preston) using preston, grep and jq.

```
preston head \
 | preston cat \
 | grep hasVersion \
 | grep -E "https://api.github.com/repos/.*/issues/1[^0-9]" \
 | head -1 \
 | preston cat \
 | jq .
```

yielding the following result:

```json
{
  "url": "https://api.github.com/repos/bio-guoda/preston/issues/1",
  "repository_url": "https://api.github.com/repos/bio-guoda/preston",
  "labels_url": "https://api.github.com/repos/bio-guoda/preston/issues/1/labels{/name}",
  "comments_url": "https://api.github.com/repos/bio-guoda/preston/issues/1/comments",
  "events_url": "https://api.github.com/repos/bio-guoda/preston/issues/1/events",
  "html_url": "https://github.com/bio-guoda/preston/issues/1",
  "id": 358301396,
  "node_id": "MDU6SXNzdWUzNTgzMDEzOTY=",
  "number": 1,
  "title": "support crawling Atlas of Living Australia",
  "user": {
    "login": "jhpoelen",
    "id": 1084872,
    "node_id": "MDQ6VXNlcjEwODQ4NzI=",
    "avatar_url": "https://avatars.githubusercontent.com/u/1084872?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/jhpoelen",
    "html_url": "https://github.com/jhpoelen",
    "followers_url": "https://api.github.com/users/jhpoelen/followers",
    "following_url": "https://api.github.com/users/jhpoelen/following{/other_user}",
    "gists_url": "https://api.github.com/users/jhpoelen/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/jhpoelen/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/jhpoelen/subscriptions",
    "organizations_url": "https://api.github.com/users/jhpoelen/orgs",
    "repos_url": "https://api.github.com/users/jhpoelen/repos",
    "events_url": "https://api.github.com/users/jhpoelen/events{/privacy}",
    "received_events_url": "https://api.github.com/users/jhpoelen/received_events",
    "type": "User",
    "user_view_type": "public",
    "site_admin": false
  },
  "labels": [
    {
      "id": 1045930075,
      "node_id": "MDU6TGFiZWwxMDQ1OTMwMDc1",
      "url": "https://api.github.com/repos/bio-guoda/preston/labels/enhancement",
      "name": "enhancement",
      "color": "a2eeef",
      "default": true,
      "description": "New feature or request"
    }
  ],
  "state": "closed",
  "locked": false,
  "assignee": null,
  "assignees": [],
  "milestone": null,
  "comments": 1,
  "created_at": "2018-09-08T14:49:22Z",
  "updated_at": "2019-09-23T12:52:47Z",
  "closed_at": "2019-09-23T12:52:47Z",
  "author_association": "MEMBER",
  "type": null,
  "active_lock_reason": null,
  "sub_issues_summary": {
    "total": 0,
    "completed": 0,
    "percent_completed": 0
  },
  "issue_dependencies_summary": {
    "blocked_by": 0,
    "total_blocked_by": 0,
    "blocking": 0,
    "total_blocking": 0
  },
  "body": "Atlas of Living Australia maintains a registry of biodiversity datasets. \r\n\r\nfrom https://api.ala.org.au several endpoints seem appropriate:\r\n\r\nhttp://collections.ala.org.au/ws/collection\r\n\r\nhttp://collections.ala.org.au/ws/dataResource\r\n\r\nhttp://collections.ala.org.au/ws/dataProvider\r\n\r\n",
  "closed_by": {
    "login": "jhpoelen",
    "id": 1084872,
    "node_id": "MDQ6VXNlcjEwODQ4NzI=",
    "avatar_url": "https://avatars.githubusercontent.com/u/1084872?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/jhpoelen",
    "html_url": "https://github.com/jhpoelen",
    "followers_url": "https://api.github.com/users/jhpoelen/followers",
    "following_url": "https://api.github.com/users/jhpoelen/following{/other_user}",
    "gists_url": "https://api.github.com/users/jhpoelen/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/jhpoelen/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/jhpoelen/subscriptions",
    "organizations_url": "https://api.github.com/users/jhpoelen/orgs",
    "repos_url": "https://api.github.com/users/jhpoelen/repos",
    "events_url": "https://api.github.com/users/jhpoelen/events{/privacy}",
    "received_events_url": "https://api.github.com/users/jhpoelen/received_events",
    "type": "User",
    "user_view_type": "public",
    "site_admin": false
  },
  "reactions": {
    "url": "https://api.github.com/repos/bio-guoda/preston/issues/1/reactions",
    "total_count": 0,
    "+1": 0,
    "-1": 0,
    "laugh": 0,
    "hooray": 0,
    "confused": 0,
    "heart": 0,
    "rocket": 0,
    "eyes": 0
  },
  "timeline_url": "https://api.github.com/repos/bio-guoda/preston/issues/1/timeline",
  "performed_via_github_app": null,
  "state_reason": "completed"
}
```

## Discussion

By tracking GitHub issues and versioning their content, we can now access issues without being constrained by GitHub API rate limits. Also, the associated content can now be accessed and processed outside the GitHub platform without putting pressure on the GitHub API services.
 

