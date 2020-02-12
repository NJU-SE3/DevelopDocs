all: install build 

install:
	apt install yarn
	yarn config set registry https://registry.npm.taobao.org
	yarn install

build:
	yarn build

docker:
	docker-compose up -d --build