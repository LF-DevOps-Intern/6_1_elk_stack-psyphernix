A. **Installing and configuring kibana and elasticsearch with basic username and password authentication on Server1 (Kubuntu 20.04 LTS):**

	$ wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
 	$ sudo apt-get install apt-transport-https
 	$ echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-7.x.list
 	$ sudo apt-get update && sudo apt-get install elasticsearch
	$ sudo vim /etc/elasticsearch/elasticsearch.yml
	
![image](https://user-images.githubusercontent.com/34814966/146120647-128a81e0-cce2-491f-9464-318098618d52.png)

![image](https://user-images.githubusercontent.com/34814966/146120065-bb926ed9-4d2d-4ee1-bd18-56d88ab55d03.png)

	$ cd /usr/share/elasticsearch/bin/
	$ sudo ./elasticsearch-setup-passwords interactive
	
![image](https://user-images.githubusercontent.com/34814966/146123183-4339b342-3c2e-48c9-a489-dfa5a82ec7c2.png)

	$ sudo systemctl enable elasticsearch.service
	$ sudo systemctl start elasticsearch.service
	$ sudo systemctl status elasticsearch.service 
					
![image](https://user-images.githubusercontent.com/34814966/146002609-95035a94-9a71-4712-a99e-3581e4a4ee7a.png)
				
	$ sudo apt-get update && sudo apt-get install kibana
	$ sudo vim /etc/kibana/kibana.yml
	
![image](https://user-images.githubusercontent.com/34814966/146124181-e12f4210-1dc5-4d56-a290-3e8f87f61985.png)

![image](https://user-images.githubusercontent.com/34814966/146124747-2ed5d002-464c-4238-b1d2-eb356fe11f8d.png)

	$ sudo systemctl enable kibana.service
	$ sudo systemctl start kibana.service
	$ sudo systemctl status kibana.service

![image](https://user-images.githubusercontent.com/34814966/146047446-f16c0eb4-26cb-4ce5-95a5-80bd8a2f2dad.png)

  **installing and configuring metricbeat on Server 2 (Kali Linux on Raspberry Pi 4B):**
	
	$ wget https://artifacts.elastic.co/downloads/beats/metricbeat/metricbeat-7.16.1-arm64.deb
   	$ sudo dpkg -i metricbeat-7.16.1-arm64.deb
	$ 


  **Collecting metric from following sources in server1 and sending them to elasticsearch. Storing them in an index named "server1-metrics" - 
          a. Memory usage 
          b. Disk usage 
          c. Load average :**


  
  
1. **Creating a dashboard in kibana and generate visual report(line graph) for Memory usage and load average of server1 with relation to time:**



2. **Generating alerts through kibana system for following thresholds - 
          a. when memory usage > 80% for last 2 minutes send alert to a slack channel 
          b. When Disk usage > 70% send alert to a slack channel 
          c. When load average > 1 for last 2 minutes send alert to a slack channel:**
          
        
