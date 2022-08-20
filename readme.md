# ansible-playbook for using Remote-Container without Docker Desktop

features:

- install genie and settings.
- install docker, docker-compose.

## sample usage

simple.

    ansible-playbook -i hosts playbook.yml --connection=local --ask-become-pass

select task.

    ansible-playbook -i hosts playbook.yml --connection=local --ask-become-pass --step --start-at='foo' -vvv
