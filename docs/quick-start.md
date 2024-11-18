# Quick Start

## Quick Start

### 1) Create account & add credit <a href="#id-1-create-account" id="id-1-create-account"></a>

Before you can rent a machine on QuickPod, you will need to setup an account and add credit. Click on the Add Credit button to add credit from Stripe payment. Adding a credit card is the simplest method. Crypto payments through Coinbase are also available. You can change the amount on the stripe checkout page.

Once you spend your balance down your instances will be stopped until you add additional credits.

### 2) Set up your device for connecting to instances <a href="#id-2-set-up-your-device-for-connecting-to-instances" id="id-2-set-up-your-device-for-connecting-to-instances"></a>

We provide a convenient web-connect feature to connect to your instances, but alternative ssh connection is also available for that you need to set your public ssh key in settings page prior to creating an instance. The provided ssh feature is limited and for a full blown ssh experience with scp and sftp you will need to setup a standalone ssh server and expose the ports through -p 22:22 docker options. A prevuild template for ssh server is also available inn public templates.

### 3) Select and customize a template <a href="#id-3-select-and-customize-a-template" id="id-3-select-and-customize-a-template"></a>

A template is a definition of a docker instance and contains a docker image, related settings and a startup command

### 4) Filter machines <a href="#id-4-filter-machines" id="id-4-filter-machines"></a>

Use the filters to specify the GPU number, type and other factors such as port ranges, number of CPUs, amount of GPU ram and more. Each filter will narrow the offers displayed. If you see few or zero search results, reset your filters.

### 5) Select Storage <a href="#id-5-select-storage" id="id-5-select-storage"></a>

Make sure to use the storage slider on top of the create page to choose your storage allocation size. You can't change this after instance creation, so make sure to size correctly at start!

### 6) Rent <a href="#id-6-rent" id="id-6-rent"></a>

Hitting the blue Create POD button will accept the offer and create an instance with the specified docker image and launch mode. Once rented, the instance will appear in the Pods page.

### 7) Connecting to your POD <a href="#id-7-enjoy" id="id-7-enjoy"></a>

If the docker image is cached your POD should load in seconds, it will go through stages of downloading which can take 1 minutes to 10 minutes depending on internet speeds. After loading the instance will startup. Once the instance has started the connect status will turn green and you can click on connect and then webconnect to connect to your POD. The popup will also provide information about connecting with your ssh private keys, if you previously setup a public ssh key in settings.

Please do not click any buttons till the pod is ready for use.

### 8) Destroy <a href="#id-8-destroy" id="id-8-destroy"></a>

Make sure to destroy PODS after you are done with them. Stopping the POD will prevent GPU charges but you will still accrue charges for the POD storage allocation. Stopped PODS can be restarted if/when the GPU/CPU is available.
