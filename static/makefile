all: install build 

install:
	apt install -y npm
	# cnpm配置
	npm install -g cnpm --registry=https://registry.npm.taobao.org
	cnpm install

build:
	cnpm build

docker:
	docker-compose up -d --build