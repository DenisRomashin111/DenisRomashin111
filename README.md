 checkout-enterprise:
    description: "Checkout enterprise code"
    parameters:
      destination:
        type: string
    steps:
      - add_ssh_keys:
          fingerprints:
            - "f9:49:75:1a:ad:44:89:10:4b:3c:70:70:ba:d3:c3:ce"
      - run:
          name: Checkout Enterprise
          environment:
            GIT_SSH_COMMAND: "ssh -o StrictHostKeyChecking=no"
          command: |
            mkdir -p << parameters.destination >>
            cd << parameters.destination >>
            git clone git@github.com:arangodb/enterprise.git .
            git reset --hard << pipeline.parameters.enterprise-commit >>


