# CI-CD-Jenkins
Includes a python program <i>snvModified.py</i> which helps in creating a generic <b>CI/CD</b> platform for the entire SCM (<u>SVN</u>) and dynamically trigger
builds for each of the modified projects.

It dynamically generates temporary properties files like <i>build0.properties, build1.properties</i> etc, each of which contain a key 'modified' which is set equal to the name of the project that was modified in the SVN repository. Ex: <b>modified=SampleApp</b>. The number of these properties files would depend on the number of projects that have been modified in our <b>SCM</b>.

For each of these properties files, we can invoke one build in Jenkins using <u>"Parametrized Build Trigger"</u> and <u>Parameter Factory: "For every property file invoke one build"</u> option.

After the parallel builds have been invoked, we delete these properties files, so that in the next poll of Jenkins, only new dynamically created files are used for triggering not the previous/old one.
