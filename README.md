# Generic CI-CD Platform Jenkins :shipit:
![Image](/Pipeline.png?raw=true "Generic CI/CD Pipeline Jenkins")
- Includes a python program <i>snvModified.py</i> which helps in creating a generic <b>CI/CD</b> platform for the entire SCM (<u>SVN</u>) and dynamically trigger builds for each of the modified projects.

- It dynamically generates temporary properties files like <i>build0.properties, build1.properties</i> etc. in Jenkins job workspace, each of which contain a key 'modified' which is set equal to the name of the project that was modified in the SVN repository. Ex: 
        
        modified=SampleApp 
                
- The number of these properties files would depend on the number of projects that have been modified in our <b>SCM</b>.

- For each of these properties files, we can invoke one build in Jenkins using <u>"Parametrized Build Trigger"</u> and <u>Parameter Factory: "For every property file invoke one build"</u> plugin.

- After the parallel builds have been invoked, we delete these properties files, so that in the next poll of Jenkins, only new dynamically created files are used for triggering not the ones we used in current build trigger.

# Usage:
        python3 svnModified.py (for Ubuntu/Linux machines)
        python svnModified.py (for Windows machines)
 You need to fill in the following variable values manually into the program:
        
        - svn_url
        - Jenkins workspace location
