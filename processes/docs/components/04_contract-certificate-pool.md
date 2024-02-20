# Contract Certificate Pool

The CCP stores the signed contract data from the eMSPs, and provides it to the CPOs and OEMs. The CPO's backend can request a signed contract using the certificateInstallationRequest, as defined on ISO 15118-2:2014.

The CPS' signed contract data will be stored in the CCP, and assigned to their respective PCID. The CCP also enables multiple contracts storing for each PCID. 

The CCP keeps contracts of each eMSP separated. The defined access rules prevent unauthorized requests to others eMSP contracts. That means each eMSP can only manage (create/update/delete) contracts of their own company.

The Ecosystem Administration creates a node for each eMSP after the provider ID confirmation from the issuing authority.


## API

The Contract Certificate Pool offers a REST API supporting registered contract certificate requests.

All CCP API's documentation are available at [ccp.v1.json](../../../specification/apis/ccp/ccp.api.v1.json).

## Processes

The Contract Certificate Pool (CCP) is involved in multiple processes across the ecosystem. The Direct Processes are described bellow:

### 1. Publish a Contract Certificate

The Contract Certificate pool can receive contracts by two means: 
1- Contracts forwarded by the CPS 
2- Added contracts by the EMSPs

<!-- theme: info -->

> Publishing a Contract Certificate in the pool can trigger an instant push notification to the OEM enrolled in the WMI corresponding to the contract's PCID. See [Webhooks Service](./06_webhook-service.md)

### 2. Update a Contract Certificate

In case an eMSP needs to renew a Contract Certificate, they may do so by sending an updated Certificate to the pool.

The update process overwrites the existing Contract Certificate with the same EMAID.

<!-- theme: info -->

> An update of a Contract Certificate in the pool can trigger an instant push notification to the OEM enrolled in the WMI corresponding to the contract's PCID. See [Webhooks Service](./06_webhook-service.md)


### 3. Delete a Contract Certificate

In case the Contract Certificate under one EMAID needs be removed from the ecosystem, the eMSP that owns it may delete it from the pool.

<!-- theme: info -->

> A deletion of a contract certificate in the pool can trigger an instant push notification to the OEM enrolled in the WMI corresponding to the contract's PCID. See [Webhooks Service](./06_webhook-service.md)


### 4. Retrieving a Contract Certificate

In case a CPO or an OEM is requesting to get a Contract Certificate the CCP sends the contract data to the requesting endpoint.


## Data Cleansing
         
The Contract Certificate Pool should be cleaned regularly.
