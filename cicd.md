Pipeline file explanation:

```
name: Python application                        # Name of the workflow
on: [push, pull_request]                        # Trigger: Run when code is pushed or a pull request is created/updated

jobs:                                           # Define the jobs in this workflow
  build:                                        # Name of the job
    runs-on: ubuntu-latest                      # Run the job on the latest Ubuntu image machine

    steps:                                      # Define the steps of the job
      - uses: actions/checkout@v3               # Check out the repository code
      - name: Set up Python 3.8                 # Name of the Python setup step
        uses: actions/setup-python@v4           # Use the Github official Python setup action tool
        with:                                   # Provide configuration options
          python-version: 3.8                   # Install and use Python 3.8 env

      - name: Install dependencies              # Name of the dependency installation step
        run: |                                  # Run the shell commands, | means pipe, can write multiple lines of Shell script
          python -m pip install --upgrade pip   # Upgrade pip to the latest version

      - name: Run tests                         # Name of the testing step
        run: |                                  # Run the shell commands
          python -m unittest discover -s tests  # Automatically discover and run tests in the tests directory, -m means specify the module to use, -s means start-directory
```


Repo URL: https://github.com/simplesilence/github-actions-python-ci