nginx-setup
=========
Install **nginx** from source on remote host.

Requirements
------------

None.

Role Variables
--------------
	
	# group
	NGINX_GROUP: nginx
	# user
	NGINX_USER: nginx
	# install path
	INSTALL_PATH: /usr/local/nginx
	# bin
	SBIN_PATH: /usr/sbin/nginx
	# conf file
	CONF_PATH: '{{INSTALL_PATH}}/conf/nginx.conf'
	# pid file 
	PID_PATH: /var/run/nginx.pid
	# lock file
	LOCK_PATH: /var/run/nginx.lock
	# error log file
	ERROR_LOG_PATH: '{{INSTALL_PATH}}/logs/error.log'
	# access log file
	ACCESS_LOG_PATH: '{{INSTALL_PATH}}/logs/access.log'
	# basic compile options
	COMPILE_BASIC_OPTIONS: '--group={{NGINX_GROUP}} --user={{NGINX_USER}} --prefix={{INSTALL_PATH}} --sbin-path={{SBIN_PATH}} --conf-path={{CONF_PATH}} --pid-path={{PID_PATH}} --lock-path={{LOCK_PATH}} --error-log-path={{ERROR_LOG_PATH}} --http-log-path={{ACCESS_LOG_PATH}}'
	# module compile options
	COMPILE_MODULE_OPTIONS: '--with-http_gzip_static_module --with-http_stub_status_module --with-http_ssl_module --with-pcre --with-file-aio --with-http_realip_module'
	# compile options
	COMPILE_OPTIONS: '{{COMPILE_BASIC_OPTIONS}} {{COMPILE_MODULE_OPTIONS}}'
	# nginx version
	NGINX_VERSION: 1.9.9
	# nginx file link
	NGINX_FILE: 'http://nginx.org/download/nginx-{{NGINX_VERSION}}.tar.gz'

Dependencies
------------

None

Example
----------------

+ The **``Playbook``** like:

		- hosts: myhost 
		  remote_user: admin 
		  sudo: yes
		  roles:
		    - {
			    role: ihaolin.nginx-setup
			    # other variables
		      }
		       		  	   
		  	   
		    
License
-------

MIT

Author Information
------------------

[haolin.h0@gmail.com](mailto:haolin.h0@gmail.com)