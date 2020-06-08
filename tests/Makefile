.PHONY: all syntax-check test clean

containers = apollo

clean_command = docker rm -f $(containers) > /dev/null 2>&1 || true

all: test

syntax-check:
	ansible-playbook $(PLAYBOOK).yml -i inventory --syntax-check

test: PLAYBOOK=test
test: syntax-check
	$(clean_command)
	ansible-playbook test.yml -i inventory

clean:
	$(clean_command)