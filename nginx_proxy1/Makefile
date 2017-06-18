run:
	docker-compose up -d
clean:
	docker-compose down 
cp:
	docker cp green.html nginx_green_1:/usr/share/nginx/html/index.html
	docker cp blue.html nginx_blue_1:/usr/share/nginx/html/index.html

	docker cp blue.conf nginx_proxy_1:/etc/nginx/conf.d/blue.conf
	docker cp green.conf nginx_proxy_1:/etc/nginx/conf.d/green.conf
	docker exec -it nginx_proxy_1 nginx -s reload
bash:
	docker exec -it nginx_proxy_1 ash

test:
	curl -v -H "HOST: green.me" localhost 
	curl -H "HOST: blue.me" localhost 
