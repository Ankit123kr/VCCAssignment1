# VCCAssignment1
Use VirtualBox to Create Multiple VMs, Connect These VMs, and Host One Microservice-Based Application



Prerequisites
VirtualBox installed and configured with two Virtual Machines (VMs).
Both VMs are connected to the same network for communication.

#Step 1: Verify IP Addresses of Virtual Machines

Use the following command on both VMs to check their IP addresses:

ip a | grep inet

Note the assigned IPs for use in the next steps.


#Step 2: Test Connectivity Between Virtual Machines
Ensure both VMs can communicate by pinging each other:

ping <VM2-IP>  
ping <VM1-IP>  
#Create a Python Script

nano Ankit.py

If packets are received, the VMs are successfully connected.

#Step 3: Install Python and Flask on Both VMs
Run the following on both VMs to install Python and Flask:

sudo apt update && sudo apt install -y python3 python3-pip  
pip3 install flask  

#Step 4: Create and Deploy a Flask Application on VM1
On VM1, create a new directory and navigate to it:

mkdir ~/flask_app && cd ~/flask_app
Create a Python file (app.py) and add the following code:
python
app = Flask(__name__)

@app.route('/')
def home():
    return 'Hello,This is Ankit'

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)  
Run the Flask application:

python3 Ankit.py  
Step 5: Install cURL on VM2 and Test the Microservice
On VM2, install curl if not already installed:

sudo apt install -y curl  
Use curl to test the Flask microservice running on VM1:

curl http://<VM1-IP>:5000  
If successful, it should return:

Flask microservice running on VM1!
