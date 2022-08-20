$ ansible-playbook -i hosts playbook.yml --connection=local --ask-become-pass

ansible-playbook -i hosts playbook.yml --connection=local --ask-become-pass --step --start-at='hoge1' -vvv

