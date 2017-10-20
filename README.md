Ansible Mandrill Routes
=========
This role helps you create mandrill inbound routes from your account

Requirements
------------

None

Role Variables
--------------

```
Variables with defaults :
---
mandrill_api_version: 1.0
mandrill_api_routes_url: https://mandrillapp.com/api/{{mandrill_api_version}}/inbounds
mandrill_api_output_format: .json
mandrill_route_operation: present # present creates a domain, absent deletes a domain and check checks a domain
mandrill_operation: add-domain # intentionnaly set as default
mandrill_request_url: "{{ mandrill_api_routes_url }}/{{ mandrill_operation }}{{ mandrill_api_output_format }}"

Other variables :

mandrill_api_key: myApiKey # Required
mandrill_route_domain: example.com # the domain for which you want to create a route
```

Dependencies
------------

None

Example Playbook
----------------

Creating a domain route:

    - hosts: localhost
      roles:
        - role: mandrill_routes
          vars:
            mandrill_api_key: yourApiKey
            mandrill_route_domain: your_company-reply.com


Removing a domain route

    - hosts: localhost
      roles:
        - role: mandrill_routes
          vars:
            mandrill_route_operation: absent
            mandrill_api_key: yourApiKey
            mandrill_route_domain: your_company-reply.com


Checking the domain

    - hosts: localhost
      roles:
        - role: mandrill_routes
          vars:
            mandrill_route_operation: check
            mandrill_api_key: yourApiKey
            mandrill_route_domain: your_company-reply.com

License
-------

BSD

Author Information
------------------

[github.com/cdalbergue](https://github.com/cdalbergue)
