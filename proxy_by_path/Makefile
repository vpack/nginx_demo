run:
	docker-compose up -d
clean:
	docker-compose down 
cp:
	docker cp green.html proxybypath_green_1:/usr/share/nginx/html/index.html
	docker cp blue.html proxybypath_blue_1:/usr/share/nginx/html/index.html
	docker cp green.html proxybypath_green_1:/usr/share/nginx/html/green.html
	docker cp blue.html proxybypath_blue_1:/usr/share/nginx/html/blue.html

	docker cp proxy.conf proxybypath_proxy_1:/etc/nginx/conf.d/proxy.conf
	docker exec -it proxybypath_proxy_1 nginx -s reload
bash:
	docker exec -it proxybypath_proxy_1 ash

test:
	curl -v -H "HOST: proxy.me" http://localhost/green/green.html
	curl -v -H "HOST: proxy.me" http://localhost/blue
	curl -v -H "HOST: proxy.me" http://localhost/blue/blue.html
