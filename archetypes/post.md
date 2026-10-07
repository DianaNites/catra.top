---
date: '{{ .Date }}'
draft: true
title: '{{ replace .File.ContentBaseName "-" " " | title }}'
hideSummary: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowWordCount: true

{{ $id := substr (now.UnixNano | sha1) 0 8 -}}

url: "/{{.Section | urlize}}/{{ $id }}/{{ .Name | urlize }}/"
aliases: [
    "/{{.Section | urlize}}/{{ $id }}",
]
---
