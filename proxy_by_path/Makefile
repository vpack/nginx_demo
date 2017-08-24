PROJECT = pbp

run:
	docker-compose --project-name $(PROJECT) up -d
clean:
	docker-compose --project-name $(PROJECT) down
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
	docker ps | grep $(PROJECT)_

test:
	curl -v -H "HOST: proxy.me" http://localhost/green/green.html
	curl -v -H "HOST: proxy.me" http://localhost/blue
	curl -v -H "HOST: proxy.me" http://localhost/blue/blue.html


#####  PART 2 - updating the default.conf 

cp2:
	docker cp default.conf $(PROJECT)_proxy_1:/etc/nginx/conf.d/default.conf
	docker exec -it $(PROJECT)_proxy_1 nginx -s reload
test2:
	curl -v  http://localhost/green/green.html
	curl -v  http://localhost/blue
	curl -v  http://localhost/blue/blue.html
