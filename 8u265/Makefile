ZULU_VERSION=8u265

image:
	docker build --build-arg ZULU_VERSION=${ZULU_VERSION} -t distroless-zulu-openjdk:${ZULU_VERSION} .
	@echo ""
	@echo "To test the image run:"
	@echo "docker run -it --rm distroless-zulu-openjdk:${ZULU_VERSION}"

tag: image
	@echo ""
	docker tag distroless-zulu-openjdk:${ZULU_VERSION} qaware/distroless-zulu-openjdk:${ZULU_VERSION}
	docker tag distroless-zulu-openjdk:${ZULU_VERSION} qaware/distroless-zulu-openjdk:8

push: tag
	@echo ""
	docker push qaware/distroless-zulu-openjdk:${ZULU_VERSION}
	docker push qaware/distroless-zulu-openjdk:8
