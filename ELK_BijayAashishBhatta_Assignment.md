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

  **Installing and configuring metricbeat on Server 2 (Kali Linux on Raspberry Pi 4B):**
	
	$ wget https://artifacts.elastic.co/downloads/beats/metricbeat/metricbeat-7.16.1-arm64.deb
   	$ sudo dpkg -i metricbeat-7.16.1-arm64.deb
	$ sudo vim /etc/metricbeat/metricbeat.yml

![image](https://user-images.githubusercontent.com/34814966/146139088-09dbb2bc-cf74-49a2-80ca-6aa2cfec081a.png)

	$ sudo systemctl enable metricbeat.service
	$ sudo systemctl start metricbeat.service 
	$ sudo systemctl status metricbeat.service 
	
![image](https://user-images.githubusercontent.com/34814966/146139429-704f40ac-17cf-4487-961c-60e22c5af13e.png)

	$ sudo metricbeat setup --template -E 'output.elasticsearch.hosts=["192.168.100.66:9200"]'
	$ sudo metricbeat setup -e -E output.elasticsearch.hosts=['192.168.100.66:9200'] -E setup.kibana.host=192.168.100.66:5601

![image](https://user-images.githubusercontent.com/34814966/146141272-9f634611-28e1-47cb-9039-ad4ffd0b1dbb.png)

  **Collecting metric from following sources in server1 and sending them to elasticsearch. Storing them in an index named "kali-rpi4"  
          - Memory usage 
          - Disk usage 
          - Load average :**

	$ sudo vim /etc/metricbeat/metricbeat.yml
	
![image](https://user-images.githubusercontent.com/34814966/146144672-c0155ef8-5366-47a8-934e-c41ae3f3281a.png)

![image](https://user-images.githubusercontent.com/34814966/146151003-49d03747-611f-48ad-9d43-21a304cf9317.png)

  
  
1. **Creating a dashboard in kibana and generate visual report(line graph) for Memory usage and load average of server1 with relation to time:**



2. **Generating alerts through kibana system for following thresholds - 
          - when memory usage > 80% for last 2 minutes send alert to a slack channel 
          - When Disk usage > 70% send alert to a slack channel 
          - When load average > 1 for last 2 minutes send alert to a slack channel:**
          
        
