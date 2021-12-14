A.**Installing and configuring kibana and elasticsearch with basic username and password authentication on Server1 (Kubuntu 20.04 LTS):**

		$ wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
 		$ sudo apt-get install apt-transport-https
 		$ echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-7.x.list
 		$ sudo apt-get update && sudo apt-get install elasticsearch
         	$ sudo systemctl enable elasticsearch.service
		$ sudo systemctl start elasticsearch.service
		$ sudo systemctl status elasticsearch.service 
					
	![image](https://user-images.githubusercontent.com/34814966/146002609-95035a94-9a71-4712-a99e-3581e4a4ee7a.png)
					
		$ sudo apt-get update && sudo apt-get install kibana
		$ sudo systemctl enable kibana.service
		$ sudo systemctl start kibana.service
		$ sudo systemctl status kibana.service


  **installing and configuring metricbeat on Server 2 (Kali Linux on Raspberry Pi 4B):**



  **Collecting metric from following sources in server1 and sending them to elasticsearch. Storing them in an index named "server1-metrics" - 
          a. Memory usage 
          b. Disk usage 
          c. Load average :**


  
  
1. **Creating a dashboard in kibana and generate visual report(line graph) for Memory usage and load average of server1 with relation to time:**



2. **Generating alerts through kibana system for following thresholds - 
          a. when memory usage > 80% for last 2 minutes send alert to a slack channel 
          b. When Disk usage > 70% send alert to a slack channel 
          c. When load average > 1 for last 2 minutes send alert to a slack channel:**
          
        
