# Overview

**Overview**

Quickpod is a GPU and CPU marketplace. Hosts sell GPU and CPU resources on the marketplace. Hosts are responsible for:

* Setup: installing Ubuntu, creating disk partitions, installing NVIDIA drivers, opening network ports on the router and installing the Quickpod hosting software.
* Testing and troubleshooting all issues that can arise, such as driver conflicts, errors, bad GPUs, and bad network ports.
* Managing the listings and GPU offers for rentals, including setting pricing and duration for the offers
* Planning for maintenance so that no client jobs are affected

#### Account setup and hosting agreement <a href="#account-setup-and-hosting-agreement" id="account-setup-and-hosting-agreement"></a>

You must create a new account for hosting. You can use a host account as a client account also.

By setting up a host account you agree to the hosting agreement.

#### Machine setup <a href="#machine-setup" id="machine-setup"></a>

Common issues to check:

* Make sure to test the networking. Quickpod requires open ports which are must have, without open ports your machine will be delisted.
* Make sure to disable auto-updates so that your machine doesn't drop a client job to update a driver.

Once you are ready to list your machine, come back to this guide to understand pricing and listing the rental contract.

#### General concepts <a href="#general-concepts" id="general-concepts"></a>

Clients have high expectations coming from AWS or GCP or Lambda. As a host, plan to offer 100% uptime for your machine during the contracted period. Expect that the GPU is going to be used at close to max capacity for the rental period. Ensure that your Internet, power source and heat dissipation systems are all functioning and that you have thought through how hosting will affect each one of those items.

#### Listings and Contracts <a href="#listings-and-contracts" id="listings-and-contracts"></a>

Hosts can create machine _listings_ (offers) through the GPU/CPU machine control panel GUI on the host machines page.

The main listing parameters include:

* the pricing per GPU, based on the PCie lanes please use different pricing for different level of GPUs
* the max duration which determines how long the listing lasts

The listing offer is good until the duration ends. When a client creates an instance on your machine, this creates a _contract_ from your listing.

Once you list and get rental contracts, it is very important to honor the terms of the contract until the end date.

#### The Rental Contract <a href="#the-rental-contract" id="the-rental-contract"></a>

By listing your machine or compute services, you are offering up a rental contract to potential clients.

Once a client accepts this listing, you and the client have entered into a rental agreement - a contract.

As the provider you are _promising_ to provide the services as advertised in your listing:

* the provider must provide the hardware/services according to all the advertised specs
* the hardware can not be used for any other purposes
* the client's data must be isolated and protected according to the data protection policy
* the advertised services must be provided up until the end date (contract expiration)

**Duration**

The duration determines till how long the pod contract will last, clients can terminate the pods prior to that, but when the contract duration ends the pods are stopped with no way to start

**Min GPU**

You can specify the minimum number of GPUs which will be available to the clients to rent e.g. in a 8x GPU machine min GPU of 4 will mean that only 4x and 8X offers will be available, not 1X or 2X. You may want to set this option judiciously to avail of maximum rental value.

**On-demand Price**

The on-demand price is the price per hour for the GPU rental. On demand rentals are the only kind of rentals available. Hosts can create jobs on their own machines which are interruptible.

#### Testing your own machine <a href="#testing-your-own-machine" id="testing-your-own-machine"></a>

It is vital to test your own machine to ensure the ports and software is running smoothly. You can use a job to test your own machine, the essential thing to test is the webconnect feature, which will only work if you have open ports and the range specified is correct.

#### Maintenance <a href="#maintenance" id="maintenance"></a>

The proper way to perform maintenance on your machine is to wait until all active contracts have expired or the machine is vacant.

Unlisting will prevent new contracts from starting on the machine. However if you have a current client rental, you could set the end date to the client end date to allow for other clients to create instances on that machine that expire at the same date. Once the end date is reached, you can then unlist the machine and then perform maintenance.

#### Common Questions <a href="#common-questions" id="common-questions"></a>

**How do I host my machine(s) on QuickPod? How can I rent my PC?**

Hosting on QuickPod will require some Linux knowledge, as you will be maintaining a server. But we provide active support through our discord channel.

**How do I check if my machine is listed?**

All listed machines within parameters will show up in the search console, common reasons for machine not showing up is machine is not online, the max duration is set to below 3 days which is default search, you have faulty GPU, the listed checkbox is not checked on the machines page.

**Do you have a verification process?**

Verification for ports is done by us for every listed machine and if ports are not corrected we will delist the machine since open ports is a must have for quickpod. The GPU verification is automated and a bandwidth test is run periodically if the result is FAILED the GPU will not appear in search, but the other healthy GPUs will continue to be listed.

**Why did the reliability on my machine decrease?**

If the machine loses connection or if there is a client instance that does not start the machine's reliability will drop.

**How do I minimize my reliability dropping?**

Do not take your machine offline. If you must take your machine offline, minimize the time you have it offline.
