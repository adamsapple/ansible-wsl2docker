# ansible-playbook for using Remote-Container without Docker Desktop

Contents.
<!-- @import "[TOC]" {cmd="toc" depthFrom=2 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [features](#features)
- [sample usage](#sample-usage)

<!-- /code_chunk_output -->

## features

- install genie and settings.
- install docker, docker-compose.

## sample usage

simple.

    ansible-playbook -i hosts playbook.yml --connection=local --ask-become-pass

select task.

    ansible-playbook -i hosts playbook.yml --connection=local --ask-become-pass --step --start-at='foo' -vvv
