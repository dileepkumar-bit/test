# test

# Jenkins Parallel Testing Demo

## Objective
Demonstrate how to run multiple test stages in parallel using a Jenkins Pipeline.

## Repository Structure

```
jenkins-parallel-testing-demo/
│
├── Jenkinsfile
├── README.md
│
├── app/
│   └── sample.txt
│
└── tests/
    ├── unit-test.sh
    ├── integration-test.sh
    └── ui-test.sh
```

## Pipeline Stages

1. Checkout
2. Build
3. Unit Test (Parallel)
4. Integration Test (Parallel)
5. UI Test (Parallel)
6. Deploy

## Expected Result

The three test stages run simultaneously, reducing the total pipeline execution time.
