# SIMPLE JMETER FRAMEWORK

This is a simple JMeter framework mainly constructed with:
  1) Keyword driven testing
  2) Passing test parameters from multiple property files. (property file reader and check the PTE.properties and Throughput.properties)
  3) Test Fragement - this is special holder of test request and executed them only when it is called from Threadgroup.
  4) Module controller - this controller holds the commonly used test request and can be called as function to executed. example: login scenario
  5) Backendlistener - to log the performance stats and push them into influxdb(whose template is customized to store the data in much simpler format)
  <img width="500" alt="backed_listener" src="https://user-images.githubusercontent.com/44027805/98073300-72c41680-1e81-11eb-8b4e-c27cc340be4f.PNG">
  6) Grafana - monitoring solution which reads the performance stats from influxdb datasource and displays in graphical representation.
      - Spin up your grafana server and import the dashboards<br>
        - Demo_Dashboard.json - gives insight of the overall test and transaction level.<br>
        - Demo_Trend.json - gives response time trend level information of multiple builds for a given transaction<br>
        <img width="700" alt="grafana_trend" src="https://user-images.githubusercontent.com/44027805/98113058-8b055700-1ebc-11eb-88cc-90282f2251b9.PNG">
