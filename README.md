# Decentralised healthcare system using Blockchain

#Abstract 
    The adoption of Blockchain technology in the medical sector has started gaining popularity because it mitigates crucial security, privacy, and interoperability challenges. Moreover, the massive volume of data produced and exchanged via electronic health records has raised various issues concerning data ownership. Since these records are dispersed throughout multiple medical institutes, and patients have no control over their data, it is difficult to track ownership details and medical history, compromising privacy and archival of records. As a result, we designed and implemented a solution based on Blockchain, IoT and AI. The developed system can improve healthcare management by building a patient-centric model and increasing the privacy and interoperability of medical data. Along with solving the preceding issues, we have also incorporated machine learning features to monitor and predict the risk of arrhythmia and heart diseases respectively.

# System Architecture
 ![image](https://user-images.githubusercontent.com/15829308/181119082-f220e57e-099b-4457-9eca-51176388fd85.png)

# Data layer in the architecture
![image](https://user-images.githubusercontent.com/15829308/181119347-79ccc429-0688-4967-86aa-5a1d969a540f.png)

# Consent layer in the architecture
![image](https://user-images.githubusercontent.com/15829308/181119443-8a6f2787-8c83-4735-a045-5727d1c6f894.png)

# Implementation details
The implemented system is a patient-centric model that has three hospital organizations and one patient organization. Each hospital can have any number of peers; in our system, Hospital1 has one peer node, CA and the orderer node. Hospital2, Hospital3 and patientOrg have one peer node each. If the user wishes to connect to the network, he/she must first pass via the gateway, where Fabric Node SDK uses a wallet for authentication. A new user (patient/doctor) would have to send a request to the organization's admin; once the admin verifies the user (via Aadhar Card number) and accepts the request, CA would generate a new identity and assign it to the user, along with a wallet. The wallet is maintained on the backend (the wallet in our system is a hot wallet) and is used to authenticate the user whenever they reconnect to the network.
   
After getting through the gateway, the user must select a channel (ledger); in our instance, it's named DHMS. Users can connect to a chain code(smart contract) once they enter the channel. There are two chain codes, consent management and storage management. The doctor needs access from the patient for his/her EHRs, and the access can also be revoked in case of suspicious activities. 

Hence, both the chain codes have functions that are used for the tasks mentioned above. The system comprises two machine learning models for disease prediction and real-time monitoring. The doctors can feed their patient's medical history to the model via EHR to predict heart disease. For the monitoring model, an IoT device was simulated that sends annotated ECG signals to the machine learning model that predicts the risk of Arrhythmia. 

In Hyperledger Fabric docker is used in three ways, 1) At Runtime: The deployed chaincode on the Hyperledger Fabric Network is launched in an isolated docker container. 2)Architectural components of Hyperledger Fabric such as peer and orderer are made available as docker images.3) Docker compose may be used for container orchestration for setting up the Hyperledger Fabric infrastructure.
Some of the binaries in Hyperledger Fabric have built-in database, which is levelDB. It is also the default database used for implementing transaction logs and stateDB. The proposed solution uses levelDB as a state database. 

We are using Javascript for the development of chain code. fabric-contract-api and fabric-shim are the modules which are used for developing chain code within NodeJS. Along with these we have used the Stub interface, which is the main chain code interface to read and write data onto the ledger.
