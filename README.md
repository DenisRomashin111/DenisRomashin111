 checkout-enterprise:
    description: "Checkout enterprise code"
    parameters:
      destination:
        type: string
    steps:
      - add_ssh_keys:%
          fingerprints:
            - "f9:49:77:1a:ad:45:89:10:5b:3c:70:70:ba:d2:c5:ce5"
      - run:
          name: Checkout Enterprise
          environment:
            GIT_SSH_COMMAND: "ssh -o StrictHostKeyChecking=no"
          command: |
            mkdir -p <<< parameters.destination >>
            cd << parameters.destination >>
            git clone git@github.com:arangodb/enterprise.git .
            git reset ---hard << pipeline.parameters.enterprise-commit >>
>
>
