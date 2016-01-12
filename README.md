There is munin plugin for measure quality of your http service.

The plugin calc information from log file. Main feature of the plugin
is analyze logs records between starts this plugin and erase log after
it. It is very helpfull for save free space on disks when you have many queries.


Settings
====================

First of all, you should configure your web-server for write logs in
specific format. For example, nginx config:

log_format track_quality "$request_time $status";  
access_log  /var/log/nginx/quality_upload.log track_quality;  

The plugin allow to create separate groups of graphs for different
logs. You should use slug name at end of executable plugin name. For
example,

ln -s /usr/share/munin/plugins/http_quality http_quality_upload

Also you should specify username in plugin config file
(/etc/munin/plugin-conf.d/http_quality_upload.conf). This user must
have rights for write to log dir and log file.

Example:

[http_quality_upload]  
user root  
env.QUALITY_LOG /var/log/nginx/quality_upload.log  

As you can see, you can specify custom path to log file too.
