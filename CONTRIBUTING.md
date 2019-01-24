# Please contribute!
You can really make a difference by:
- [Making an issue](https://help.github.com/articles/creating-an-issue/). A well described issue helps a lot.
- [Making a pull request](https://services.github.com/on-demand/github-cli/open-pull-request-github) when you see the error in code.

To test this role locally please use [Molecule](https://github.com/metacloud/molecule):
```
pip install molecule
molecule test
```

To test on Amazon EC2, configure [~/.aws/credentials](https://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/credentials.html) and `export AWS_REGION=eu-central-1` before running `molecule test --scenario-name ec2`.

Run the [ansible-galaxy](https://github.com/ansible/galaxy-lint-rules) and [robertdebock's](https://github.com/robertdebock/ansible-lint-rules) lint rules if you want your change to be merged:

```shell
git clone https://github.com/ansible/ansible-lint.git /tmp/ansible-lint
ansible-lint -r /tmp/ansible-lint/lib/ansiblelint/rules .

git clone https://github.com/robertdebock/ansible-lint /tmp/robertdebock-ansible-lint
ansible-lint -r /tmp/robertdebock-ansible-lint/rules .
```
