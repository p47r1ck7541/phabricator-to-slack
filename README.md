# Phabricator-to-Slack

[![Build Status](https://travis-ci.org/p47t/phabricator-to-slack.svg?branch=master)](https://travis-ci.org/p47t/phabricator-to-slack)
[![GoDoc](https://godoc.org/github.com/p47t/phabricator-to-slack?status.svg)](https://godoc.org/github.com/p47t/phabricator-to-slack)
[![Coverage Status](https://coveralls.io/repos/github/p47t/phabricator-to-slack/badge.svg?branch=master)](https://coveralls.io/github/p47t/phabricator-to-slack?branch=master)
[![Go Report Card](https://goreportcard.com/badge/github.com/p47t/phabricator-to-slack)](https://goreportcard.com/report/github.com/p47t/phabricator-to-slack)
[![codebeat badge](https://codebeat.co/badges/9e65f307-a91b-4016-9da1-c1bfe62cffb5)](https://codebeat.co/projects/github-com-p47t-phabricator-to-slack)

## What?

The code demostrates sending Phabricator notifications to Slack. It is implemented with Go majorly for advatange of single-binary deployment.

## Why?

Phabricator and Slack are among my favorite tools. It will be nice if they can work together.

## How?

Phabricator-to-Slack works by installing itself as a HTTP hook of Phabricator. After receiving notification from Phabricator, it digs more information from Phabricator via its Conduit API and send the message to specified Slack channel.

### Build the code

    go get github.com/p47t/phabricator-to-slack

### Install as system service

    sudo phabricator-to-slack install

#### Ubuntu 12.04

Ubuntu 12.04 is the only tested platform. However, it should work only any platform that Go supports.

If you are using upstart, you should edit `/etc/init/phabricator-to-slack.conf` and add the following environment variables:

    env PORT=...              # e.g. 8000
    env SLACK_CHANNEL=...     # e.g. #random
    env SLACK_TOKEN=...       # find it in https://api.slack.com/
    env PHABRICATOR_HOST=...  # e.g. https://your.phabricator.host
    env PHABRICATOR_TOKEN=... # find it in /settings/panel/apitokens/ of your Phabricator site

### Phabricator Setup

Remember to configure Phabricator (`/config/edit/feed.http-hooks/`) so that notifications can be published to phabricator-to-slack.

## Thanks

Justin Tulloss - for him blog post ["Authenticating With Phabricator"](https://justin.harmonize.fm/development/2013/06/29/authenticating-with-phabricator.html)
