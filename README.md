# CI-CD-Jenkins
Includes a python programming which helps in creating a generic CI/CD platform for the entire SCM (SVN) and dynamically trigger
builds for modified projects.

It dynamically generates temporary properties files, each of which contain a key 'modified' which is set equal to the name of the project that was modified in the SVN repository. Ex: modified=SampleApp.

For each of these properties files, we can invoke one build in Jenkins using Parametrized Build Trigger and Paramter Factory "For every property file invoke one build" option.
