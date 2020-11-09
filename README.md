# SIMPLE JMETER FRAMEWORK

This is a simple JMeter framework mainly constructed with:
  1) Keyword driven testing - the test suite is designed in such a way that it accept the scenario to execute as simple keyword.<br>
      example: <B>jmeter -n -t jmeter_testplan_jenkins.jmx -JuserCount=10 -Jrampup=2 -Jduration=60 -Jkeywordss=keyword1;keyword2;keyword3 -l testlog.csv </B>
  2) Passing test parameters from multiple property files. (property file reader - check the PTE.properties containing the test environment details)
  3) Test Fragement - this is special holder of test request and executed them only when it is called from Threadgroup.
  4) Backendlistener - to log the performance stats and push them into influxdb(whose template is customized to store the data in much simpler format)
  <img width="600" alt="backed_listener" src="https://user-images.githubusercontent.com/44027805/98073300-72c41680-1e81-11eb-8b4e-c27cc340be4f.PNG">
  5) Grafana - monitoring solution which reads the performance stats from influxdb datasource and displays in graphical representation.
      - Spin up your grafana server and import the dashboards<br>
        - Grafana_Dashboard_latest.json - gives insight of the overall test and transaction level.<br>
        <img width="600" alt="grafana_dashboard" src="https://user-images.githubusercontent.com/44027805/98113671-6f4e8080-1ebd-11eb-9e47-f8f277f227cc.PNG">
        - Grafana_Trend.json - gives response time trend level information of multiple builds for a given transaction<br>
        <img width="600" alt="grafana_trend" src="https://user-images.githubusercontent.com/44027805/98113058-8b055700-1ebc-11eb-88cc-90282f2251b9.PNG">
        
  This can be 
  1) easily integrated with Jenkins and can be deployed into CI/CD pipeline.(activity in progress)
  2) easily executed with jmeter docker image and can be executed
