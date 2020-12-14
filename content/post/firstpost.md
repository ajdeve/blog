---
title: "JDBC_JPA"
date: 2020-09-15T11:30:03+00:00
weight: 1
aliases: ["/first"]
tags: ["JDBC"]
author: "Me"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
disableShare: false
cover:
    image: "<image path/url>"
    alt: "<alt text>"
    caption: "<text>"
    relative: false
comments: falsse
---

# JDBC_JPA

flush() : DB에 실제 쿼리를 날려 execute하는 기능이며 commit이 아니기에 DB에 반영이 되지 않는다. 

clear() : 영속성 컨텍스트에 저장한 데이터를 지워버린다.

commit() : DB에 저장,수정,삭제를 반영한다. 

rollback:() : DB에 저장하지 않고 영속성 컨텍스트 데이터를 날린다.
