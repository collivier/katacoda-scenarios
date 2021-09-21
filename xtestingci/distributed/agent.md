Jenkins agents (formely Jenkins slaves) are commonly used to share the common
builds accross multiple servers or to execute the test cases as closed as
possible from your System Under Tests (see: security, performance, etc.).

XtestingCI fully supports Jenkins agents as well as GitLab CI/CD runners:
- boot new agents
- connect them to Jenkins or to GitLab CI/CD
- configure job to run the test cases from them

Let's now reconfigure *HOST2* to also boot a new agent *myrunner* which will
execute the Xtesting sample:

```
cat << EOF >> site2.yml
    jenkins_agent_deploy: true
    jenkins_agent_name: myrunner
    use_slave: true
    docker_tags:
      - latest:
          slave: myrunner

EOF
ansible-playbook -i inventory site2.yml
```{{execute}}

Please start a new build of xtesting-latest-daily again without changing the
default parameters. Compared to the previous build, Jenkins prompts you a new
parameter *slave* and the last column higlights that the test cases are now
built on *myrunner*.

That's all folks!
