# SIMPLE JMETER FRAMEWORK

This is a simple JMeter framework mainly constructed with:
  1) Keyword driven testing
  2) Passing test parameters from multiple property files. (property file reader)
  3) Test Fragement - this is special holder of test request and executed them only when it is called from Threadgroup.
  4) Module controller - this controller holds the commonly used test request and can be called as function to executed. example: login scenario
  5) Backendlistener - to log the performance stats and push them into influxdb(whose template is customized to store the data in much simpler format)
  <img width="500" alt="backed_listener" src="https://user-images.githubusercontent.com/44027805/98073300-72c41680-1e81-11eb-8b4e-c27cc340be4f.PNG">
  6) Grafana - monitoring solution which reads the performance stats from influxdb datasource and displays in graphical representation.
