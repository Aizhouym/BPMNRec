## BPMNRec Usage
- Bpstruct [the source link] (https://code.google.com/archive/p/bpstruct/wikis/CommandLineTool.wiki)

  **Command line tool**:

  BPStruct is available as a command line tool. Please download the latest` bpstruct-x.y.z.jar file` (see in featured downloads). The usage of the command line tool is proposed below.

  `Usage: java -jar bpstruct.jar [options] <inputmodel> Options: -dot : Generate DOT file -odir FILE : Output directory`

  The tool expects <inputmodel> as input parameter - a file which contains a process model serialized in JSON format (for more information on the serialization format check here). Furthermore, the tool accepts two options:

  - dot : If -dot option is specified, then no structuring takes place. Instead, the input process model is serialized in DOT (Graphviz) format.
  - odir FILE : If -odir option with FILE parameter is specified, then all the output of the tool is forwarded to the FILE folder.
Sample shell script
       - 1: `java -jar bpstruct-x.y.z.jar model.json`
       
       - 2: `java -jar bpstruct-x.y.z.jar -dot model.json `
       
       - 3: `java -jar bpstruct-x.y.z.jar -dot model.struct.json `
       
       - 4: `dot -Tpng -omodel.png model.dot `
       
       - 5: `dot -Tpng -omodel.struct.png model.struct.dot`

  At line 1, a process model in model.json gets structured; the result is serialized in model.struct.json. Both the input and the structured process model get serialized in DOT format at lines 2 and 3, respectively. Finally, visual representations of both process models are generated at lines 4 and 5 (in PNG format).


- BPMNDiffviz [the source link] (https://bitbucket.org/sivanov68/bpmndiffviz/src/master/)

  **Usage**:

  *Get Sources*: `git clone https://sivanov68@bitbucket.org/sivanov68/bpmndiffviz.git`

  *Installation*:
  
  1 Install Tomcat (tested with versions 7.0.54, 9.0.12 and 9.0.43)  (https://tomcat.apache.org/download-90.cgi)
    
  2 Install PostgreSQL with pgAdmin (tested with versions 9.1.1 and 10.16) (http://www.postgresql.org/download/)
    
    - Type `89106540101` as a password for the postgres database user during setup
      
  3 Launch pgAdmin
    
    - pgAdmin 3:

         Connect to the localhost (File -> Add server... -> Name: any_name_you_want, Host: localhost, other fields: default)

         If connection is successfully established but you do not see any servers in the list restart pgAdmin3 (looks like a bug)

         Create database "vkr"

    - pgAdmin 4:

         Click on Servers > PostgreSQL <version> > Databases and create a new database "vkr"

  4 If you want to make any changes (if you do not want then go to the next step):
    
    - Get sources of BPMNDiffViz

    - Set up database connection (BPMNDiffViz/src/main/webapp/jdbc.properties)

    - Build BPMNDiffViz.war by yourself using Maven ("mvn package" command) - You can find the instuctions for installing maven here: https://maven.apache.org/install.html

    - Get BPMNDiffViz/target/BPMNDiffViz.war

  5 Put BPMNDiffViz.war into Tomcat webapps folder (<Tomcat installation root>/webapps)

  6 Start Tomcat using shell (<Tomcat installation root>/bin/startup.bat)
   
   - If you are getting an error when tomcat can not bind to the port change it to 8081 (or any other not used port) in the <Tomcat installation root>/conf/server.xml

  7 Open browser and go to URL: http://localhost:8080/BPMNDiffViz/ (it may be another port if you changed it in the previous step)
  
  8 Create a folder for storing models and input it into the Models path field on the Settings tab


- BPMNRec --BPMNRec.ipynb
  - Firstly, set up bpstruct and download the MaxStructEvaluation dataset. Use bpstruct to convert non-structured BPMN models to structured models, obtaining the structured model's JSON files. In the BPMNRec.ipynb file, within the main function, replace Unstructured_transform.json with the JSON file obtained from the previous step.
  - Then, pass the BPMN models you want to compare to achieve distance calculation. Secondly, configure BPMNDiffviz to handle the computation for other recommendation algorithms.







