---
# Most projects come from data/projects.json. Use this only for a one-off,
# hand-written project page.
title: "{{ replace .File.ContentBaseName "-" " " | title }}"
date: {{ .Date }}
summary: ""
link: "https://{{ .File.ContentBaseName }}.hatchetlabs.com"
status: "beta"        # alpha | beta | live | archived
tags: []
draft: true
---
