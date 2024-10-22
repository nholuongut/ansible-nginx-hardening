# N ginx Hardening (Ansible Role)
![](https://i.imgur.com/waxVImv.png)
### [View all Roadmaps](https://github.com/nholuongut/all-roadmaps) &nbsp;&middot;&nbsp; [Best Practices](https://github.com/nholuongut/all-roadmaps/blob/main/public/best-practices/) &nbsp;&middot;&nbsp; [Questions](https://www.linkedin.com/in/nholuong/)
<br/>


## Requirements

* Ansible >= 2.5

## Role Variables

* [nginx_client_body_buffer_size][]
  * Default: `1k`
  * Description: Sets buffer size for reading client request body. In case the request body is larger than the buffer, the whole body or only its part is written to a temporary file.
* nginx_remove_default_site
  * Default: `true`
  * Description: Disables the default site. Set to false to enable the default site in nginx.
* [nginx_client_max_body_size][]
  * Default: `1k`
  * Description: Sets the maximum allowed size of the client request body, specified in the “Content-Length” request header field. If the size in a request exceeds the configured value, the 41
3 (Request Entity Too Large) error is returned to the client.
* [nginx_keepalive_timeout][]
  * Default: `5 5`
  * Description: The first parameter sets a timeout during which a keep-alive client connection will stay open on the server side. The zero value disables keep-alive client connections. The op
tional second parameter sets a value in the “Keep-Alive: timeout=time” response header field.
* [nginx_server_tokens][]
  * Default: `off`
  * Description: Disables emitting nginx version in error messages and in the "Server" response header field. Set to on to enable the nginx version in error messages and "Server" response head
er.
* [nginx_client_header_buffer_size][]
  * Default: `1k`
  * Description:  Sets buffer size for reading client request header. For most requests, a buffer of 1K bytes is enough.
* [nginx_large_client_header_buffers][]
  * Default: `2 1k`
  * Description: Sets the maximum number and size of buffers used for reading large client request header.
* [nginx_client_body_timeout][]
  * Default: `10`
  * Description: Defines a timeout for reading client request body.
* [nginx_client_header_timeout][]
  * Default: `10`
  * Description: Defines a timeout for reading client request header.
* [nginx_send_timeout][]
  * Default: `10`
  * Description: Sets a timeout for transmitting a response to the client.
* [nginx_limit_conn_zone][]
  * Default: `$binary_remote_addr zone=default:10m`
  * Description: Sets parameters for a shared memory zone that will keep states for various keys.
* [nginx_limit_conn][]
  * Default: `default 5`
  * Description: Sets the shared memory zone and the maximum allowed number of connections for a given key value.
* [nginx_add_header][]
  * Default: `[ "X-Frame-Options SAMEORIGIN", "X-Content-Type-Options nosniff", "X-XSS-Protection \"1; mode=block\"" ]`
  * Description:Adds the specified field to a response header provided that the response code equals 200, 201, 204, 206, 301, 302, 303, 304, or 307.
* [nginx_ssl_protocols][]
  * Default: `TLSv1.2`
  * Description: Specifies the SSL protocol which should be used.
* [nginx_ssl_ciphers][]
  * Default: *see defaults.yml*
  * Description: Specifies the TLS ciphers which should be used.
* [nginx_ssl_prefer_server_ciphers][]
  * Default: `on`
  * Description: Specifies that server ciphers should be preferred over client ciphers when using the TLS protocols. Set to false to disable it.
* [nginx_dh_size][]
  * Default: `2048`
  * Description: Specifies the length of DH parameters for EDH ciphers.

## Installation

Install the role with ansible-galaxy:

```
ansible-galaxy install dev-sec.nginx-hardening
```

## Example Playbook

    - hosts: localhost
      roles:
        - dev-sec.nginx-hardening

## Local Testing

The preferred way of locally testing the role is to use Docker. You will have to install Docker on your system. See [Get started](https://docs.docker.com/) for a Docker package suitable to for your system.

You can also use vagrant and Virtualbox or VMWare to run tests locally. You will have to install Virtualbox and Vagrant on your system. See [Vagrant Downloads](http://downloads.vagrantup.com/) for a vagrant package suitable for your system. For all our tests we use `test-kitchen`. If you are not familiar with `test-kitchen` please have a look at [their guide](http://kitchen.ci/docs/getting-started).

Next install test-kitchen:

```bash
# Install dependencies
gem install bundler
bundle install
```

### Testing with Docker

```
# fast test on one machine
bundle exec kitchen test default-ubuntu-1204

# test on all machines
bundle exec kitchen test

# for development
bundle exec kitchen create default-ubuntu-1204
bundle exec kitchen converge default-ubuntu-1204
```

### Testing with Virtualbox

```
# fast test on one machine
KITCHEN_YAML=".kitchen.vagrant.yml" bundle exec kitchen test nginx-ansible-19-ubuntu-1404

# test on all machines
KITCHEN_YAML=".kitchen.vagrant.yml" bundle exec kitchen test

# for development
KITCHEN_YAML=".kitchen.vagrant.yml" bundle exec kitchen create nginx-ansible-19-ubuntu-1404
KITCHEN_YAML=".kitchen.vagrant.yml" bundle exec kitchen converge nginx-ansible-19-ubuntu-1404
```

For more information see [test-kitchen](http://kitchen.ci/docs/getting-started)

# 🚀 I'm are always open to your feedback.  Please contact as bellow information:
### [Contact ]
* [Name: nho Luong]
* [Skype](luongutnho_skype)
* [Github](https://github.com/nholuongut/)
* [Linkedin](https://www.linkedin.com/in/nholuong/)
* [Email Address](luongutnho@hotmail.com)

![](https://i.imgur.com/waxVImv.png)
![](Donate.png)
[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/nholuong)

# License
* Nho Luong (c). All Rights Reserved.🌟