.PHONY: test clean

containers = provision_docker_host_one

clean_command = docker rm -f $(containers) || true

all: test

test:
	$(clean_command)
	ansible-playbook test.yml -i inventory --syntax-check

clean:
	$(clean_command)