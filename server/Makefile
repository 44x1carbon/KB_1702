.DEFAULT_GOAL := help

docker_server: docker_build docker_up

docker_clean: docker_stop docker_rm

help:
	@echo docker_build:	dockerのコンテナをビルドします
	@echo docker_up:	dockerのコンテナを立ち上げます
	@echo docker_stop:	dockerのコンテナを止めます
	@echo docker_rm:	dockerのコンテナを削除します
	@echo docker_ssh:	dockerのコンテナにsshでアクセスします
	@echo docker_restart: dockerのコンテナを再起動します

docker_build:
	docker-compose build

docker_up:
	docker-compose up

docker_stop:
	docker-compose stop

docker_restart:
	docker-compose restart

docker_rm:
	docker-compose rm

docker_ssh_api:
	docker exec -it api /bin/bash

docker_ssh_mongo:
	docker exec -it mongo /bin/bash

direnv:
	direnv allow

SERVER := "./go/src/app"

install:
	$(MAKE) -C $(SERVER) submodule
	$(MAKE) -C $(SERVER) depend
	$(MAKE) -C $(SERVER) gen

mac-install:
	which direnv || brew install direnv
	@echo 'zshならzshrcに eval "$$(direnv hook zsh)" の記述を追加してください'
	@echo 'bashならbashrcに　eval "$$(direnv hook bash)"  の記述を追加してください'
	@echo 参考URL:https://qiita.com/ngyuki/items/fda1bbf29384bef7a805

win-install:
	git clone http://github.com/zimbatm/direnv
	cd direnv
	sudo make install
	@echo bashrcに　eval "$(direnv hook bash)"  の記述を追加してください
	@echo 参考URL:https://qiita.com/ngyuki/items/fda1bbf29384bef7a805

curl:
	curl -v -X POST --header 'Content-Type: application/json' --header 'Accept: application/vnd.goa.error' 'http://localhost:8080/api/rooms' -d '{"room": {"room_id": "hdwhalndwkandla","name": "うぇいサウンド","progress": 1,"start_at": "1995-01-11T06:25:13+09:00","end_at": "1995-01-11T06:25:13+09:00","agenda": [{"id": 1,"title": "アイデア出し","goal": "アイデアを10個出す","time": 10,"start_at": "1995-01-11T06:25:13+09:00","end_at": "1995-01-11T06:25:13+09:00"},{"id": 2,"title": "アイデアを絞る","goal": "アイデdwadaアを1個に絞る","time": 10,"start_at": "1995-01-11T06:25:13+09:00","end_at": "1995-01-11T06:25:13+09:00"}]}}'

ws-install:
	go get -u github.com/raphael/wsc

ws:
	wsc ws://localhost:8080/api/rooms/ws?id=$(id)

pro-ws:
	wsc ws://blouson.tech/api/rooms/ws?id=$(id)
