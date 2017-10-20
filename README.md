Ansible Mandrill Routes
=========
This role helps you create mandrill inbounds and routes from your account

Requirements
------------

None

Role Variables
--------------

```
Variables with defaults :
mandrill_api_version: 1.0
mandrill_api_base_url: https://mandrillapp.com/api/{{mandrill_api_version}}
mandrill_api_inbounds_url: "{{ mandrill_api_base_url }}/inbound"
mandrill_api_routes_url: "{{ mandrill_api_base_url }}/route"
mandrill_api_output_format: .json
mandrill_inbound_key_operation: present
mandrill_inbound_operation: add-domain
mandrill_inbounds_request_url: "{{ mandrill_api_inbounds_url }}/{{ mandrill_inbound_operation }}{{ mandrill_api_output_format }}"
mandrill_routes_operation: add-route
mandrill_routes_request_url: "{{ mandrill_api_routes_url }}/{{ mandrill_operation }}{{ mandrill_api_output_format }}"

Other variables :

mandrill_api_key: myApiKey # Required
mandrill_inbound_domain: example.com # the domain for which you want to create a route
mandrill_route_pattern: * # the pattern you want to use for a route
mandrill_route_url: https://example.com/webhook the url you want to redirect to
```

Dependencies
------------

None

Example Playbook
----------------

Creating a domain:

    - hosts: localhost
      roles:
        - role: mandrill_routes
          vars:
            mandrill_api_key: yourApiKey
            mandrill_inbound_domain: your_company-reply.com
            mandrill_route_pattern: *
            mandrill_route_url: https://your_company.com/webhook

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
