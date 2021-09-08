# APISIX

---

# Reload plugins

---

```shell
curl http://${APISIX_HOST}/apisix/admin/plugins/reload -H 'X-API-KEY: edd1c9f034335f136f87ad84b625c8f1pedd1c9f034335f136f87ad84b625c8f1' -X PUT
```

# OSS (1)

---

```shell
curl http://${APISIX_HOST}/apisix/admin/routes/1 -H 'X-API-KEY: edd1c9f034335f136f87ad84b625c8f1pedd1c9f034335f136f87ad84b625c8f1' -X PUT -d '
{
  "name": "oss-proxy",
  "methods": ["GET"],
  "uri": "/api/oss/*",
  "plugins": {
    "access-auth": {},
    "oss-proxy": {
      "uri_prefix": "/api/oss/"
    }
  }
}'
```

# Nacos for Discovery

---

```shell
# Desk (2)
curl http://${APISIX_HOST}/apisix/admin/routes/2 -H 'X-API-KEY: edd1c9f034335f136f87ad84b625c8f1pedd1c9f034335f136f87ad84b625c8f1' -X PUT -i -d '
{
  "name": "nacos-blade-desk",
  "uri": "/api/blade-desk/*",
  "upstream": {
    "service_name": "blade-desk",
    "type": "roundrobin",
    "discovery_type": "nacos",
    "discovery_args": {
      "namespace_id": "218688d0-cb1b-4755-9ddb-fa52a706e658"
    }
  },
  "plugins": {
    "proxy-rewrite": {
      "regex_uri": ["^/api/blade-desk/(.*)", "/$1"]
    },
    "access-auth": {}
  }
}'

# Auth (3)
curl http://${APISIX_HOST}/apisix/admin/routes/3 -H 'X-API-KEY: edd1c9f034335f136f87ad84b625c8f1pedd1c9f034335f136f87ad84b625c8f1' -X PUT -i -d '
{
  "name": "nacos-blade-auth",
  "uri": "/api/blade-auth/*",
  "upstream": {
    "service_name": "blade-auth",
    "type": "roundrobin",
    "discovery_type": "nacos",
    "discovery_args": {
      "namespace_id": "218688d0-cb1b-4755-9ddb-fa52a706e658"
    }
  },
  "plugins": {
    "proxy-rewrite": {
      "regex_uri": ["^/api/blade-auth/(.*)", "/$1"]
    },
    "access-auth": {
      "skip_urls": ["/api/blade-auth"]
    }
  }
}'

# System (4)
curl http://${APISIX_HOST}/apisix/admin/routes/4 -H 'X-API-KEY: edd1c9f034335f136f87ad84b625c8f1pedd1c9f034335f136f87ad84b625c8f1' -X PUT -i -d '
{
  "name": "nacos-blade-system",
  "uri": "/api/blade-system/*",
  "upstream": {
    "service_name": "blade-system",
    "type": "roundrobin",
    "discovery_type": "nacos",
    "discovery_args": {
      "namespace_id": "218688d0-cb1b-4755-9ddb-fa52a706e658"
    }
  },
  "plugins": {
    "proxy-rewrite": {
      "regex_uri": ["^/api/blade-system/(.*)", "/$1"]
    },
    "access-auth": {}
  }
}'

# Develop (5)
curl http://${APISIX_HOST}/apisix/admin/routes/5 -H 'X-API-KEY: edd1c9f034335f136f87ad84b625c8f1pedd1c9f034335f136f87ad84b625c8f1' -X PUT -i -d '
{
  "name": "nacos-blade-develop",
  "uri": "/api/blade-develop/*",
  "upstream": {
    "service_name": "blade-develop",
    "type": "roundrobin",
    "discovery_type": "nacos",
    "discovery_args": {
      "namespace_id": "218688d0-cb1b-4755-9ddb-fa52a706e658"
    }
  },
  "plugins": {
    "proxy-rewrite": {
      "regex_uri": ["^/api/blade-develop/(.*)", "/$1"]
    },
    "access-auth": {}
  }
}'

# Visual (6)
curl http://${APISIX_HOST}/apisix/admin/routes/6 -H 'X-API-KEY: edd1c9f034335f136f87ad84b625c8f1pedd1c9f034335f136f87ad84b625c8f1' -X PUT -i -d '
{
  "name": "nacos-blade-visual",
  "uri": "/api/blade-visual/*",
  "upstream": {
    "service_name": "blade-visual",
    "type": "roundrobin",
    "discovery_type": "nacos",
    "discovery_args": {
      "namespace_id": "218688d0-cb1b-4755-9ddb-fa52a706e658"
    }
  },
  "plugins": {
    "proxy-rewrite": {
      "regex_uri": ["^/api/blade-visual/(.*)", "/$1"]
    },
    "access-auth": {}
  }
}'

# Log (7)
curl http://${APISIX_HOST}/apisix/admin/routes/7 -H 'X-API-KEY: edd1c9f034335f136f87ad84b625c8f1pedd1c9f034335f136f87ad84b625c8f1' -X PUT -i -d '
{
  "name": "nacos-blade-log",
  "uri": "/api/blade-log/*",
  "upstream": {
    "service_name": "blade-log",
    "type": "roundrobin",
    "discovery_type": "nacos",
    "discovery_args": {
      "namespace_id": "218688d0-cb1b-4755-9ddb-fa52a706e658"
    }
  },
  "plugins": {
    "proxy-rewrite": {
      "regex_uri": ["^/api/blade-log/(.*)", "/$1"]
    },
    "access-auth": {}
  }
}'

# User (8)
curl http://${APISIX_HOST}/apisix/admin/routes/8 -H 'X-API-KEY: edd1c9f034335f136f87ad84b625c8f1pedd1c9f034335f136f87ad84b625c8f1' -X PUT -i -d '
{
  "name": "nacos-blade-user",
  "uri": "/api/blade-user/*",
  "upstream": {
    "service_name": "blade-user",
    "type": "roundrobin",
    "discovery_type": "nacos",
    "discovery_args": {
      "namespace_id": "218688d0-cb1b-4755-9ddb-fa52a706e658"
    }
  },
  "plugins": {
    "proxy-rewrite": {
      "regex_uri": ["^/api/blade-user/(.*)", "/$1"]
    },
    "access-auth": {}
  }
}'

# Resource (9)
curl http://${APISIX_HOST}/apisix/admin/routes/9 -H 'X-API-KEY: edd1c9f034335f136f87ad84b625c8f1pedd1c9f034335f136f87ad84b625c8f1' -X PUT -i -d '
{
  "name": "nacos-blade-resource",
  "uri": "/api/blade-resource/*",
  "upstream": {
    "service_name": "blade-resource",
    "type": "roundrobin",
    "discovery_type": "nacos",
    "discovery_args": {
      "namespace_id": "218688d0-cb1b-4755-9ddb-fa52a706e658"
    }
  },
  "plugins": {
    "proxy-rewrite": {
      "regex_uri": ["^/api/blade-resource/(.*)", "/$1"]
    },
    "access-auth": {}
  }
}'

# Swagger (10)
curl http://${APISIX_HOST}/apisix/admin/routes/10 -H 'X-API-KEY: edd1c9f034335f136f87ad84b625c8f1pedd1c9f034335f136f87ad84b625c8f1' -X PUT -i -d '
{
  "name": "nacos-blade-swagger",
  "uri": "/api/blade-swagger/*",
  "upstream": {
    "service_name": "blade-swagger",
    "type": "roundrobin",
    "discovery_type": "nacos",
    "discovery_args": {
      "namespace_id": "218688d0-cb1b-4755-9ddb-fa52a706e658"
    }
  },
  "plugins": {
    "proxy-rewrite": {
      "regex_uri": ["^/api/blade-swagger/(.*)", "/$1"]
    },
    "access-auth": {}
  }
}'
```
