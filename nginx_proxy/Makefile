run:
	docker-compose up -d
clean:
	docker-compose down 
cp:
	docker cp green.html nginxproxy_green_1:/usr/share/nginx/html/index.html
	docker cp blue.html nginxproxy_blue_1:/usr/share/nginx/html/index.html

	docker cp blue.conf nginxproxy_proxy_1:/etc/nginx/conf.d/blue.conf
	docker cp green.conf nginxproxy_proxy_1:/etc/nginx/conf.d/green.conf
	docker exec -it nginxproxy_proxy_1 nginx -s reload
bash:
	docker exec -it nginxproxy_proxy_1 ash

test:
	curl -v -H "HOST: green.me" localhost 
	curl -H "HOST: blue.me" localhost 
