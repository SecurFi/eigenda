clean:
	rm -rf ./bin

build: clean
	# cd ../.. && make protoc
	go mod tidy
	go build -o ./bin/server ./cmd

run: build
	TRAFFIC_GENERATOR_HOSTNAME=localhost \
	TRAFFIC_GENERATOR_GRPC_PORT=32001 \
	TRAFFIC_GENERATOR_TIMEOUT=10s \
	TRAFFIC_GENERATOR_NUM_INSTANCES=1 \
	TRAFFIC_GENERATOR_REQUEST_INTERVAL=1s \
	TRAFFIC_GENERATOR_DATA_SIZE=1000 \
	TRAFFIC_GENERATOR_RANDOMIZE_BLOBS=true \
	./bin/server
