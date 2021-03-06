---
title: Release machine from isolation API
description: Use this API to create calls related to release a machine from isolation.
keywords: apis, graph api, supported apis, remove machine from isolation
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: w10
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
ms.date: 12/08/2017
---

# Release machine from isolation API

**Applies to:**

- [Windows Defender Advanced Threat Protection (Windows Defender ATP)](https://wincom.blob.core.windows.net/documents/Windows10_Commercial_Comparison.pdf)



Undo isolation of a machine.

## Permissions
Users need to have Security administrator or Global admin directory roles.

## HTTP request
```
POST /testwdatppreview/machines/{id}/unisolate
```

## Request headers

Header | Value 
:---|:---
Authorization | Bearer {token}. **Required**.
Content-Type	| application/json

## Request body
In the request body, supply a JSON object with the following parameters:

Parameter |	Type	| Description
:---|:---|:---
Comment |	String |	Comment to associate with the action. **Required**.

## Response
If successful, this method returns 201, Created response code and _MachineAction_ object in the response body.


## Example

**Request**

Here is an example of the request.

```
POST https://graph.microsoft.com/testwdatppreview/machines/fb9ab6be3965095a09c057be7c90f0a2/unisolate 
Content-type: application/json
{
  "Comment": "Unisolate machine since it was clean and validated"
}

```
**Response**

Here is an example of the response.

>[!NOTE]
>The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```
HTTP/1.1 201 Created
Content-type: application/json
{
    "@odata.context": "https://graph.microsoft.com/testwdatppreview/$metadata#MachineActions/$entity",
    "id": "09a0f91e-a2eb-409d-af33-5577fe9bd558",
    "type": "Unisolate",
    "requestor": "Analyst@ contoso.com ",
    "requestorComment": "Unisolate machine since it was clean and validated ",
    "status": "InProgress",
    "error": "None",
    "machineId": "f46b9bb259ed4a7fb9981b73510e3cc7aa81ec1f",
    "creationDateTimeUtc": "2017-12-04T12:13:15.0104931Z",
    "lastUpdateTimeUtc": "2017-12-04T12:13:15.0104931Z" 
}


```
