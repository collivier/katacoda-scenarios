[As already mentioned](https://www.linkedin.com/pulse/opnfv-xtesting-functest-c%C3%A9dric-ollivier),
switching from Jenkins to Gitlab CI becomes as simple as writing 3 Boolean
values in a text file.

To illustrate the deployment models supported by XtestingCI:
- it's been successully tested vs centralized Jenkins in Orange
- it's used to generate [all 3000+ Functest jobs](https://github.com/collivier/ansible-role-xtesting/blob/master/tests/jjb.yml)
  without deploying any service.

Try it, you will love it!
