
* osxの環境
* docker toolbox

==================================================================
▼ grafana
---------------------------------------------
docker run \
-d \
-p 3000:3000 \
-v /home/sitespeed/monitoring/grafana:/var/lib/grafana \
-e GF_SECURITY_ADMIN_USER=admin \
-e GF_SECURITY_ADMIN_PASSWORD=password \
--name grafana \
--restart=always \
 grafana/grafana
---------------------------------------------


mickey390/grafana





docker build -t mickey390/grafana:0.2 .


docker run -d -p 3000:3000 --restart=always mickey390/grafana:0.3


==================================================================

▼ graphite
---------------------------------------------
docker run\
-d\
--name graphite\
-p 8080:80\
-p 2003:2003\
--restart=always\
-v /home/sitespeed/monitoring/graphite/:/opt/graphite/storage/whisper\
-v /home/sitespeed/.htpasswd:/etc/nginx/.htpasswd\ 
sitespeedio/graphite
---------------------------------------------

* basic認証 Basic Auth guest/guest


docker build -t mickey390/graphite:0.1 .

docker run -d -p 8080:80 -p 2003:2003 --restart=always mickey390/graphite:0.2


http://192.168.99.100:8080/

▼ sitespeed.io
---------------------------------------------
docker run \
--privileged \
--rm \
-v /home/sitespeed/monitoring/sitespeed.io:/sitespeed.io \
sitespeedio/sitespeed.io \
sitespeed.io \
-u https://auone.jp/ \
--userAgent     " \
-b firefox \
-n 1 \
-m 1 \
--connection cable \
--graphiteHost 10.0.0.96 \
--graphiteData summary,rules,pagemetrics,timings,timings
---------------------------------------------
