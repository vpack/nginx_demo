PROJECT = pbp

run:
	docker-compose --project $(PROJECT) up -d
clean:
	docker-compose --project $(PROJECT) down
cp:
	docker cp green.html $(PROJECT)_green_1:/usr/share/nginx/html/index.html
	docker cp blue.html $(PROJECT)_blue_1:/usr/share/nginx/html/index.html
	docker cp green.html $(PROJECT)_green_1:/usr/share/nginx/html/green.html
	docker cp blue.html $(PROJECT)_blue_1:/usr/share/nginx/html/blue.html

	docker cp proxy.conf $(PROJECT)_proxy_1:/etc/nginx/conf.d/proxy.conf
	docker exec -it $(PROJECT)_proxy_1 nginx -s reload
bash:
	docker exec -it $(PROJECT)_proxy_1 ash
ps:
	docker ps | grep 

test:
	curl -v -H "HOST: proxy.me" http://localhost/green/green.html
	curl -v -H "HOST: proxy.me" http://localhost/blue
	curl -v -H "HOST: proxy.me" http://localhost/blue/blue.html
