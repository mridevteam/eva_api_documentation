FORMAT: 1A

# EVA-API
The following is a documentation of the available EVA (EMU) web services available for authorized consumers.  

    
#### Access Request
Access to the EVA API is controlled via the NASA NAMs authentication management system.  To request access to the EVA API:
+ [Visit NAMs workflow system](https://nams.nasa.gov)
+ Select "Your requests"
+ Submit new request for "EVA-API"
+ Select Cuong Q. Nguyen as the sponsor



## Group Components
Components within EVA are the serial and/or lot controlled EVA hardware, tools, or material instances.

**Component Models consist of**:
+ [identification data](http://docs.emuapi.apiary.io/#reference/components/component-model)
+ [attributes](http://docs.emuapi.apiary.io/#reference/components/component-model)
+ as-built [bill](http://docs.emuapi.apiary.io/#reference/components/bill-collection) of assembly
+ associated [documents](http://docs.emuapi.apiary.io/#reference/documents/document-model)
+ [limited life](http://docs.emuapi.apiary.io/#reference/components/limited-life-collection) items
+ [calibrations](http://docs.emuapi.apiary.io/#reference/components/calibrations-collection)
+ [events](http://docs.emuapi.apiary.io/#reference/components/event-collection)
+ [transactions](http://docs.emuapi.apiary.io/#reference/components/transactions-collection)
+ [audit](http://docs.emuapi.apiary.io/#reference/components/audit-model) data


Components are the functional instances of their parent [Master](http://docs.emuapi.apiary.io/#reference/masters/master-model).

### Component Model [/component/{id}]
    
A **Component** model has the following properties:

+ **id** - *number* - The ESOC model id **(primary key, unique)**
+ **tracerNumber** - *string* - The SARAH component id **(primary key, unique)**
+ **tracerControlId** - *string* - The SARAH tracerControlId  **(primary key SARAH, unique)**
+ **masterId** - *number* - The ESOC master id of the component's parent **(fk, unique)**
+ **itemNumber** - *string* - The SARAH master id of the component's parent **(fk SARAH, unique)**
+ **description** - *string* - The description of the component.
+ **drawingNumber** - *string* - The drawing number of the component.
+ **serialNumber** - *string* - The serial number of the component.
+ **lotNumber** - *string* - The lot number of the component.
+ **side** - *string* - The side of the component.
+ **itemSize** - *string* - The size of the component.
+ **lastUpdatedDate** - *string* - Last update date.
+ **attributes** - *object* - The component's attributes
    + **birthDate** - *date* - The date the component was fabricated/built/manufactured/assembled.
    + **openDate** - *date* - The date this record was initiated.  Used as the acquired date in 1018 reporting
    + **cost** - *number* - The current cost of the component.  
    + **jscTag** - *string* - A bar code tag that was applied to JSC property.
    + **dimension** - *number* - Actual measurements of hardware.
    + **calibrationNumber** - *string* - Unique tag number assigned to identify a GSE calibrated component. 
    + **firstUsedDate** - *date* - The date the component was first put into operation.
    + **asdesignNumber** - *string* - The highest configuration to which the hardware is authorized to be built/designed.
    + **shelfLifeChanges** - *number* - Number of times the Shelf Life expiration or Usage Life expiration of this item has been extended.
    + **fepcTag** - *string* - A bar code tag that was applied to property under the contract (original FEPC then FCE and now ESOC).
    + **cabinet** - *string* - The number of the Quality Records Center (QRC) cabinet in which the data pack for this item is kept.
    + **shelf** - *string* - The shelf in the record center cabinet where the data pack for this component will be stored (see cabinet).
    + **remarks** - *string* - Any additional information pertaining to this component that would be useful to the user.
    + **installCost** - *number* - Any cost associated with the installation of the component.
    + **isEstimatedCost** - *bool* - Flags if entered costs are estimates. 
    + **fscm** - *string* - The Federal Supply Code for Manufacturers.
    + **acquired** - *string* - This how the component was acquired / received into the responsibility of the contract and is either Capital Acquired Property (CAP) or Government Furnished Property (GFP).
    + **extendedAsbuilt** - *string* - Used for Vendor supplied components that have an asbuilt number greater than the 5 characters that asbuiltNumber supports.
    + **asbuiltStatus** - *string* - The status of an asbuilt bill of material for this component.
    + **companyTag** - *string* - A unique character-string identifying an item as company property.
    + **excessConditionCode** - *string* - Code used to indicate the condition of the component being excessed / shipped.
    + **dateLastPmrutReport** - *string* - The date on which the item was last reported on a PMRUT (Item Utilization) report.
    + **manufacturedDate** - *date* - Date that an component was manufactured.
    + **manufacturedLotNumber** - *string* - The manufacturer’s lot number.
    + **acquiredCost** - *number* - The cost of the component at time of acquisition for all property not classified as material.  Also used during receiving process for non-serial / non-lot controlled material to store the receiving cost.
    + **acquiredDate** - *string* - The date the component was acquired.
    + **acquiredDocumentNumber** - *string* - The document number on which the component was acquired.
    + **acquiredDocumentLineNumber** - *number* - The line number of the document on which the component was acquired.
    + **manufacturersItemNumber** - *string* - The manufacturers item number for the component.
    + **manufacturersName** - *string* - Name of the component’s manufacturer.
    + **tracerControlNumber** - *string* - Unique non-intelligent code which has a 1-to-1 correspondence with a tracer and can be used in lieu of a tracer for applications requiring use of a bar-code to identify an item.
    + **last911TagDate** - *date* - The last date a bar-coded 911 tag was printed for this component.
    + **last1106TagDate** - *date* - The last date a bar-coded 1106 tag was printed for this component.
    + **isSuspendedShelfLife** - *bool* - Flag indicating whether the shelf life of the component has been suspended.
    + **excludeEmail** - *bool* - Flag indicating whether the component should be excluded from limited life email notifications.
    
+ **bill** - *arrry[object]* - The component's as-built bill of material assembly
    > [*Bill model*](http://docs.emuapi.apiary.io/#reference/components/bill-model)
+ **documents** - *array[object]* - The component's associated documents
    > [*Subset of a Document model*](http://docs.emuapi.apiary.io/#reference/components/document-model)
+ **limitedlife** - *object* - The component's limited life information
    > [*Limited Life model*](http://docs.emuapi.apiary.io/#reference/components/limited-life-model)
+ **calibrations** - *object* - The component's calibration data.
    > [*Calibration model*](http://docs.emuapi.apiary.io/#reference/components/calibration-model)
+ **events** - *array[object]* - The component's associated events
    > [*Subset of a  Event model*](http://docs.emuapi.apiary.io/#reference/components/event-model)
+ **transactions** - *array[object]* - The component's associated transactions
    > [*Transaction model*](http://docs.emuapi.apiary.io/#reference/components/event-model)
+ **audit** - *object* - The component's auditable history items
    > [*Audit model*](http://docs.emuapi.apiary.io/#reference/components/audit-model)
    
    
+ Parameters
    + id: 1 (required, number) - ID of the desired component
    
### Get Component Model by componentId [GET]

    URL
    /component/{id}
    
    PARAMETERS
    id: component's NEDi model id

+ Response 200 (application/json)

        {
            "id": 1,
            "tracerNumber": "12345abcdef",
            "tracerControlId": "abc1",
            "masterId": 1,
            "itemNumber": "SVG1235",
            "description": "EMU GLOVE",
            "drawingNumber": "1234Draw",
            "serialNumber": "3001",
            "lotNumber": null,
            "side": "right",
            "itemSize": "YG"
            "lastUpdateDate": '01-01-2015',
            "attributes": {
                "birthDate": 01-01-2015,
                "inactiveDate": null,
                "cost": "600.00",
                "jscTag": "jsc1234,
                "dimension" 2.6",
                "asBuiltNumber": 301,
                "calibrationNumber": "CAL1234",
                "firstUsedDate": 01-30-2015,
                "asDesignNumber": "201ABC",
                "shelfLifeChanges" 1,
                "fepcTag": "123fepc",
                "cabinet": "cab124",
                "shelf": "2A",
                "remarks": "Some additional remark.",
                "installCost": "80.00",
                "isEstimatedCost": true,
                "fscm": "123ABC",
                "acquired": "fabricated",
                "extendedAsBuilt: "10112",
                "asBuiltStatus": "complete",
                "companyTag": "LC 420536",
                "excessConditionCode": "USABLE",
                "manufacturedDate": 01-01-2015,
                "dateLastPmrutReport": 01-20-2015,
                "manufacturedLotNumber": "RECV",
                "acquiredCost": "300.00",
                "acquiredDate": "01-05-2015",
                "acquiredDocumentNumber": "C6-344-005"
                "acquiredDocumentLineNumber": "1",
                "manufacturersName": "COLLIN ELECTRONICS",
                "tracerControlNumber": "ASRK",
                "last911TagDate": 02-01-2015,
                "last1106TagDate": 02-01-2015,
                "isSupsendShelfLife": false,
                "excludeEmail": false,
                "createdBy": "CJESTES",
                "createdDate": 01-01-2015,
                "closedDate": 01-30-2015,
                "closedBy": "MFIELDEN"
            },
            "bill": {
                "children": [{
                    "id": 2,
                    "tracer": "2345zabc",
                    "masterId": 2,
                    "itemNumber": "1234ITEM",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678",
                    "serialNumber": "3001",
                    "lotNumber": null,
                    "side": null,
                    "itemSize": "YG",
                    "isParent": true
                }, {
                    "id": 3,
                    "tracer": "0001ABC",
                    "masterId": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123",
                    "serialNumber": "3001",
                    "lotNumber": null,
                    "side": null,
                    "itemSize": "YG",
                    "isParent": true
                }],
                "parent": {
                    "id": 1,
                    "tracer": "12345abcdef",
                    "masterId": 1,
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123",
                    "serialNumber": "3001",
                    "lotNumber": null,
                    "side": null,
                    "itemSize": "YG"
                    "isParent": false
                }
            },
            "documents": [{
                "id": 1,
                "sarahDocumentId": "WAIVER-1234",
                "type": "WAIVER",
                "openDate": 01-01-2014,
                "closeDate": 02-01-2015,
                "title": "EMU Waiver for CR 1234",
                "comments": "This is a comment on a WAIVER.  More comments are also included.",
            }, {
                "id": 1,
                "sarahDocumentId": "WAIVER-56789",
                "type": "WAIVER",
                "openDate": 01-01-2014,
                "closeDate": 02-01-2015,
                "title": "EMU Waiver for CR 56789",
                "comments": "This is a comment on a WAIVER.  More comments are also included.",
            }]
            "limitedLife": [{
                "id": 1,
                "componentId": 1
                "attributes": {
                    "type": "date",
                    "name": "shelfLifeExpirationDate",
                    "description": "The component's shelf life expiration date",
                    "value": "01-01-2014",
                    "requirement": {
                        "unit": "days",
                        "value": "365",
                        "description": "365 days from the component's birth date"
                    }
            }, {
                "id": 1,
                "componentId": 1
                "attributes": {
                    "type": "number",
                    "name": "maxtoolImmersions",
                    "description": "The component's total immersion count",
                    "value": "5",
                    "requirement": {
                        "unit": "number",
                        "value": "100",
                        "description": "100 Total tool immersions"
                    }
                }
            }],
            "calibrations": [{
                "id": 1,
                "componentId": 1
                "attributes": [{
                    "type": "number",
                    "name": "Some Setting",
                    "description": "The component's calibration setting for something",
                    "value": "1.0"
                }]
            }, 
            {
                "id": 2,
                "componentId": 1
                "attributes": {
                    "type": "string",
                    "name": "Some Other Setting",
                    "description": "The component's calibration setting for something else",
                    "value": "1ABC"
                }
            }],
            "events": [{
                "id": 1,
                "eventTag": "1234Event",
                "hardwareListNumber": 1234ABC,
                "type": "EVA",
                "flight" null,
                "crewMember": {
                    "id": 1,
                    "crewId": "1234ABC,
                    "firstName": "Collin",
                    "lastName": "Estes",
                    "middelInitial": "J",
                    "nasaInitials": "CJE",
                    "sex": "male",
                    "type": "astronaut",
                    "isActive": true
                }
                "status": "active",
                "audit": {}
            }, {
                "id": 1,
                "eventTag": "1234Event",
                "hardwareListNumber": 1234ABC,
                "type": "EVA",
                "flight" null,
                "crewMember": {
                    "id": 1,
                    "crewId": "1234ABC,
                    "firstName": "Collin",
                    "lastName": "Estes",
                    "middelInitial": "J",
                    "nasaInitials": "CJE",
                    "sex": "male",
                    "type": "astronaut",
                    "isActive": true
                }
                "status": "active",
                "audit": {}
            }],
            "transactions": [{
                "id": 1,
                "type": "location",
                "date": 01-15-2015,
                "attributes": { }
            }, {
                "id": 1,
                "type": "location",
                "date": 01-15-2015,
                "attributes": { }
            }],
            "audit": [{
                "lastUpdatedBy": "MFIELDEN",
                "lastUpdatedDate": 01-30-2015,
                "description": "Created Item"
            }, {
                "lastUpdatedBy": "CJESTES",
                "lastUpdatedDate": 02-15-2015,
                "description": "Updated Item"
            }]
        }
 
### Get Component Model by tracerControlId [GET /component?tracercontrolid=123]

 URL
 /component/{?tracerControlId}
    
 PARAMETERS
 tracerControlId: component's unique identifier stored in SARAH
    
+ Response 200 (application/json)
    
        {
           "id": 1,
            "tracerNumber": "12345abcdef",
            "tracerControlId": "abc1",
            "masterId": 1,
            "itemNumber": "SVG1235",
            "description": "EMU GLOVE",
            "drawingNumber": "1234Draw",
            "serialNumber": "3001",
            "lotNumber": null,
            "side": "right",
            "itemSize": "YG" 
        }
        
### Component Collection [/components(?since)]

+ Parameters
    + since: 01/01/2014 (optional, date) - Only return records that have been updated since the parameter.
    
#### Get Components Collection [GET]
 
    URL
    /components
    
    QUERY STRING OPTIONS
    since:  Only return records that have been updated since the parameter
    
+ Response 200 (application/json)

        [{
            "id": 1,
            "tracerNumber": "12345abcdef",
            "tracerControlId": "abc1",
            "masterId": 1,
            "itemNumber": "SVG1235",
            "description": "EMU GLOVE",
            "drawingNumber": "1234Draw",
            "serialNumber": "3001",
            "lotNumber": null,
            "side": "right",
            "itemSize": "YG"
            "attributes": {
                "birthDate": 01-01-2015,
                "inactiveDate": null,
                "cost": "600.00",
                "jscTag": "jsc1234,
                "dimension" 2.6",
                "asBuiltNumber": 301,
                "calibrationNumber": "CAL1234",
                "firstUsedDate": 01-30-2015,
                "asDesignNumber": "201ABC",
                "shelfLifeChanges" 1,
                "fepcTag": "123fepc",
                "cabinet": "cab124",
                "shelf": "2A",
                "remarks": "Some additional remark.",
                "installCost": "80.00",
                "isEstimatedCost": true,
                "fscm": "123ABC",
                "acquired": "fabricated",
                "extendedAsBuilt: "10112",
                "asBuiltStatus": "complete",
                "companyTag": "LC 420536",
                "excessConditionCode": "USABLE",
                "manufacturedDate": 01-01-2015,
                "dateLastPmrutReport": 01-20-2015,
                "manufacturedLotNumber": "RECV",
                "acquiredCost": "300.00",
                "acquiredDate": "01-05-2015",
                "acquiredDocumentNumber": "C6-344-005"
                "acquiredDocumentLineNumber": "1",
                "manufacturersName": "COLLIN ELECTRONICS",
                "tracerControlNumber": "ASRK",
                "last911TagDate": 02-01-2015,
                "last1106TagDate": 02-01-2015,
                "isSupsendShelfLife": false,
                "excludeEmail": false
            },
            "bill": {
                "children": [{
                    "id": 2,
                    "tracerNumber": "2345zabc",
                    "tracerControlId": "ab2a",
                    "masterId": 2,
                    "itemNumber": "1234ITEM",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678",
                    "serialNumber": "3001",
                    "lotNumber": null,
                    "side": null
                    "itemSize": "YG",
                    "isParent": true
                }, {
                    "id": 3,
                    "tracerNumber": "0001ABC",
                    "tracerControlId": "ab2b",
                    "masterId": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123",
                    "serialNumber": "3001",
                    "lotNumber": null,
                    "side": null
                    "itemSize": "YG",
                    "isParent": true
                }],
                "parent": {
                    "id": 1,
                    "tracerNumber": "12345abcdef",
                    "tracerControlId": "ab2c",
                    "masterId": 1,
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123",
                    "serialNumber": "3001",
                    "lotNumber": null,
                    "side": null
                    "itemSize": "YG",
                    "isParent": false
                }
            },
            "documents": [{
                "id": 1,
                "sarahDocumentId": "WAIVER-1234",
                "type": "WAIVER",
                "openDate": 01-01-2014,
                "closeDate": 02-01-2015,
                "title": "EMU Waiver for CR 1234",
                "comments": "This is a comment on a WAIVER.  More comments are also included.",
            }, {
                "id": 1,
                "sarahDocumentId": "WAIVER-56789",
                "type": "WAIVER",
                "openDate": 01-01-2014,
                "closeDate": 02-01-2015,
                "title": "EMU Waiver for CR 56789",
                "comments": "This is a comment on a WAIVER.  More comments are also included.",
            }]
            "limitedLife": [{
                "id": 1,
                "componentId": 1
                "attributes": {
                    "type": "date",
                    "name": "shelfLifeExpirationDate",
                    "description": "The component's shelf life expiration date",
                    "value": "01-01-2014",
                    "requirement": {
                        "unit": "days",
                        "value": "365",
                        "description": "365 days from the component's birth date"
                    }
            }, {
                "id": 1,
                "componentId": 1
                "attributes": {
                    "type": "number",
                    "name": "maxtoolImmersions",
                    "description": "The component's total immersion count",
                    "value": "5",
                    "requirement": {
                        "unit": "number",
                        "value": "100",
                        "description": "100 Total tool immersions"
                    }
                }
            }],
            "calibrations": [{
                "id": 1,
                "componentId": 1
                "attributes": [{
                    "type": "number",
                    "name": "Some Setting",
                    "description": "The component's calibration setting for something",
                    "value": "1.0"
                }]
            }, 
            {
                "id": 2,
                "componentId": 1
                "attributes": {
                    "type": "string",
                    "name": "Some Other Setting",
                    "description": "The component's calibration setting for something else",
                    "value": "1ABC"
                }
            }],
            "events": [{
                "id": 1,
                "eventTag": "1234Event",
                "hardwareListNumber": 1234ABC,
                "type": "EVA",
                "flight" null,
                "crewMember": {
                    "id": 1,
                    "crewId": "1234ABC,
                    "firstName": "Collin",
                    "lastName": "Estes",
                    "middelInitial": "J",
                    "nasaInitials": "CJE",
                    "sex": "male",
                    "type": "astronaut",
                    "isActive": true
                }
                "status": "active",
                "audit": {}
            }, {
                "id": 1,
                "eventTag": "1234Event",
                "hardwareListNumber": 1234ABC,
                "type": "EVA",
                "flight" null,
                "crewMember": {
                    "id": 1,
                    "crewId": "1234ABC,
                    "firstName": "Collin",
                    "lastName": "Estes",
                    "middelInitial": "J",
                    "nasaInitials": "CJE",
                    "sex": "male",
                    "type": "astronaut",
                    "isActive": true
                }
                "status": "active",
                "audit": {}
            }],
            "transactions": [{
                "id": 1,
                "type": "location",
                "date": 01-15-2015,
                "attributes": { }
            }, {
                "id": 1,
                "type": "location",
                "date": 01-15-2015,
                "attributes": { }
            }],
            "audit": {
                "createdBy": "CJESTES",
                "createdDate": 01-01-2015,
                "closedDate": 01-30-2015,
                "closedBy": "MFIELDEN",
                "lastUpdatedBy": "MFIELDEN"
                "lastUpdatedDate": 01-30-2015
            }
        }, {
            "id": 2,
            "tracerNumber": "09877abcdef",
            "tracerControlId": "abc1",
            "masterId": 2,
            "itemNumber": "SVG9876",
            "description": "EMU ARM",
            "drawingNumber": "Draw98765",
            "serialNumber": "3001",
            "lotNumber": null,
            "side": "right",
            "itemSize": "YG"
            "attributes": {
                "birthDate": 01-01-2015,
                "inactiveDate": null,
                "cost": "600.00",
                "jscTag": "jsc1234,
                "dimension" 2.6",
                "asBuiltNumber": 301,
                "calibrationNumber": "CAL1234",
                "firstUsedDate": 01-30-2015,
                "asDesignNumber": "201ABC",
                "shelfLifeChanges" 1,
                "fepcTag": "123fepc",
                "cabinet": "cab124",
                "shelf": "2A",
                "remarks": "Some additional remark.",
                "installCost": "80.00",
                "isEstimatedCost": true,
                "fscm": "123ABC",
                "acquired": "fabricated",
                "extendedAsBuilt: "10112",
                "asBuiltStatus": "complete",
                "companyTag": "LC 420536",
                "excessConditionCode": "USABLE",
                "manufacturedDate": 01-01-2015,
                "dateLastPmrutReport": 01-20-2015,
                "manufacturedLotNumber": "RECV",
                "acquiredCost": "300.00",
                "acquiredDate": "01-05-2015",
                "acquiredDocumentNumber": "C6-344-005"
                "acquiredDocumentLineNumber": "1",
                "manufacturersName": "COLLIN ELECTRONICS",
                "tracerControlNumber": "ASRK",
                "last911TagDate": 02-01-2015,
                "last1106TagDate": 02-01-2015,
                "isSupsendShelfLife": false,
                "excludeEmail": false
            },
            "bill": {
                "children": [{
                    "id": 2,
                    "tracerNumber": "2345zabc",
                    "tracerControlId": "ab2b",
                    "masterId": 2,
                    "itemNumber": "1234ITEM",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678",
                    "serialNumber": "3001",
                    "lotNumber": null,
                    "side": null,
                    "itemSize": "YG",
                    "isParent": true
                }, {
                    "id": 3,
                    "tracerNumber": "0001ABC",
                    "tracerControlId": "ab2c",
                    "masterId": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123",
                    "serialNumber": "3001",
                    "lotNumber": null,
                    "side": null,
                    "itemSize": "YG",
                    "isParent": true
                }],
                "parent": {
                    "id": 1,
                    "tracerNumber": "12345abcdef",
                    "tracerControlId": "ab2d",
                    "masterId": 1,
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123",
                    "serialNumber": "3001",
                    "lotNumber": null,
                    "side": null,
                    "itemSize": "YG",
                    "isParent": false
                }
            },
            "documents": [{
                "id": 1,
                "sarahDocumentId": "WAIVER-1234",
                "type": "WAIVER",
                "openDate": 01-01-2014,
                "closeDate": 02-01-2015,
                "title": "EMU Waiver for CR 1234",
                "comments": "This is a comment on a WAIVER.  More comments are also included.",
            }, {
                "id": 1,
                "sarahDocumentId": "WAIVER-56789",
                "type": "WAIVER",
                "openDate": 01-01-2014,
                "closeDate": 02-01-2015,
                "title": "EMU Waiver for CR 56789",
                "comments": "This is a comment on a WAIVER.  More comments are also included.",
            }]
            "limitedLife": [{
                "id": 1,
                "componentId": 1
                "attributes": {
                    "type": "date",
                    "name": "shelfLifeExpirationDate",
                    "description": "The component's shelf life expiration date",
                    "value": "01-01-2014",
                    "requirement": {
                        "unit": "days",
                        "value": "365",
                        "description": "365 days from the component's birth date"
                    }
            }, {
                "id": 1,
                "componentId": 1
                "attributes": {
                    "type": "number",
                    "name": "maxtoolImmersions",
                    "description": "The component's total immersion count",
                    "value": "5",
                    "requirement": {
                        "unit": "number",
                        "value": "100",
                        "description": "100 Total tool immersions"
                    }
                }
            }],
            "calibrations": [{
                "id": 1,
                "componentId": 1
                "attributes": [{
                    "type": "number",
                    "name": "Some Setting",
                    "description": "The component's calibration setting for something",
                    "value": "1.0"
                }]
            }, 
            {
                "id": 2,
                "componentId": 1
                "attributes": {
                    "type": "string",
                    "name": "Some Other Setting",
                    "description": "The component's calibration setting for something else",
                    "value": "1ABC"
                }
            }],
            "events": [{
                "id": 1,
                "eventTag": "1234Event",
                "hardwareListNumber": 1234ABC,
                "type": "EVA",
                "flight" null,
                "crewMember": {
                    "id": 1,
                    "crewId": "1234ABC,
                    "firstName": "Collin",
                    "lastName": "Estes",
                    "middelInitial": "J",
                    "nasaInitials": "CJE",
                    "sex": "male",
                    "type": "astronaut",
                    "isActive": true
                }
                "status": "active",
                "audit": {}
            }, {
                "id": 1,
                "eventTag": "1234Event",
                "hardwareListNumber": 1234ABC,
                "type": "EVA",
                "flight" null,
                "crewMember": {
                    "id": 1,
                    "crewId": "1234ABC,
                    "firstName": "Collin",
                    "lastName": "Estes",
                    "middelInitial": "J",
                    "nasaInitials": "CJE",
                    "sex": "male",
                    "type": "astronaut",
                    "isActive": true
                }
                "status": "active",
                "audit": {}
            }],
            "transactions": [{
                "id": 1,
                "type": "location",
                "date": 01-15-2015,
                "attributes": { }
            }, {
                "id": 1,
                "type": "location",
                "date": 01-15-2015,
                "attributes": { }
            }],
             "audit": [{
                "lastUpdatedBy": "MFIELDEN",
                "lastUpdatedDate": 01-30-2015,
                "description": "Created Item"
            }, {
                "lastUpdatedBy": "CJESTES",
                "lastUpdatedDate": 02-15-2015,
                "description": "Updated Item"
            }]
        }]
        
### Limited Life [/component/limitedlife{?tracercontrolid}] 

A component's **Limited life** Model has the following properties:

+ **tracerNumber** - *string* - The SARAH component id **(primary key, unique)**
+ **tracerControlId** - *string* - The SARAH tracerControlId  **(primary key SARAH, unique)**
+ **shelfLifeDueDate** - *date*
+ **usageLifeDueDate** - *date*
+ **operationLife** - *string*
+ **nextGroundServiceDate** - *date*
+ **operationLifeDueDate** - *date*
+ **onOrbitServiceExpDueDate** - *date*
+ **onOrbitServiceDueDate** - *date*
+ **evaServiceCount** - *number*
+ **evasRemainingCount** - *number*
+ **mannedSublimatorTotalTime** - *string*
+ **mannedCumulativeTotalTime** - *string*
+ **remainingCycleCount** - *number*
+ **cumulativeTime** - *string*
+ **remainingTime** - *string*
+ **lastUpdatedDate** - *string*

### Get Limited Life Model [GET]

URL
/component/limitedlife{?tracercontrolid}

+ Response 200 (application/json)

        {
            "tracerNumber": '123454qe',
            "tracerControlId": '1bc2',
            "shelfLifeDueDate": '01-01-1970',
            "usageLifeDueDate": '01-01-1970',
            "operationLife": '12',
            "nextGroundServiceDate": '01-01-1970',
            "operationLifeDueDate": '01-01-1970',
            "onOrbitServiceExpDueDate": '01-01-1970',
            "onOrbitServiceDueDate": '01-01-1970',
            "evaServiceCount": 5,
            "evasRemainingCount": 4,
            "mannedSublimatorTotalTime": '2:10',
            "mannedCumulativeTotalTime": '1:10',
            "remainingCycleCount": 1,
            "cumulativeTime": '54',
            "remainingTime": '44',
            "lastUpdateDate": '01-01-1970'
        }
        
### Bill Model [/component/bill{?tracercontrolid}]

A component's **bill** Model has been flattened to include all components on the **bill**
The ComponentBillModel is identical to the [ComponentModel](http://docs.emuapi.apiary.io/#reference/components/component-model).

+ **id** - *number* - The ESOC model id **(primary key, unique)**
+ **componentId** - *number* - The SARAH component id **(primary key, unique)**
+ **tracerNumber** - *string* - The SARAH component id **(primary key, unique)**
+ **tracerControlId** - *string* - The SARAH tracerControlId  **(primary key SARAH, unique)**
+ **parentId** - *number* - **(fk, unique)**
+ **parentTracerNumber** - *string* - **(fk SARAH, unique)**
+ **parentTracerControlId** - *string* 
+ **masterId** - *string* 
+ **itemNumber** - *string*
+ **description** - *string* 
+ **drawingNumber** - *string* 
+ **serialNumber** - *string*
+ **lotNumber** - *string*
+ **side** - *string*
+ **size** - *string*
+ **quantityPer** - *string*
+ **isParent** - *string*
+ **lastUpdatedDate** - *string*

### Get Bill Model [GET]

URL
/component/bill{?tracercontrolid}
    
+ Response 200 (application/json)
        
        {   "id": 1,
            "componentId": 2,
            "tracerNumber": "asfdsadf",
            "tracerControlId": 'av2c',
            "parentId": 1,
            "parentTraceNumber": '123423',
            "parentTracerControlId": 'abev',
            "masterId": '',
            "itemNumber": 'adfasf',
            "description": "this is a description",
            "drawingNumber": '23413214ds',
            "serialNumber": '1234',
            "lotNumber": '1',
            "side": 'L',
            "size": 'XL',
            "quantityPer": '2',
            "isParent": true,
            "lastUpdateDate": '01-01-1970'
        }

### Calibrations Collection [/component/{id}/calibrations]

A component's **calibration** Model has the following properties:

+ **id** - *number* - The NEDi Model id **(primary key, unique)**.
+ **componentId** - *number* - The NEDi Model component id **(foreign key, unique)**.
+ **attributes** - *array[object]* - An array of the limited life attributes for the component
    + **type** - *string* - The type of calibration.
    > available types: TODO:  DETERMINE TYPES.
    + **name** - *string* - The name of the calibration attribute.
    + **description** - *string* - A description of the calibration attribute.
    + **value** - *string* - The value of the limited life requirement, all converted to a string
    > values could be: TODO: DETERMINE TYPES. 

+ Parameters
    + id: 1 (required, number) - ID of the desired component
    
#### Get Component's Calibration Collection [GET]
    
    URL
    /component/{id}/calibrations
    
    PARAMETERS
    id: component's NEDi model id or component's tracer id from SARAH

+ Response 200 (application/json)

        [{
            "id": 1,
            "componentId": 1
            "attributes": [{
                "type": "number",
                "name": "Some Setting",
                "description": "The component's calibration setting for something",
                "value": "1.0"
            }]
        }, 
        {
            "id": 2,
            "componentId": 1
            "attributes": [{
                "type": "string",
                "name": "Some Other Setting",
                "description": "The component's calibration setting for something else",
                "value": "1ABC"
            }]
        }]
        
### Event Collection [/component/{id}/events(?since)]

A component's **Event** Model is a subset of the full [*Event model*](http://docs.emuapi.apiary.io/#reference/events/event-model) with the following properties

+ **id** - *number* - The ESOC model id. *(primary key, unique)*
+ **eventTag** - *string* - The SARAH event id. *(primary key SARAH, unique)*
+ **hardwareListNumber** - *string* - The SARAH hardware list number.
+ **type** - *string* - The type of event.
+ **flight** - *string* - The name of the associated flight to the event, if applicable.
+ **crewMember** - *object* - The associated crewMember model of the event, if applicable.
    + **id** - *number* - The ESOC model id **(primary key, unique)**
    + **crewId** - *string* - The SARAH crew member id **(primary key SARAH, unique)**
    + **firstName** - *string* - The crew member's first name
    + **lastName** - *string* - The crew member's last name
    + **middleInitial** - *string* - The crew member's middle initial
    + **nasaInitials** - *string* - The crew member's initials as assigned by NASA.
    + **sex** - *string* - The crew member's sex
    + **type** - *string* - The crew member's type
    + **isActive** - *bool* - Shows if crewmember is currently active
     > [A subset of the  *CrewMember model*](http://docs.emuapi.apiary.io/#reference/crewmembers/crewmember-model)
+ **status** - *string* - The Event's current status.
+ **audit** - *object* - The Event's audit model.


+ Parameters
    + id: 1 (required, number) - ID of the desired component
    + since: 01/01/2014 (optional, date) - Only return records that have been updated since the parameter.'
    
#### Get Component's Event Collection [GET]
    
    URL
    /component/{id}/events
    
    PARAMETERS
    id: component's NEDi model id or component's tracer id from SARAH

    QUERY STRING OPTIONS
    since:  Only return records that have been updated since the parameter
    
+ Response 200 (application/json)

        [{
            "id": 1,
            "eventTag": "1234Event",
            "hardwareListNumber": 1234ABC,
            "type": "EVA",
            "flight" null,
            "crewMember": {
                "id": 1,
                "crewId": "1234ABC,
                "firstName": "Collin",
                "lastName": "Estes",
                "middelInitial": "J",
                "nasaInitials": "CJE",
                "sex": "male",
                "type": "astronaut",
                "isActive": true
            }
            "status": "active",
            "audit": {}
        }, {
            "id": 1,
            "eventTag": "1234Event",
            "hardwareListNumber": 1234ABC,
            "type": "EVA",
            "flight" null,
            "crewMember": {
                "id": 1,
                "crewId": "1234ABC,
                "firstName": "Collin",
                "lastName": "Estes",
                "middelInitial": "J",
                "nasaInitials": "CJE",
                "sex": "male",
                "type": "astronaut",
                "isActive": true
            }
            "status": "active",
            "audit": {}
        }]
        
### Transactions Collection [/component/{id}/transactions(?since)]

A component's **Transaction** Model has the following properties

+ **id** - *number* - The ESOC model id. *(primary key, unique)*
+ **type** - *string* - The transaction type
+ **date** - *string* - The transaction date
+ **attributes** - *object*



+ Parameters
    + id: 1 (required, number) - ID of the desired component
    + since: 01/01/2014 (optional, date) - Only return records that have been updated since the parameter.'
    
#### Get Component's Transaction Collection [GET]
    
    URL
    /component/{id}/transactions
    
    PARAMETERS
    id: component's NEDi model id or component's tracer id from SARAH

    QUERY STRING OPTIONS
    since:  Only return records that have been updated since the parameter
    
+ Response 200 (application/json)

        [{
            "id": 1,
            "type": "location"
            "date": 01-01-2015
            "attributes": { }
        },{
            "id": 2,
            "type": "shipping",
            "date": 01-15-2015,
            "attributes": { }
        }]        

### Audit Model [/component/{id}/audit]

A component's **audit** Model has the following attributes:


+ **lastUpdatedDate** - *date* - The date the component record was last updated.
+ **lastUpdatedBy** - *string* - The user who last updated the component record.
+ **description** - *string* - The description of the update.

+ Parameters
     + id: 1 (required, number) - ID of the desired master
    
#### Get Component's Audit Model [GET]
    
    URL
    /component/{id}/calibration
    
    PARAMETERS
    id: component's NEDi model id or component's tracer id from SARAH

+ Response 200 (application/json)

        {
            "lastUpdatedBy": "MFIELDEN",
            "lastUpdatedDate": 01-30-2015,
            "description": "Created Item"

        }
        






## Group Masters
Masters within EVA are hardware, tool, or material information at the drawing level.  Every EVA component is an instance of master, the master defines several common data elements pertaining to a particular type/configuration of a given EVA hardware, tool, or material.
Components within EVA are the serial and/or lot controlled EVA hardware, tools, or material instances.

**Component Models consist of**:
+ [identification data](http://docs.emuapi.apiary.io/#reference/masters/master-model)
+ [attributes](http://docs.emuapi.apiary.io/#reference/masters/master-model)
+ [quantity](http://docs.emuapi.apiary.io/#reference/masters/quantity-model)
+ [bill](http://docs.emuapi.apiary.io/#reference/masters/bill-model) of material
+ associated [documents](http://docs.emuapi.apiary.io/#reference/masters/document-model)
+ default [limited life](http://docs.emuapi.apiary.io/#reference/masters/limitied-life-model) items
+ default [calibrations](http://docs.emuapi.apiary.io/#reference/masters/calibrations-model)
+ [audit](http://docs.emuapi.apiary.io/#reference/masters/audit-model) data

### Masters Model [/master/{id}]

A **Master** model has the following attributes:

+ **id** - *number* - the ESOC model id **(primary key, unique)**.
+ **itemNumber** - *string* - The SARAH id for the master **(primary key SARAH, unique)**.
+ **description** - *string* - The description of the master.
+ **drawingNumber** - *string* - The master's drawing number.
+ **attributes** - *object* - The master's attributes.
   + **itemNumber** - *string* - Unique identifier for any manufactured or purchased part, material, subassembly, product or service.
    + **drawingNumber** - *string* - Unique identifier for a drawing.
    + **side** - *string* - Designates an item as right or left.
    + **itemSize** - *string* - Designates the size of an item.
    + **asbuiltNumber** - *string* -  A configuration version number of a drawing.
    + **description** - *string* - Nomenclature for describing an item.
    + **stockUnitMeasure** - *string* - Stock unit of measure.
    + **currentEcl** - *string* - Indicates the Engineering Change Level for an item.
    + **itemType** - *string* - A method of associating item numbers into a group.
    + **category** - *string* - Category is a one or two letter code that identifies the kind of hardware the part is.  Examples: "BE" is business equipment, "H" is flight hardware, "EH" is EMU hardware, RF is raw food, FF is flight food, etc.
    + **objectClass** - *number* -A method of grouping equipment for Property.
    + **status** - *string* -A code to indicate if the item is "A"ctive or "I"nactive.  
    + **isPhantom** - *boolean* - A flag indicating part does not have a physical reality.  It exists as a phantom so that its components can be manipulated as a group.
    + **isSerial** - *boolean* - Aflag used to designate a part as serial controlled.
    + **isLot** - *boolean* - A flag used to designate an item as lot controlled.
    + **ceiNumber** - *string* -Some items within equipment group 2.01 (EMU hardware) have a 3 digit contract end item (CEI) number, consisting of a digit 0-9 to further group or categorize the items.For example, a PLSS is CEI 100, HUT is 102, LTA is 104, SOP is 200, etc.  The CEI number is assigned by the vendor, Hamilton Standard and/or ILC.
    + **equipmentGroup** - *string* -A code for categorizing hardware into engineering groups for responsibility assignment.
    + **lifeLimit** - *string* -Short description of life limit.
    + **isADP** - *boolean* -  A flag indicates whether or not an item requires an approved data pack.
    + **soleSourceCode** - *string* -A code to indicate if there is a sole source for this item.  "M" (manufacturer), "V" (vendor), or "N" (none). 
    + **isShelfLife** - *boolean* -A Flag to indicate whether there is a shelf limited life requirement for the item.
    + **isUsageLife** - *boolean* - A Flag to indicate whether there is a usage limited life requirement for the item.
    + **isTimeLife** - *boolean* -A Flag to indicate whether there is a time limited life requirement for the item (Currently, this is dealing primarily with pressure time or fan time).
    + **isCycleLife** - *boolean* -A Flag to indicate whether there is a cycle limited life requirement for the item.
    + **isFlightLife** - *boolean* - A Flag to indicate whether there is a flight limited life requirement for the item.  
    + **reasonInitCode** - *string* - A code used to identify what caused the initiation of the item master.
    + **approvalStatus** - *string* - The status of the approval.
    + **vendorCode** - *string* - A six-digit number assigned to suppliers of SGT equipment and services.
    + **limitedLifeCode** - *string* - A code that defines the limited life type.
    + **isHazardousMaterial** - *boolean* - Identifies if an item is considered a hazardous material. 
    + **expendRefurbCode** - *string* - A code to indicate whether an item is expendable or refurbishable.
    + **insertDate** (date) - The date on which the data record was entered.
    + **shelfLifeDefault** - *number* - A value defining the maximum amount of time an item is allowed to sit on the shelf. 
    + **usageLifeDefault** - *number* - A value defining the maximum amount of time an item is allowed to be used.  
    + **timeLifeDefault** - *number* - A value defining the maximum amount of time allowed on the item.  
    + **cycleshelfLifeDefault** - *number* - A value defining the maximum number of cycles allowed on the item before service; refurbishment or limited life extension must occur. 
    + **flightLifeDefault** - *number* - A value defining the maximum number of flights the item can fly before it must be serviced, refurbished, downgraded, or scrapped.  
    + **shelfLifeUM** - *string* - Shelf life Unit of Measure.  Defines whether the shelf life limited life requirements are in DAYS, MONS or YRS. 
    + **usageLifeUM** - *string* - Usage life Unit of Measure.  Defines whether the usage life limited life requirements are in DAYS, MONS or YRS.
    + **timeLifeUM** - *string* - Time life Unit of Measure.  Defines whether the time life limited life requirements are in HRS, MONS, or YRS.
    + **hdwSource** - *string* - Identifies the supplier of an item.
    + **usageLifeServiceDefault** - *number* - Usage Life Service Default.  This defines when the item must be serviced which then re-starts the limited life "clock". 
    + **timeLifeServiceDefault** - *number* - Time Life Service Default.  This defines when the item must be serviced which then re-starts the limited life "clock".
    + **cycleLifeServiceDefault** - *number* - Cycle Life Service Default.  This defines when the item must be serviced which then re-starts the limited life "clock".
    + **flightLifeServiceDefault** - *number* -Flight Life Service Default.  This defines when the item must be serviced which then re-starts the limited life "clock".
    + **isCleanTrack** - *boolean* - A flag to indicate if cleanliness tracking is required on this item.
    + **preciousCode** - *string* - A two digit code used to designate a precious material.
    + **initDocument** - *string* -Document number that authorizes part to be initialized into SARAH.
    + **vendorItemNumber** - *string* - Vendor's part number.
    + **inventoryMethod** - *string* -The method by which the item will be inventoried. C=Count, O=Observation, and W=Weighed.
    + **criticalityCode** - *string* - A code describing the importance of an item to the mission, the vehicle, or the crew.  1/1 = Loss of either crew or vehicle or both; 2/2 = Loss of Mission; 3/3 = No effect on either crew, vehicle, or mission; 2/1R = Loss of mission for a single failure, Loss of crew for multiple failure of redundant items; 3/1R = No effect for a single failure, Loss of crew for multiple failure of redundant items; 3/2R = No effect for a single failure, Loss of mission for multiple failures of redundant items
    + **isFractureCritical** - *boolean* - A Flag indicates whether the item is a fracture critical part. A fracture critical part is one whose failure would result in a catastrophic occurrence such as loss of life, disabling injury, or loss of vehicle or mission.
    + **itemWeight** - *number* - The weight of an item in pounds.
    + **isPreprocessedHardware** - *boolean* - A flag indicates whether the item is preprocessed hardware.
    + **FSC** - *number* -Federal Supply Class. FSC is a code assigned by the Federal Government to a manufacturer.
    + **isGP** - *boolean* - A flag to indicate whether there is a Green Procurement requirement for this item.
    + **gpCatCode** - *string* -  Green Procurement Category Code. It is used to identify a specific combination of a green procurement category and a green procurement subcategory for an item.
    + **gpCat** - *string* -Green Procurement Category. It is used to identify a product category outlined in the Environmental Protection Agency's Comprehensive Procurement Guideline(CPG) for an item.
    + **gpSubcat** - *string* - Green Procurement Subcategory. It is used to identify a product subcategory outlined in the Environmental Protection Agency's Comprehensive Procurement Guideline (CPG) for an item.
    + **complexHardwareCode** - *string* - Identifies whether the item number is defined as complex or non-complex. The valid values are- 'C' for complex, 'N' for non-complex and 'X' for materials that do not fall within the Complex/Non-complex requirements.
    + **isTransfer** - *boolean* -This flag is used to identify whether the item number has been transferred.
    + **isTransition** - *boolean* - This flag is used to identify whether the item number has been transitioned.
    + **programCode** - *string* - A code number of program to which depreciation will be charged. 
    + **isSphn** - *boolean* - A flag is used to designate special packaging, handling, storage and transportation requirements.
    + **isOperationLife** - *boolean* - A flag to indicate whether there is an operational life requirement for the item. 
    + **operationLifeDefault** - *number* - Maximum amount of chronological time or manned pressurized time in days, months or years that the part can be used which starts once the part is put into service or removed from controlled conditions.
    + **operationLifeServiceDefault** - *number* - Number of days, months or years that the part can be used prior to requiring a service.
    + **operationLifeUnitMeasure** - *string* - Operational life unit of measure.
    + **isOnOrbitLife** - *boolean* - A flag to indicate whether there is an on-orbit  life requirement for the item. 
    + **onOrbitLifeDefault** - *number* - Maximum number of days, months or years that the part can be on-orbit.
    + **onOrbitLifeServiceDefault** - *number* - Number of days, months or years that the part can be on-orbit prior to requiring a service.
    + **onOrbitLifeUnitMeasure** - *string* - On-Orbit life unit of measure.
    + **isIntervalLife**  - *boolean* - A flag to indicate whether there is an interval (non-consecutive days, months or years) limited life requirement for the item. 
    + **intervalLifeDefault** - *number* - Maximum number of non-consecutive days, months or years.
    + **intervalLifeServiceDefault** - *number* - Number of days, months or years during the interval period prior to requiring a service.
    + **intervalLifeUnitMeasure** - *string* - Interval life unit of measure.
    + **isEvaLimit** - *boolean* - A flag to indicate whether there is a EVA limited life requirement for the item. 
    + **evaLimitDefault** - *number* - Maximum number of EVAs.
    + **evaLimitServiceDefault** - *number* - Number of EVAs allowed prior to requiring service.
+ **quantity** - *object* - The master inventory quantities for child components
    >[*see quantity model*](http://docs.emuapi.apiary.io/#reference/masters/quantity-model)
+ **limitedLife** - *array[objects]* - The master's limited life data
    > [*see Limited Life model*](http://docs.emuapi.apiary.io/#reference/masters/limited-life-model)
+ **calibrations** - *object* - The master's calibration data 
    > [*see Calibration model*](http://docs.emuapi.apiary.io/#reference/masters/calibration-model)
+ **documents** - *array[objects]* - The master's collection of associated documents.
    > [*see Document model*](http://docs.emuapi.apiary.io/#reference/documents/document-model)
+ **components** - *array[objects]* - The master's collection of children components.  Instances of the master.
    > [*see Component model*](http://docs.emuapi.apiary.io/#reference/components/component-model)
+ **bill** - *object* - The master's bill of material assembly
    > [*see Bill model*](http://docs.emuapi.apiary.io/#reference/masters/bill-model)
+ **drawing** - *object* - The master's associated draw
    > [*see Drawing model*](http://docs.emuapi.apiary.io/#reference/masters/drawing-model)
+ **audit** - *object* - The master's auditable history items
    > [*see Audit model*](http://docs.emuapi.apiary.io/#reference/masters/audit-model)
    

+ Parameters
    + id: 1 (required, number) - ID of the desired master
 
#### Get Masters Model [GET]

    URL
    /master/{id}
    
    PARAMETERS
    id: master's NEDi model id or master's itemNumber id from SARAH

+ Response 200 (application/json)

         {
            "id": 1,
            "itemNumber": "SVG1235",
            "description": "EMU GLOVE",
            "drawingNumber": "1234Draw",
            "attributes": {
                "itemNumber": "A100L5",
                "drawingNumber": "B200R1",
                "side": "right",
                "itemSize": "large",
                "asbuiltNumber": "A100L5B200R1RL",
                "description": "Helmet assembly to be used with EMU",
                "stockUnitMeasure": "inches",
                "currentEcl": "low level",
                "itemType": "AB10",
                "category": "BE",
                "objectClass": 1105,
                "status": "A",
                "isPhantom": True,
                "isSerial": True,
                "isLot": True,
                "ceiNumber": "A123B10",
                "equipmentGroup": "TB100",
                "lifeLimit": "Limited to ten uses before needing rebuild",
                "isADP": True,
                "soleSourceCode": "M",
                "isShelfLife": True,
                "isUsageLife": True,
                "isTimeLife": True,
                "isCycleLife": Flase,
                "isFlightLife": False,
                "reasonInitCode": "C100A",
                "approvalStatus": "Awaiting signitures",
                "vendorCode": "500100",
                "limitedLifeCode": "STerm",
                "isHazardousMaterial": False,
                "expendRefurbCode": "Exp",
                "insertDate": "01-05-2015",
                "shelfLifeDefault": 100,
                "usageLifeDefault": 25,
                "timeLifeDefault": 365,
                "cycleshelfLifeDefault": 10,
                "flightLifeDefault": 5,
                "shelfLifeUM": "DAYS",
                "usageLifeUM": "DAYS",
                "timeLifeUM": "MONS",
                "hdwSource": "Ratheon",
                "usageLifeServiceDefault": 15,
                "timeLifeServiceDefault": 20,
                "cycleLifeServiceDefault": 10,
                "flightLifeServiceDefault": 20,
                "isCleanTrack": True,
                "preciousCode": "Au"
                "initDocument": "S100B2",
                "vendorItemNumber": "C100",
                "inventoryMethod": "C",
                "criticalityCode": "3/2R",
                "isFractureCritical": True,
                "itemWeight": 1125,
                "isPreprocessedHardware": False,
                "FSC": 100418,
                "isGP": True,
                "gpCatCode": "GP100B",
                "gpCat": "Reusable",
                "gpSubcat": "Non-corrosive",
                "complexHardwareCode": "C",
                "isTransfer": True,
                "isTransition": True,
                "programCode": "A12B2",
                "isSphn": False,
                "isOperationLife": True,
                "operationLifeDefault": 365,
                "operationLifeServiceDefault": 180,
                "operationLifeUnitMeasure": "Days",
                "isOnOrbitLife": True,
                "onOrbitLifeDefault": 365,
                "onOrbitLifeServiceDefault": 180,
                "onOrbitLifeUnitMeasure": "Days",
                "isIntervalLife": True,
                "intervalLifeDefault": 180,
                "intervalLifeServiceDefault": 90,
                "intervalLifeUnitMeasure": "Days",
                "isEvaLimit": True,
                "evaLimitDefault": 5,
                "evaLimitServiceDefault": 10
            }
            "bill": {
                "children": [{
                    "id": 2,
                    "itemNumber": "1234ITEM",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678"
                }, {
                    "id": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123",
                }],
                "parent": {
                    "id": 1,
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123",
                }
            },
            "documents": [{
                "id": 1,
                "sarahDocumentId": "YTN-1234",
                "type": "YTN",
                "openDate": 01-01-2014,
                "closeDate": 02-01-2015,
                "title": "EMU YTN from DR 1234",
                "comments": "This is a comment on a YTN.  More comments are also included.",
            }, {
                "id": 1,
                "sarahDocumentId": "DR-56789",
                "type": "DR",
                "openDate": 01-01-2014,
                "closeDate": 02-01-2015,
                "title": "EMU DR for CR 56789",
                "comments": "This is a comment on a DR.  More comments are also included.",
            }]
            "limitedLife": [{
                "id": 1,
                "componentId": 1
                "attributes": {
                    "type": "date",
                    "name": "shelfLifeExpirationDate",
                    "description": "The masters's default shelf life expiration date",
                    "requirement": {
                        "unit": "days",
                        "value": "365",
                        "description": "365 days from the master's birth date"
                    }
            }, {
                "id": 1,
                "componentId": 1
                "attributes": {
                    "type": "number",
                    "name": "maxtoolImmersions",
                    "description": "The master's total immersion count",
                    "requirement": {
                        "unit": "number",
                        "value": "100",
                        "description": "100 Total tool immersions"
                    }
                }
            }],
            "calibrations": [{
                "id": 1,
                "componentId": 1
                "attributes": [{
                    "type": "number",
                    "name": "Some Setting",
                    "description": "The master's calibration setting for something",
                    "value": "1.0"
                }]
            }, 
            {
                "id": 2,
                "componentId": 1
                "attributes": {
                    "type": "string",
                    "name": "Some Other Setting",
                    "description": "The master's calibration setting for something else",
                    "value": "1ABC"
                }
            }],
            "drawing":  {
                "id": 1,
                "itemNumber": "ABC1234"
                "attributes": {
                    "id": 1,
                    "drawingNumber": "1234Draw",
                    "original": null,
                    "revision": "123ABC",
                    "releaseDate": 01-01-2014,
                    "totalSheets": 2,
                    "copyType": "hardcopy",
                    "securityClass": "I",
                    "prefix": null,
                    "title": "A hardware component",
                    "federalSupplyCode: null,
                    "isRetired": false,
                    "hasDrawingChange": false,
                    "prefixDrawing": null,
                    "comments": "This is a comment.",
                    "assetClassUsage: [{
                        "itemClass": "I",
                        "assetClassification": null,
                        "assetUsage": null,
                        "isCriticalGse": false
                    }, { 
                        "itemClass": "II",
                        "assetClassification": null,
                        "assetUsage": null,
                        "isCriticalGse": true
                    }]
                }
            },
            "audit": [{
                "lastUpdatedBy": "MFIELDEN",
                "lastUpdatedDate": 01-30-2015,
                "description": "Created Item"
            }, {
                "lastUpdatedBy": "CJESTES",
                "lastUpdatedDate": 02-15-2015,
                "description": "Updated Item"
            }]
        }
        
### Masters Collection [/masters(?since)]

+ Parameters
    + since: 01/01/2014 (optional, date) - Only return records that have been updated since the parameter.'
    
#### Get Masters Collection [GET]

    URL
    /masters
    
    QUERY STRING OPTIONS
    since:  Only return records that have been updated since the parameter
    
+ Response 200 (application/json)

         [{
            "id": 1,
            "itemNumber": "SVG1235",
            "description": "EMU GLOVE",
            "drawingNumber": "1234Draw",
            "attributes": {
                "itemNumber": "A100L5",
                "drawingNumber": "B200R1",
                "side": "right",
                "itemSize": "large",
                "asbuiltNumber": "A100L5B200R1RL",
                "description": "Helmet assymbly to be used with EMU",
                "stockUnitMeasure": "inches",
                "currentEcl": "low level",
                "itemType": "AB10",
                "category": "BE",
                "objectClass": 1105,
                "status": "A",
                "isPhantom": True,
                "isSerial": True,
                "isLot": True,
                "ceiNumber": "A123B10",
                "equipmentGroup": "TB100",
                "lifeLimit": "Limited to ten uses before needing rebuild",
                "isADP": True,
                "soleSourceCode": "M",
                "isShelfLife": True,
                "isUsageLife": True,
                "isTimeLife": True,
                "isCycleLife": Flase,
                "isFlightLife": False,
                "reasonInitCode": "C100A",
                "approvalStatus": "Awaiting signitures",
                "vendorCode": "500100",
                "limitedLifeCode": "STerm",
                "isHazardousMaterial": False,
                "expendRefurbCode": "Exp",
                "insertDate": "01-05-2015",
                "shelfLifeDefault": 100,
                "usageLifeDefault": 25,
                "timeLifeDefault": 365,
                "cycleshelfLifeDefault": 10,
                "flightLifeDefault": 5,
                "shelfLifeUM": "DAYS",
                "usageLifeUM": "DAYS",
                "timeLifeUM": "MONS",
                "hdwSource": "Ratheon",
                "usageLifeServiceDefault": 15,
                "timeLifeServiceDefault": 20,
                "cycleLifeServiceDefault": 10,
                "flightLifeServiceDefault": 20,
                "isCleanTrack": True,
                "preciousCode": "Au"
                "initDocument": "S100B2",
                "vendorItemNumber": "C100",
                "inventoryMethod": "C",
                "criticalityCode": "3/2R",
                "isFractureCritical": True,
                "itemWeight": 1125,
                "isPreprocessedHardware": False,
                "FSC": 100418,
                "isGP": True,
                "gpCatCode": "GP100B",
                "gpCat": "Reusable",
                "gpSubcat": "Non-corrosive",
                "complexHardwareCode": "C",
                "isTransfer": True,
                "isTransition": True,
                "programCode": "A12B2",
                "isSphn": False,
                "isOperationLife": True,
                "operationLifeDefault": 365,
                "operationLifeServiceDefault": 180,
                "operationLifeUnitMeasure": "Days",
                "isOnOrbitLife": True,
                "onOrbitLifeDefault": 365,
                "onOrbitLifeServiceDefault": 180,
                "onOrbitLifeUnitMeasure": "Days",
                "isIntervalLife": True,
                "intervalLifeDefault": 180,
                "intervalLifeServiceDefault": 90,
                "intervalLifeUnitMeasure": "Days",
                "isEvaLimit": True,
                "evaLimitDefault": 5,
                "evaLimitServiceDefault": 10
            }
            
            "bill": {
                "children": [{
                    "id": 2,
                    "itemNumber": "1234ITEM",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678"
                }, {
                    "id": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123",
                }],
                "parent": {
                    "id": 1,
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123",
                }
            },
            "documents": [{
                "id": 1,
                "sarahDocumentId": "YTN-1234",
                "type": "YTN",
                "openDate": 01-01-2014,
                "closeDate": 02-01-2015,
                "title": "EMU YTN from DR 1234",
                "comments": "This is a comment on a YTN.  More comments are also included.",
            }, {
                "id": 1,
                "sarahDocumentId": "DR-56789",
                "type": "DR",
                "openDate": 01-01-2014,
                "closeDate": 02-01-2015,
                "title": "EMU DR for CR 56789",
                "comments": "This is a comment on a DR.  More comments are also included.",
            }]
            "limitedLife": [{
                "id": 1,
                "componentId": 1
                "attributes": {
                    "type": "date",
                    "name": "shelfLifeExpirationDate",
                    "description": "The masters's default shelf life expiration date",
                    "requirement": {
                        "unit": "days",
                        "value": "365",
                        "description": "365 days from the master's birth date"
                    }
            }, {
                "id": 1,
                "componentId": 1
                "attributes": {
                    "type": "number",
                    "name": "maxtoolImmersions",
                    "description": "The master's total immersion count",
                    "requirement": {
                        "unit": "number",
                        "value": "100",
                        "description": "100 Total tool immersions"
                    }
                }
            }],
            "calibrations": [{
                "id": 1,
                "componentId": 1
                "attributes": [{
                    "type": "number",
                    "name": "Some Setting",
                    "description": "The master's calibration setting for something",
                    "value": "1.0"
                }]
            }, 
            {
                "id": 2,
                "componentId": 1
                "attributes": {
                    "type": "string",
                    "name": "Some Other Setting",
                    "description": "The master's calibration setting for something else",
                    "value": "1ABC"
                }
            }],
            "drawing":  {
                "id": 1,
                "attributes": {
                    "id": 1,
                    "drawingNumber": "1234Draw",
                    "original": null,
                    "revision": "123ABC",
                    "releaseDate": 01-01-2014,
                    "totalSheets": 2,
                    "copyType": "hardcopy",
                    "securityClass": "I",
                    "prefix": null,
                    "title": "A hardware component",
                    "federalSupplyCode: null,
                    "isRetired": false,
                    "hasDrawingChange": false,
                    "prefixDrawing": null,
                    "comments": "This is a comment.",
                    "assetClassUsage: [{
                        "itemClass": "I",
                        "assetClassification": null,
                        "assetUsage": null,
                        "isCriticalGse": false
                    }, { 
                        "itemClass": "II",
                        "assetClassification": null,
                        "assetUsage": null,
                        "isCriticalGse": true
                    }]
                }
            },
            "audit": {
                "createdBy": "CJESTES",
                "createdDate": 01-01-2015,
                "closedDate": 01-30-2015,
                "closedBy": "MFIELDEN",
                "lastUpdatedBy": "MFIELDEN"
                "lastUpdatedDate": 01-30-2015
            }
        },
         {
            "id": 2,
            "itemNumber": "SVG9876",
            "description": "EMU ARM",
            "drawingNumber": "DRAW1234",
            "attributes": {
                "itemNumber": "A200L4",
                "drawingNumber": "B200R2",
                "side": "right",
                "itemSize": "large",
                "asbuiltNumber": "A200L4B200R2RL",
                "description": "Helmet assymbly to be used with EMU",
                "stockUnitMeasure": "inches",
                "currentEcl": "low level",
                "itemType": "AB10",
                "category": "BE",
                "objectClass": 1105,
                "status": "A",
                "isPhantom": True,
                "isSerial": True,
                "isLot": True,
                "ceiNumber": "A123B10",
                "equipmentGroup": "TB100",
                "lifeLimit": "Limited to ten uses before needing rebuild",
                "isADP": True,
                "soleSourceCode": "M",
                "isShelfLife": True,
                "isUsageLife": True,
                "isTimeLife": True,
                "isCycleLife": Flase,
                "isFlightLife": False,
                "reasonInitCode": "C100A",
                "approvalStatus": "Awaiting signitures",
                "vendorCode": "500100",
                "limitedLifeCode": "STerm",
                "isHazardousMaterial": False,
                "expendRefurbCode": "Exp",
                "insertDate": "01-05-2015",
                "shelfLifeDefault": 100,
                "usageLifeDefault": 25,
                "timeLifeDefault": 365,
                "cycleshelfLifeDefault": 10,
                "flightLifeDefault": 5,
                "shelfLifeUM": "DAYS",
                "usageLifeUM": "DAYS",
                "timeLifeUM": "MONS",
                "hdwSource": "Ratheon",
                "usageLifeServiceDefault": 15,
                "timeLifeServiceDefault": 20,
                "cycleLifeServiceDefault": 10,
                "flightLifeServiceDefault": 20,
                "isCleanTrack": True,
                "preciousCode": "Au"
                "initDocument": "S100B2",
                "vendorItemNumber": "C100",
                "inventoryMethod": "C",
                "criticalityCode": "3/2R",
                "isFractureCritical": True,
                "itemWeight": 1125,
                "isPreprocessedHardware": False,
                "FSC": 100418,
                "isGP": True,
                "gpCatCode": "GP100B",
                "gpCat": "Reusable",
                "gpSubcat": "Non-corrosive",
                "complexHardwareCode": "C",
                "isTransfer": True,
                "isTransition": True,
                "programCode": "A12B2",
                "isSphn": False,
                "isOperationLife": True,
                "operationLifeDefault": 365,
                "operationLifeServiceDefault": 180,
                "operationLifeUnitMeasure": "Days",
                "isOnOrbitLife": True,
                "onOrbitLifeDefault": 365,
                "onOrbitLifeServiceDefault": 180,
                "onOrbitLifeUnitMeasure": "Days",
                "isIntervalLife": True,
                "intervalLifeDefault": 180,
                "intervalLifeServiceDefault": 90,
                "intervalLifeUnitMeasure": "Days",
                "isEvaLimit": True,
                "evaLimitDefault": 5,
                "evaLimitServiceDefault": 10
            }
            "bill": {
                "children": [{
                    "id": 2,
                    "itemNumber": "1234ITEM",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678"
                }, {
                    "id": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123",
                }],
                "parent": {
                    "id": 1,
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123",
                }
            },
            "documents": [{
                "id": 1,
                "sarahDocumentId": "YTN-1234",
                "type": "YTN",
                "openDate": 01-01-2014,
                "closeDate": 02-01-2015,
                "title": "EMU YTN from DR 1234",
                "comments": "This is a comment on a YTN.  More comments are also included.",
            }, {
                "id": 1,
                "sarahDocumentId": "DR-56789",
                "type": "DR",
                "openDate": 01-01-2014,
                "closeDate": 02-01-2015,
                "title": "EMU DR for CR 56789",
                "comments": "This is a comment on a DR.  More comments are also included.",
            }]
            "limitedLife": [{
                "id": 1,
                "componentId": 1
                "attributes": {
                    "type": "date",
                    "name": "shelfLifeExpirationDate",
                    "description": "The masters's default shelf life expiration date",
                    "requirement": {
                        "unit": "days",
                        "value": "365",
                        "description": "365 days from the master's birth date"
                    }
            }, {
                "id": 1,
                "componentId": 1
                "attributes": {
                    "type": "number",
                    "name": "maxtoolImmersions",
                    "description": "The master's total immersion count",
                    "requirement": {
                        "unit": "number",
                        "value": "100",
                        "description": "100 Total tool immersions"
                    }
                }
            }],
            "calibrations": [{
                "id": 1,
                "componentId": 1
                "attributes": [{
                    "type": "number",
                    "name": "Some Setting",
                    "description": "The master's calibration setting for something",
                    "value": "1.0"
                }]
            }, 
            {
                "id": 2,
                "componentId": 1
                "attributes": {
                    "type": "string",
                    "name": "Some Other Setting",
                    "description": "The master's calibration setting for something else",
                    "value": "1ABC"
                }
            }],
            "drawing":  {
                "id": 1,
                "drawingNumber": 
                "attributes": {
                    "id": 1,
                    "drawingNumber": "1234Draw",
                    "original": null,
                    "revision": "123ABC",
                    "releaseDate": 01-01-2014,
                    "totalSheets": 2,
                    "copyType": "hardcopy",
                    "securityClass": "I",
                    "prefix": null,
                    "title": "A hardware component",
                    "federalSupplyCode: null,
                    "isRetired": false,
                    "hasDrawingChange": false,
                    "prefixDrawing": null,
                    "comments": "This is a comment.",
                    "assetClassUsage: [{
                        "itemClass": "I",
                        "assetClassification": null,
                        "assetUsage": null,
                        "isCriticalGse": false
                    }, { 
                        "itemClass": "II",
                        "assetClassification": null,
                        "assetUsage": null,
                        "isCriticalGse": true
                    }]
                }
            },
            "audit": {
                "createdBy": "CJESTES",
                "createdDate": 01-01-2015,
                "closedDate": 01-30-2015,
                "closedBy": "MFIELDEN",
                "lastUpdatedBy": "MFIELDEN"
                "lastUpdatedDate": 01-30-2015
            }
        }]

### Quantity Model [/master/{id}/quantity]

A master's **Quantity** Model has the following attributes:

+ **id** - *number* - The NEDi Model id **(primary key, unique)**.
+ **masterId** - *number* - The NEDi Model master id **(foreign key, unique)**.
+ **attributes** - *object* - Object containing the various quantities for a given master
    + TODO: NEED TO DEFINE
    

+ Parameters
     + id: 1 (required, number) - ID of the desired master
    
#### Get Master's quantity Model [GET]

    URL
    /master/{id}
    
    PARAMETERS
    id: master's NEDi model id or master's itemNumber id from SARAH
    
+ Response 200 (application/json)

        {
            "id": 1,
            "masterId": 1
            "attributes": {}
        }        
        
### Limited Life Collection [/master/{id}/limitedlifes]

A master's **Limited life** Model has the following properties:

+ **id** - *number* - The NEDi Model id **(primary key, unique)**.
+ **master** - *number* - The NEDi Model master id **(foreign key, unique)**.
+ **attributes** - *array[object]* - An array of the limited life attributes for the master
    + **type** - *string* - The type of requirement.
    > available types: 'date', 'count', 'time'.
    + **name** - *string* - The name of the limited life attribute.
    + **description** - *string* - A description of the limited life attribute.
    + **value** - *string* - The value of the limited life requirement, all converted to a string
    > values could be dates, numbers, or time values depending on the type above.  All will be converted to strings
    + **requirement** - *object* - The limited life requirement (FEMU defined) value.
        + **unit** - *string* - The unit of measure of the requirement value.
        + **value** -*string* - The limited life requirement value
        + **description** - *string* - A description of the limited life requirement.

+ Parameters
    + id: 1 (required, number) - ID of the desired master
    
#### Get Masters's Limited Life Collection [GET]

    URL
    /master/{id}/limitedlife
    
    PARAMETERS
    id: master's NEDi model id or master's itemNumber id from SARAH

+ Response 200 (application/json)

        [{
            "id": 1,
            "componentId": 1
            "attributes": [{
                "type": "date",
                "name": "shelfLifeExpirationDate",
                "description": "The master's default shelf life expiration date",
                "requirement": {
                    "unit": "days",
                    "value": "365",
                    "description": "365 days from the master's birth date"
                }
            }, {
                "type": "number",
                "name": "maxtoolImmersions",
                "description": "The master's default total immersion count",
                "requirement": {
                    "unit": "number",
                    "value": "100",
                    "description": "100 Total tool immersions"
                }
            }
        }]
        
### Bill Model [/master/{id}/bill]

A master's **bill** Model has the following properties:

+ **masterId** - *number* - The NEDi Model id of the corresponding master **(primary key, unique)**.
+ **itemNumber** - *number* - The SARAH master id. **(foreign key, unique)**.
+ **children** - array[objects] - An array of the master's children sub-assembly master models as built as a subset.
    > *master models for both the array of children objects will be [Master Models](http://docs.emuapi.apiary.io/#reference/components/master-model)
+ **parent** - object - The master's parent master assembly as built top level information. 
    + **id** - *number* - The ESOC model id **(primary key, unique)**
    + **tracer** - *string* - The SARAH component id **(primary key SARAH, unique)**
    + **masterId** - *number* - The ESOC master id of the master's parent **(fk, unique)**
    + **itemNumber** - *string* - The SARAH master id of the master's parent **(fk SARAH, unique)**
    
+ Parameters
    + id: 1 (required, number) - ID of the desired master
    
#### Get Bill Model [GET]

    URL
    /master/{id}/bill
    
    PARAMETERS
    id: master's NEDi model id or master's itemNumber id from SARAH

+ Response 200 (application/json)

           "bill": {
                "children": [{
                    "id": 2,
                    "masterId": 2,
                    "itemNumber": "1234ITEM",
                    "description": "Wrist connector",
                    "drawingNumber": "ABC678"
                }, {
                    "id": 3,
                    "tracer": "0001ABC",
                    "masterId": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678"
                }],
                "parent": {
                    "id": 1,
                    "tracer": "12345abcdef",
                    "masterId": 1,
                    "description": "EMU GLOVE"
                    "drawingNumber": "ABC678"
                }
            }
        
### Calibrations Collection [/master/{id}/calibrations]

A Master's **Calibration** Model has the following properties:

+ **id** - *number* - The NEDi Model id **(primary key, unique)**.
+ **itemNumber** - *number* - The SARAH master id. **(foreign key, unique)**.
+ **attributes** - *array[object]* - An array of the limited life attributes for the component
    + **type** - *string* - The type of calibration.
    > available types: TODO:  DETERMINE TYPES.
    + **name** - *string* - The name of the calibration attribute.
    + **description** - *string* - A description of the calibration attribute.
    + **value** - *string* - The value of the limited life requirement, all converted to a string
    > values could be: TODO: DETERMINE TYPES. 

+ Parameters
    + id: 1 (required, number) - ID of the desired master
    
#### Get Master's Calibration Collection [GET]

    URL
    /master/{id}/calibrations
    
    PARAMETERS
    id: master's NEDi model id or master's itemNumber id from SARAH

+ Response 200 (application/json)

        [{
            "id": 1,
            "itemNumber": 1
            "attributes": [{
                "type": "number",
                "name": "Some Setting",
                "description": "The component's calibration setting for something",
                "value": "1.0"
            }]
        }, 
        {
            "id": 2,
            "itemNumber": 1
            "attributes": [{
                "type": "string",
                "name": "Some Other Setting",
                "description": "The component's calibration setting for something else",
                "value": "1ABC"
            }]
        }]

### Drawing Model [/master/{id}/drawing]

A master's **Drawing** Model has the following properties:

+ **id** - *number* - The NEDi Model id **(primary key, unique)**.
+ **masterId** - *number* - The NEDi Model master id **(foreign key, unique)**.
+ **itemNumber** - *number* - The SARAH master id. **(foreign key, unique)**.
+ **attributes** - *object* - The Master's drawing attributes
    + **id** - *number* - The ESOC model id (primary key, unique)
    + **drawingNumber** - *string* -  Unique identifier for a drawing. **(primary key SARAH, unique)**
    + **original** - *string* -  A code which represents if the drawing in SGT possession is the original.
    + **revision** - *string* -  The revision of a drawing.   
    + **releaseDate** - *date* -  The date that the physical drawing was released.     
    + **totalSheet** - *number* -  The total number of sheets comprising the drawing.
    + **copyType** - *string* -  Drawing copy type.
    + **securityClass** - *string* -  The security level of the drawing.
    + **prefix** - *string* -  The prefix of the drawing identifier.  The drawing prefix is a concatenation of three individual one 1-letter codes - NASA Center Designator, Engineering Drawing Type, and NASA Program Designator.               
    + **title** - *string* -  The title of a drawing.
    + **federalSupplyCode** - *string* -  The Federal Supply Code for Manufacturers (FSCM).                                   
    + **isRetired** - *bool* -  A flag which indicated if the drawing has been retired. 
    + **hasDrawingChange** - *bool* -  A true/false flag which indicates if an Advance Drawing Change Notice (ADCN) or a Drawing Change Notice (DCN) exists against the drawing.             
    + **prefixDrawing** - *string* -  the prefix concatenated with the base drawing number
    + **comments** - *string* -  Comments for a drawing
    + **assetClassUsage** - *array[Objects]* - The allowed combinations of item class, asset classification and asset usage which can be applied to an item at the drawing level.
        + **itemClass** - *string* -  The quality class of an item.
        + **assetClassification** - *string* -  Asset classification that is used with asset usage to categorize drawings as to the level of configuration control required.
        + **assetUsage** - *string* -  Asset Usage that is used with asset classification to specify the level of configuration control for items at the drawing level. 
        + **isCritcalGse** - *bool* -  bool if the asset usage/asset classification combination applies to critical GSE.
    + **audit** - *object* - The component's auditable history items
        > [*Audit model*](http://docs.emuapi.apiary.io/#reference/components/audit-model)
        
+ Parameters
     + id: 1 (required, number) - ID of the desired master
    
#### Get Masters's Drawing Model [GET]

    URL
    /master/{id}/drawing
    
    PARAMETERS
    id: master's NEDi model id or master's itemNumber id from SARAH

+ Response 200 (application/json)

        {
            "id": 1,
            "itemNumber": "ABC1234"
            "attributes": [{
                "id": 1,
                "drawingNumber": "1234Draw",
                "original": null,
                "revision": "123ABC",
                "releaseDate": 01-01-2014,
                "totalSheets": 2,
                "copyType": "hardcopy",
                "securityClass": "I",
                "prefix": null,
                "title": "A hardware component",
                "federalSupplyCode: null,
                "isRetired": false,
                "hasDrawingChange": false,
                "prefixDrawing": null,
                "comments": "This is a comment.",
                "assetClassUsage: [{
                    "itemClass": "I",
                    "assetClassification": null,
                    "assetUsage": null,
                    "isCriticalGse": false
                    }, 
                    { 
                    "itemClass": "II",
                    "assetClassification": null,
                    "assetUsage": null,
                    "isCriticalGse": true
                    }]
            }]
            "audit": [{
                "lastUpdatedBy": "MFIELDEN",
                "lastUpdatedDate": 01-30-2015,
                "description": "Created Item"
            }, {
                "lastUpdatedBy": "CJESTES",
                "lastUpdatedDate": 02-15-2015,
                "description": "Updated Item"
            }]
        }

### Audit Model [/master/{id}/audit]

A master's **Audit** Model has the following attributes:

+ **id** - *number* - The NEDi Audit Model id **(primary key, unique)**.
+ **itemNumber** - *number* - The NEDi Model master id **(foreign key, unique)**.
+ **createdDate** - *date* - The date the component record was created.
+ **createdBy** - *string* - The user who created the master record.
+ **closedDate** - *date* - The date the master was closed.
+ **closeddBy** - *string* - The user who closed the master record.
+ **lastUpdatedDate** - *date* - The date the master record was last updated.
+ **lastUpdatedBy** - *date* - The user who last updated the master record.

+ Parameters
     + id: 1 (required, number) - ID of the desired master
    
#### Get Master's Audit Model [GET]

    URL
    /master/{id}/audit
    
    PARAMETERS
    id: master's NEDi model id or master's itemNumber id from SARAH

+ Response 200 (application/json)

        {
            "id": 1,
            "itemNumber": 1,
            "createdBy": "CJESTES",
            "createdDate": 01-01-2015,
            "closedDate": 01-30-2015,
            "closedBy": "MFIELDEN",
            "lastUpdatedBy": "MFIELDEN"
            "lastUpdatedDate": 01-30-2015
            
        }





## Group Events
Events within EVA are flights, Chamber runs, EVAs, or other designated activities. Events utlize hardware, tools, and/or material components, this usage is documented in the event's bill property.

### Event Model [/event/{id}]

An "Event" model has the following attributes:

+ **eventId** - *string* The EVA API id
+ **eventTag** - *string* The SARAH event id. *(primary key SARAH, unique)*
+ **eventName** - *string* The name of the event
+ **eventType** - *string* The type of the event
+ **billTypeName** - *string* The type of event bill
+ **flightName** - *string* The name of the associated flight to the event, if applicable.
+ **crewCodeId** - *string* The crew code identifier.
+ **lastUpdateDate** - *string* The last update date.
+ **eventDate** - *string* The Date of the event.
+ **listNumber** - *string* The hardware list number used by SARAH
+ **crewName** - *string* The associated crewMember name of the event, if applicable.
+ **status** - *string* The Event's current status.
+ **statusCode** - *string* The status code used by SARAH    
    
+ Parameters
    + id: 1 (required, number) - ID of the desired event
    
#### Get Event Model [GET]

    URL
    /event/{id}
    
    PARAMETERS
    id: event's NEDi model id or event's eventTag id from SARAH

+ Response 200 (application/json)

        {
            "eventId": 1,
            "eventTag": "129084522",
            "eventName": "SSATA",
            "eventType": "CHMBR",
            "billTypeName": "CREWMEMBER",
            "flightName": "EXP44",
            "crewCodeId": null,
            "eventDate": "12-20-2014",
            "listNumber": "129084522",
            "crewName": "John Doe",
            "status": "Final",
            "statusCode": "F"
        }
        
### Events Collection [/events(?status,since)]

+ Parameters
    + status: "final" (optional, string) - Only return events of a specified status
    + since: 01/01/2014 (optional, date) - Only return records that have been updated since the parameter.
    
#### Get Events Collection [GET]

    URL
    /esoc/v1/events
    
    QUERY STRING OPTIONS
    status: Only return records with a status matching the parameter.
    since:  Only return records that have been updated since the parameter.

+ Response 200 (application/json)

        [{
            "eventId": "129084522",
            "eventTag": "129084522",
            "eventName": "SSATA",
            "eventType": "CHMBR",
            "billTypeName": "CREWMEMBER",
            "flightNumber": "EXP44",
            "crewCodeId": null,
            "eventDate": "2014-07-20T00:00:00.000Z",
            "listNumber": "129084522",
            "crewName": "John Doe",
            "status": "Cancelled",
            "statusCode": "X"
        }, {
            "eventId": "268074738",
            "eventTag": "268074738",
            "eventName": "LAUNCH",
            "eventType": "FLIGHT",
            "billTypeName": "CREWMEMBER",
            "flightNumber": "SPX-5",
            "crewCodeId": null,
            "eventDate": "2014-12-01T00:00:00.000Z",
            "listNumber": "FHL-14-20",
            "crewName": "John Doe",
            "status": "Final",
            "statusCode": "F"

        }]
        
### Event Bill [/event/{eventId}/bill]

The Event Bill Component is used to produce a flatten collection of the event bill tree components. This flat representation can be transformed into a tree structure using the parentTracer/componentTracer relationship.  

Supplying the *event id* will return all components (including sub assembly components that make up an event bill.

+ Parameters
    + eventId: 1 (required, number) - ID of the desired event bill.
    
#### Get Event Bill Component [GET]

    URL
    /event/{eventId}/bill
    
    PARAMETERS
    id:  bill's NEDi model id

+ Response 200 (application/json)

            [
                {
                "tracerNumber": "AL9697540",
                "parentTracer": "AL12345",
                "itemNumber": "AL9697-04",
                "description": "CLAMP, THREE HOSE ASSY",
                "serialNumber": "540",
                "lotNumber": null,
                "side": null,
                "size": null,
                "drawingNumber": "AL9697",
                "quantity": 1
              },
              {
                "tracerNumber": "12345",
                "parentTracer": null,
                "itemNumber": "SED16102311-327",
                "description": "COMMUNICATIONS CARRIER ELECTRONICS MODULE, CCEM",
                "serialNumber": "5024",
                "lotNumber": null,
                "side": null,
                "size": null,
                "drawingNumber": "SED16102311",
                "quantity": 1
              },
              {
                "tracerNumber": "AL12345",
                "parentTracer": "abc12345",
                "itemNumber": "AL9693-03",
                "description": "CONNECTOR, MULTIPLE",
                "serialNumber": "485",
                "lotNumber": null,
                "side": null,
                "size": null,
                "drawingNumber": "AL9693",
                "quantity": 1
              }
            
            ]
            
### Event Bill Documents [/events/{id}/bill/documents(?status,type)]

+ Parameters
    + type: "DR" (optional, string) - Only return documents of the specified type that are associated with the event bill components.
    + status: "Open" (optional, string) - Only return document of a the specified status (open/closed) that are associated with the event bill components.
    
####Get Event Bill Documents [GET]

    URL
    /event/bill/{id}/documents/{componentId}
    
    PARAMETERS
    id:  bill's NEDi model id
    
    QUERY STRING OPTIONS
    type: Only return documents with a type matching the parameter.
    status: Only return documents with a status matching the parameter.

+ Response 200 (application/json)

        []


## Group Documents
Within EVA documents are written against masters and components.  The data relating to documents returned is specific to the documents type. Currently the available document types are:

+ **DR** - *"Discrepancy Report"* - DRs are written against components and/or masters to document discovered discrepancies and actions taken to address.
+ **EC** - *"Engineering Change"* - ECs are written against components and/or masters to document approved changes.
+ **TPS** - *"Task Preparation Sheet"* - TPSs are written against components and details the task steps to be performed on a component.
+ **YTN** - *"Yellow Tag Notice"* - YTNs are written against components and/or masters to document a yellow tag.
+ **OD** - *"Other Documents"* - ODs are written against components and/or masters.
+ **ODT** - *"Over Due Tags"* - ODTs are written against components and/or masters.
+ **FAB** - *"Fabrication Action Breakdown"* - FABs are written against masters and to the components that are fabricated to fulfill the FAB.
+ **WAIVER** - *"Waivers"* - Waivers are written against masters and/or components.
+ **ADCN** - *"Advanced Drawing Change Notice"* - ADCNs are written against a master (drawing) to provide notice of an upcoming drawing change.
+ **DCN** - *"Drawing Change Notice"* - DCNs are written against a master (drawing) to provide notice of a drawing change.
+ **ECM** - *"Engineering Change Memo"* - ECMs are written against a master (drawing) to document an engineering change.

### Document Model [/document/{id}]

A "Document" model has the following attributes:

+ **id** - *number* - The ESOC model id. **(primary key, unique)**
+ **documentNumber** - *string* - The SARAH document id. **(primary key SARAH, unique)**
+ **documentType** - *string* - The document's type.
+ **openDate** - *date* - The date the document was opened.
+ **closeDate** - *date* - The date the document was closed.
+ **documentTitle** - *string* - The document title.
+ **componentIds** - *array[strings]* - The applicable componentIds of the document.
+ **componentTracerControllerIds** - *array[strings]* - The applicable componentsTracerControllerIds of the document.
+ **lastUpdateDate** - *string* - The last update date.
+ **masters** - *array[objects]* - The applicable masters of the document.
+ **attributes** - *object* - The documents attributes (specific to it's type).
    > *See document specific attributes below*
    
+ Parameters
    + id: 1 (required, number) - ID of the desired document
    
#### Get Document Model [GET]

    URL
    /document/{id}
    

    PARAMETERS
    id: document's NEDi model id 

+ Response 200 (application/json)

        {
            "id": 1,
            "sarahDocumentId": "TPS-1234",
            "type": "TPS",
            "openDate": 01-01-2104,
            "title": "The way to fix the widget",
            "comments": "This is a comment on a TPS",
            "componentIds": ["abc123", "efg456"],
            "componentTracerControllerIds": ["a1b1c", "a2b2c2"],
            "lastUpdateDate": "01-01-2015",
            "masters": [{ }],
            "attributes": { }
        }
        
### Document Collection [/documents(?since)]

+ Parameters
    + since: 01/01/2014 (optional, date) - Only return records that have been updated since the parameter.'
    
#### Get Documents Collection [GET]

    URL
    /documents
    
    QUERY STRING OPTIONS
    since:  Only return records that have been updated since the parameter
    
+ Response 200 (application/json)

        [{
            "id": 1,
            "sarahDocumentId": "TPS-1234",
            "type": "TPS",
            "openDate": 01-01-2014,
            "title": "The way to fix the widget",
            "comments": "This is a comment on a TPS",
            "components": [{ }],
            "masters": [{ }],
            "attributes": { }
        }, {
            "id": 2,
            "sarahDocumentId": "DR-1234",
            "type": "DR",
            "openDate": 01-01-2013,
            "title": "The problem with the widget",
            "comments": "This is a comment on a DR",
            "components": [{ }],
            "masters": [{ }],
            "attributes": { }
            }
        }]
  
### DR Model [/document/dr/{id}]

A "DR" document type has the following attributes:

+ **id** - *number* - The ESOC model id. **(primary key, unique)**
+ **sarahDocumentId** - *string* - The SARAH document id. **(primary key SARAH, unique)**
+ **type** - *string* - The document's type.
+ **openDate** - *date* - The date the document was opened.
+ **closeDate** - *date* - The date the document was closed.
+ **title** - *string* - The document title.
+ **comments** - *string* - All comments added to the document.
+ **components** - *array[objects]* - The applicable components of the document.
+ **masters** - *array[objects]* - The applicable masters of the document.
+ **audit** - *object* - The Audit model for the DR 
+ **attributes** - object - The documents attributes (specific to it's type).
    + **dispositionTitle** - *string* - Short summary describing the solution to the discrepancy (DISP_TITLE||DISP_TITLE2)
    + **initiator** - *string* - Identification of the person that initiated the Work Authorizing Document
    + **wbs** - *number* - Work Breakdown Structure, a number indicating type of hardware (no longer used but has history) 
    + **mrb** - *string* - A flag (Y, N) to indicate whether Material Review Board (MRB) approval is required
    + **whenNoticed** - *number* - A numeric code defining when the discrepancy was noticed (reference table exists WHEN_NOTICED_REF)
    + **fault** - *number* - A numeric code defining the initial cause of the discrepancy (reference table exists FAULT_REF)
    + **hardware** - *number* - A numeric code to define the type of hardware that is discrepant (reference table exists HARDWARE_REF)
    + **cause** - *number* - A numeric code defining the root cause (real reason) of the discrepancy (reference table exists CAUSE_REF)
    + **disposition** - *number* - A numeric code defining the how the discrepancy was resolved (reference table exists DISP_REF)
    + **qualityControlStamp** - *string* - The stamp number of the Quality Control Inspector that signed off and closed the physical document
    + **flag** - *string* - ??? 1053 Records out of 117754 have flag = R
    + **manHour** - *number* - This is no longer used and there are only 3 records with data
    + **daysToClose** - *number* - The number indicating the amount of days it took from the last bought off step to the closure step.  (QRC has stated that this is no longer needed)
    + **openProblemNumber** - *number* - A 2-digit code indicating the type of problem encountered when closing the document.  The OPEN_PROBLEM_NO is manually validated against a list maintained in Data Management/Record Center.  There is no validation within SARAH.  (QRC has stated that this column is no longer needed but there is history)
    + **closeProblemNumber** - *number* - A 1 or 2 digit code indicating the type of problem encountered when closing the document.  The CLOSE_PROBLEM_NO is manually validated against a list maintained in Data Management/Record Center.  There is no validation within SARAH.  (QRC has stated that this column is no longer needed but there is history)
    + **interimDisposition** - *number* - Short title (verbage) describing the interim disposition or fix of the discrepancy (INTERIM_DISP1||INTERIM_DISP2)
    + **hasOpenShipper** - *bool* - A flag to indicate whether the DR (discrepancy report) will ship with the item as open paperwork (however, QRC has indicated no longer used)
    + **repairType** - *string* - A code defining the type of repair for the discrepancy (reference table exists DR_REPAIR_TYPES_REF)
    + **reOpen** - Flag (Y, N) used in both DR & TPS tables to track whether DR or TPS has been re-opened
    + **uaoNumber** - Use as Original.  Designates the number of copies being used as original
    + **isPracaReportable** - *bool* - A code defining if the DR is PRACA reportable or if it needs to go to the PRT for review (reference table exists PRACA_REPORTABLES) 
    + **fiarLimitExpirationDate** - *date* - A 21-day limit from open date of DR defines the expiration date for present to the PRT and defining if a FIAR is required
    + **docType** - *string* - A code to indicate the type of document being referenced (Reference table exists RECV_DOC_REF)
    + **labLocation** *string* – The physical location of the paperwork (LOCATION from the DROPEN_STATUS table)
    + **location** - *number* - A numeric code defining the where the discrepancy occurred (reference table exists LOCA_REF)
    + **refDoc** - *string* - Reference Document.  The related document that was being worked when discrepancy was discovered/occurred
    + **respOrg** - *string* - The organization that was responsible for the disposition of the discrepancy (Reference table exists RESP_ORG_REF)
    + **status** - *string* - The status (STATUS_CODE) of the open DR from DROPEN_STATUS table (reference table exists DR_STATCODE)
    + **transDate** - *string* - The date that the last item transaction occurred 
    + **lineItems** - *array[objects]* - The DR's line items
        + **component** - *object* - The EVA component model
        > [*see Component model*](http://docs.emuapi.apiary.io/#reference/components/component-model)
        + **flag** - ???
        + **LogCardNumber** - *string* - og Cards used to be used to document pressure time but this is no longer used and no data exists
        + **audit** - *object* - The Audit model for the DR line Item
        
+ Parameters
    + id: 1 (required, number) - ID of the desired DR
    
#### Get DR Model [GET]

+ Response 200 (application/json)

        {
            "id": 1,
            "sarahDocumentId": "DR-1234",
            "type": "DR",
            "openDate": 01-01-2104,
            "title": "The problem with the widget",
            "comments": "This is a comment on a DR",
            "components": [{ 
                "id": 1,
                "tracer": "12345abcdef",
                "masterId": 1,
                "itemNumber": "SVG1235"
            }, { 
                "id": 2,
                "tracer": "6789zxyv",
                "masterId": 1,
                "itemNumber": "SVG1236"
            }, { 
                "id": 3,
                "tracer": "5555asdf",
                "masterId": 1,
                "itemNumber": "SEMU987"
            }],
            "masters": [{
                    "id": 2,
                    "itemNumber": "1234ITEM",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678"
                }, {
                    "id": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123"
            }],
            "attributes": {
                "dispositionTitle": "Fixing leak in helmet",
                "initiator": "PKELLY",
                "wbs": 5,
                "mrb": "Y",
                "whenNoticed": 12,
                "fault": 3,
                "hardware": 15,
                "cause": 1
                "disposition": 6,
                "qualityControlStamp": "107B",
                "flag": "R",
                "manHour": 120,
                "daysToClose": 30,
                "openProblemNumber": 15,
                "closeProblemNumber": 9,
                "interimDisposition": 10,
                "hasOpenShipper": false,
                "repairType": "Refurb",
                "reOpen": "N",
                "uaoNumber": 2,
                "isPracaReportable": true,
                "fiarLimitExpirationDate": 05-15-2015,
                "docType": "Drawing",
                "labLocation": "LTX",
                "location": 20,
                "refDoc": "100B10",
                "respOrg": "UTAS",
                "status": "1B",
                "transDate": 05-10-2015,
                "lineItems": [
                   {
                        "component": {
                            "id": 1,
                            "tracer": "12345abcdef",
                            "masterId": 1,
                            "itemNumber": "SVG1235",
                            "description": "EMU GLOVE",
                            "drawingNumber": "1234Draw",
                            "serialNumber": "3001",
                            "lotNumber": null,
                            "side": "right",
                            "itemSize": "YG"
                        },
                        "flag": "R",
                        "logCardNumber": "AB11",
                        "audit": {}
                   },
                   {
                        "component": {
                            "id": 2,
                            "tracer": "54231abcdef",
                            "masterId": 1,
                            "itemNumber": "SVG2343",
                            "description": "EMU GLOVE",
                            "drawingNumber": "43244Draw",
                            "serialNumber": "3002",
                            "lotNumber": null,
                            "side": "right",
                            "itemSize": "YG"
                        },
                        "flag": "R",
                        "logCardNumber": "AB12",
                        "audit": {}
                    }
                ]
            }
        }
        
### DR Collection [/document/drs(?since)]

+ Parameters
    + since: 01/01/2014 (optional, date) - Only return records that have been updated since the parameter.'
    
#### Get DR Collection [GET]

    URL
    /document/drs
    
    QUERY STRING OPTIONS
    since:  Only return records that have been updated since the parameter
    
+ Response 200 (application/json)

        [{
            "id": 1,
            "sarahDocumentId": "DR-1234",
            "type": "DR",
            "openDate": 01-01-2104,
            "title": "The problem with the widget",
            "comments": "This is a comment on a DR",
            "components": [{ 
                "id": 1,
                "tracer": "12345abcdef",
                "masterId": 1,
                "itemNumber": "SVG1235"
            }, { 
                "id": 2,
                "tracer": "6789zxyv",
                "masterId": 1,
                "itemNumber": "SVG1236"
            }, { 
                "id": 3,
                "tracer": "5555asdf",
                "masterId": 1,
                "itemNumber": "SEMU987"
            }],
            "masters": [{
                    "id": 2,
                    "itemNumber": "1234ITEM",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678"
                }, {
                    "id": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123"
            }],
            "attributes": {
                "dispositionTitle": "Fixing leak in helmet",
                "initiator": "PKELLY",
                "wbs": 5,
                "mrb": "Y",
                "whenNoticed": 12,
                "fault": 3,
                "hardware": 15,
                "cause": 1
                "disposition": 6,
                "qualityControlStamp": "107B",
                "flag": "R",
                "manHour": 120,
                "daysToClose": 30,
                "openProblemNumber": 15,
                "closeProblemNumber": 9,
                "interimDisposition": 10,
                "hasOpenShipper": false,
                "repairType": "Refurb",
                "reOpen": "N",
                "uaoNumber": 2,
                "isPracaReportable": true,
                "fiarLimitExpirationDate": 05-15-2015,
                "docType": "Drawing",
                "labLocation": "LTX",
                "location": 20,
                "refDoc": "100B10",
                "respOrg": "UTAS",
                "status": "1B",
                "transDate": 05-10-2015,
                "lineItems": [
                   {
                        "component": {
                            "id": 1,
                            "tracer": "12345abcdef",
                            "masterId": 1,
                            "itemNumber": "SVG1235",
                            "description": "EMU GLOVE",
                            "drawingNumber": "1234Draw",
                            "serialNumber": "3001",
                            "lotNumber": null,
                            "side": "right",
                            "itemSize": "YG"
                        },
                        "flag": "R",
                        "logCardNumber": "AB11",
                        "audit": {}
                   },
                   {
                        "component": {
                            "id": 2,
                            "tracer": "12345abcdef",
                            "masterId": 2,
                            "itemNumber": "SVG1235",
                            "description": "EMU GLOVE",
                            "drawingNumber": "1234Draw",
                            "serialNumber": "3001",
                            "lotNumber": null,
                            "side": "left",
                            "itemSize": "YG"
                        },
                        "flag": "R",
                        "logCardNumber": "AB12",
                        "audit": {}
                    }
                ]
            }
        },
        {
            "id": 2,
            "sarahDocumentId": "DR-5002",
            "type": "DR",
            "openDate": 01-01-2104,
            "title": "Blocked relief valve, preventing drain from operating properly",
            "comments": "This is a comment on another DR",
           "components": [{ 
                "id": 1,
                "tracer": "12345abcdef",
                "masterId": 1,
                "itemNumber": "SVG1235"
            }, { 
                "id": 2,
                "tracer": "6789zxyv",
                "masterId": 1,
                "itemNumber": "SVG1236"
            }, { 
                "id": 3,
                "tracer": "5555asdf",
                "masterId": 1,
                "itemNumber": "SEMU987"
            }],
            "masters": [{
                    "id": 2,
                    "itemNumber": "1234ITEM",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678"
                }, {
                    "id": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123"
            }],
            "attributes": {
                "dispositionTitle": "Clear relief valve blockage",
                "initiator": "PKELLY",
                "wbs": 5,
                "mrb": "Y",
                "whenNoticed": 12,
                "fault": 3,
                "hardware": 15,
                "cause": 1
                "disposition": 6,
                "qualityControlStamp": "103C",
                "flag": "R",
                "manHour": 20,
                "daysToClose": 10,
                "openProblemNumber": 12,
                "closeProblemNumber": 15,
                "interimDisposition": 3,
                "hasOpenShipper": false,
                "repairType": "Refurb",
                "reOpen": "N",
                "uaoNumber": 2,
                "isPracaReportable": true,
                "fiarLimitExpirationDate": 05-15-2015,
                "docType": "Drawing",
                "labLocation": "LTX",
                "location": 20,
                "refDoc": "100B10",
                "respOrg": "UTAS",
                "status": "1B",
                "transDate": 05-10-2015,
                "lineItems": [
                   {
                        "component": {
                            "id": 1,
                            "tracer": "12345abcdef",
                            "masterId": 1,
                            "itemNumber": "SVG1235",
                            "description": "EMU GLOVE",
                            "drawingNumber": "1234Draw",
                            "serialNumber": "3001",
                            "lotNumber": null,
                            "side": "right",
                            "itemSize": "YG"
                        },
                        "flag": "R",
                        "logCardNumber": "AD11",
                        "audit": {}
                   },
                   {
                        "component": {
                            "id": 1,
                            "tracer": "12345abcdef",
                            "masterId": 2,
                            "itemNumber": "SVG1235",
                            "description": "EMU GLOVE",
                            "drawingNumber": "1234Draw",
                            "serialNumber": "3002",
                            "lotNumber": null,
                            "side": "left",
                            "itemSize": "YG"
                        },
                        "flag": "R",
                        "logCardNumber": "AD12",
                        "audit": {}
                    }
                ]
            }
        }]
        
### TPS Model [/document/tps/{id}]

A "TPS" document type has the following attributes:

+ **id** - *number* - The ESOC model id. **(primary key, unique)**
+ **sarahDocumentId** - *string* - The SARAH document id. **(primary key SARAH, unique)**
+ **type** - *string* - The document's type.
+ **openDate** - *date* - The date the document was opened.
+ **closeDate** - *date* - The date the document was closed.
+ **title** - *string* - The document title.
+ **comments** - *string* - All comments added to the document.
+ **components** - *array[objects]* - The applicable components of the document.
+ **masters** - *array[objects]* - The applicable masters of the document.
+ **audit** - *object* - The Audit model for the TPS
+ **attributes** - object - The documents attributes (specific to it's type).
    + **orderNumber** - *string*  - The number designating a specific document.
    + **orderStatus** - *string*   - The status of a TPS, "H" for Hold and "D" for Done.
    + **isSeeBelow** -  *boolean* -  A Y/N flag to designate if the tracer of the top assembly is uniquely identified by having the drawingNumber, itemNumber, side, itemSize, serialNumber and lotNumbervalues as applicable, or there is no top assembly and all pertinent details of the hardware to be worked on are spelled out in the text or picklist.  
    + **dueDate** -  *date* -  The date that the work on the order must be completed.
    + **itemNumber** - *string*  - Unique identifier for an item.
    + **tracer** - *string*  -  Unique identifier for an item. It consists of drawing number, serial number, lot number, side and size.
    + **drawingNumber** - *string*  -  Unique identifier for a drawing.
    + **asbuiltNumber** - *string*  - A configuration version number of a drawing.
    + **serialNumber** - *string*  - Unique identifier for a specific instance of an item.
    + **lotNumber** - *string*  - The lot number of a group of similiar items.
    + **side** - *string*  - Designates an item as right or left.
    + **itemSize** - *string*  - Designates the size of an item.
    + **itemClass** - *string*  - This is the quality class of an item.
    + **description** - *string*   -  Nomenclature for describing an item.
    + **dateComplete** - *date* -   The date when the FAB was completed.
    + **quantityOrdered** -  *number* -  Quantity of material/services to be acquired.
    + **title** - *string*  - Words describing the purpose or objective of the document.
    + **contractNumber** - *string*  -  Contract number against which an item is acquired/tracked.
    + **estimateBeginDate** - *date* -  The date used to indicate to processing personnel when the processing of the item will begin.
    + **estimateEndDate** - *date* -  The date the work on the order is estimated to be completed.
    + **releasedDate** -  *date* -  The date the TPS was released.
    + **routingRevision** - *string*  -  The number of the Master TPS from which this working TPS was derived.
    + **initiator** - *string*   -  Identification of the person that initiated the TPS.
    + **typeTPS** - *string*  - A code to indicate whether the TPS performed a configuration change to the hardware.  A = configuration change.  B = non configuration change.
    + **engineeringApproval** -  *boolean* -  Indicates whether engineering approval is required for this TPS.
    + **qualityApproval** -  *boolean* -  Indicates whether Quality Engineering approval is required for this TPS.
    + **nasaApproval** -  *boolean* -  Indicates whether NASA approval is required for this TPS.
    + **startDate** - *date* -  The date on which the TPS or modsheet was created.
    + **applicableDocument** - *string*   - Document or event that authorized the creation of the working TPS
    + **area** - *string*  -  Identifies what kind of hardware is being processed.
    + **labelNumber** - *string*   -  The charge number to which all charges for this TPS are to be charged.
    + **permanentTemporaryCode** - *string*   -  A code to indicate if configuration change to an item is permanent or temporary. “P” = Permanent, “T” = Temporary.
    + **isTimeCycle** -  *boolean* -  Indicates to Quality Records Center personnel if update(s) to time/cycle data is required.
    + **isQAonly** -  *boolean* -   “Y” means the inspection(s) on this TPS must be performed by Quality Personnel only. "N" means that the inspection can be performed by Designated Inspectors (DIs) in lieu of a Quality person.
    + **approvalCode** - *string*  - The approval_status of the TPS (N=Not approved by any organization yet, P=Pending Final Approval, R=Rejected, Y=Fully Approved)
    + **approvalDate** - *date* -   The date of the final approval of the TPS.
    + **prePostCode** - *string*   -  A code indicating whether the TPS applies to "P" Postflight activities, "R" Preflight activities, "B" Both Pre- and Post-Flight activities, or "O" Other (neither Pre- nor Post- Flight) activities.  
    + **modsheets** -  *number* - Sequential number for a modification to the basic order number.  
    + **tpsTag** - *string*   - An identifier indicating a specific TPS (Used before the TPS has an order number assigned; can be used as an alternate to the order number or modsheet).
    + **procedure** -  *Array[Objects]* -  The operational steps for a working TPS.
    + **operationSequence** -  *number* -  A number indicating the sequence in which operational steps are to be performed.
    + **lineNumber** - *number* - A number used to order multiple text lines or steps in a multi-step operation.
    + **MIP** - *string*   -  A code “<M>” to indicate the operation step is a Mandatory Inspection Point (MIP) where the inspector must sign off. Other values are <T> where Technician Stamp required; <O> where other discipline’s stamp required (like Property, QRC, etc)
    + **operationText** - *string*   -   the wording of the operation step.
    + **pickList** -  *Array[Objects]* -  The hardware list for a working TPS.
    + **hardwareCode** - *string*   -  A code indicating what is to be done with the item at that particular operation sequence. (P = Pick and issue out, T = Transfer to another location, R = Return component to stores, D = Documentation only, I = Incorporate into the higher assembly, F = Floor Stock).
    + **expendRefurbCode** - *string*  -  A code to indicate whether the component item is expendable or refurbishable.
    + **componentNumber** - *string*  -  The item number of the component item.
    + **componentDescription** - *string*   -  The description of the component item.
    + **componentTracer** - *string*   -  The tracer of the component item.
    + **componentDrawingNumber** - *string*   -  The drawing number of the component item.
    + **componentAsbuiltNumber** - *string*   -  The as-built number of the component item.
    + **componentSerialNumber** - *string*   -  The serial number (if any) of the component item.
    + **componentLotNumber** - *string*   -  The lot number (if any) of the component item.
    + **componentSide** - *string*   -  Designates the component item as right or left.
    + **componentSize** - *string*  - Designates the size of the component item.
    + **isSerial** - *boolean* - Indicates if  the component item is serial controlled.
    + **isLot** - *boolean* - Indicates if  the component item is lot controlled.
    + **isShelfLifeSuspend** -  *boolean* - Indicates if the shelf life of the component item has been suspended.
    + **shelfLife** - *date* -  The shelf life expiration date of the component item.
    + **usageLife** -  *date* -  The usage life expiration date of the component item.
    + **operationLife** - *date* -  The operation life expiration date of the component item.
    + **componentItemClass** - *string*  -  The quality class of the component item.
    + **componentQuantityPer** -  *number* -  Quantity required for the component item.
    + **componentQuantityRequired** -  *number* -  The total amount of the component required to make the desired number of higher assemblies
    + **componentUnitOfMeasure** - *string*   -  The stock unit measure of the component item.
    + **alternateComponentNumber** - *string*   -  Indicates an item which can be used in lieu of the specified component item.
    + **alternateComponentDescription** - *string*   -  The description of the alternate component item.
    
    
+ Parameters
    + id: 1 (required, number) - ID of the desired TPS
    
#### Get TPS Model [GET]

    URL
    /document/tps/{id}
    

    PARAMETERS
    id: document's NEDi model id or document's sarahDocumentId id from SARAH

+ Response 200 (application/json)

        {
            "id": 1,
            "sarahDocumentId": "TPS-1234",
            "type": "TPS",
            "openDate": 01-01-2104,
            "title": "The steps to fix the widget",
            "comments": "This is a comment on a TPS",
            "components": [{ 
                "id": 1,
                "tracer": "12345abcdef",
                "masterId": 1,
                "itemNumber": "SVG1235"
            }, { 
                "id": 2,
                "tracer": "6789zxyv",
                "masterId": 1,
                "itemNumber": "SVG1236"
            }, { 
                "id": 3,
                "tracer": "5555asdf",
                "masterId": 1,
                "itemNumber": "SEMU987"
            }],
            "masters": [{
                    "id": 2,
                    "itemNumber": "1234ITEM",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678"
                }, {
                    "id": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123"
            }],
            "attributes": { 
                "orderNumber": "1A300",
                "orderStatus": "H",
                "isSeeBelow": True,
                "dueDate": 05-3-2015,
                "itemNumber": "B200",
                "tracer": "1A300B200LSM",
                "drawingNumber": "1A",
                "asbuiltNumber": "300",
                "serialNumber": "B200",
                "lotNumber": "C4",
                "side": "L",
                "itemSize": "SM",
                "itemClass": "FAB",
                "description": "a very good description of the this item",
                "dateComplete": 06-2-2015,
                "quantityOrdered": 10,
                "title": "EMU visor assembly",
                "contractNumber": "1EVA2003CB4",
                "estimateBeginDate": 10-7-2015,
                "estimateEndDate": 12-10-2015,
                "releasedDate": 10-1-2015,
                "routingRevision": "B4",
                "initiator": "RGILL",
                "typeTPS": "B",
                "qualityApproval": False,
                "nasaApproval": True,
                "startDate": 10-8-2015,
                "applicableDocument": "B200EVA12",
                "area": "EMU",
                "labelNumber": "NES",
                "permanentTemporaryCode": "P",
                "isQAonly": True,
                "approvalCode": "R",
                "approvalDate": 10-10-2015,
                "prePostCode": "B",
                "modsheets": 9,
                "tpsTag": "T100B6",
                "procedure": [{}, {}, ... ],
                "operationSequence": 3,
                "lineNumber": 20,
                "MIP": "M",
                "operationText": "Remove the metal shavings",
                "pickList": [{}, {}, ... ],
                "hardwareCode": "D",
                "expendRefurbCode": "EXP",
                "componentNumber": "C10B200",
                "componentDescription": "Ball joint",
                "componentTracer": "T1002",
                "componentDrawingNumber": "B2A1",
                "componentAsbuiltNumber": "100B",
                "componentSerialNumber": "42001285",
                "componentLotNumber": "B100",
                "componentSide": "L",
                "componentSize": "LG",
                "isSerial": True,
                "isLot": False,
                "isShelfLifeSuspend": True,
                "shelfLife": 9-1-2015,
                "usageLife": 9-1-2016,
                "operationLife": 9-1-2018,
                "componentItemClass": "EVA",
                "componentQuantityPer": 4,
                "componentQuantityRequired": 8,
                "componentUnitOfMeasure": "inches",
                "alternateComponentNumber": "B100C",
                "alternateComponentDescription": "U joint"
            }
        }
        
### TPS Collection [/document/tpss(?since)]

+ Parameters
    + since: 01/01/2014 (optional, date) - Only return records that have been updated since the parameter.'
    
#### Get TPS Collection [GET]

    URL
    /document/tpss
    
    QUERY STRING OPTIONS
    since:  Only return records that have been updated since the parameter
    
+ Response 200 (application/json)

        [{
            "id": 1,
            "sarahDocumentId": "TPS-3334",
            "type": "TPS",
            "openDate": 01-01-2104,
            "title": "The steps to fix the widget",
            "comments": "This is a comment on a TPS",
            "components": [{ 
                "id": 1,
                "tracer": "12345abcdef",
                "masterId": 1,
                "itemNumber": "SVG1235"
            }, { 
                "id": 2,
                "tracer": "6789zxyv",
                "masterId": 1,
                "itemNumber": "SVG1236"
            }, { 
                "id": 3,
                "tracer": "5555asdf",
                "masterId": 1,
                "itemNumber": "SEMU987"
            }],
            "masters": [{
                    "id": 2,
                    "itemNumber": "1234ITEM",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678"
                }, {
                    "id": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123"
            }],
            "attributes": { 
                "orderNumber": "2A300",
                "orderStatus": "H",
                "isSeeBelow": True,
                "dueDate": 05-3-2015,
                "itemNumber": "B200",
                "tracer": "1A300B200LSM",
                "drawingNumber": "1A",
                "asbuiltNumber": "300",
                "serialNumber": "B200",
                "lotNumber": "C4",
                "side": "L",
                "itemSize": "SM",
                "itemClass": "FAB",
                "description": "a very good description of the this item",
                "dateComplete": 06-2-2015,
                "quantityOrdered": 10,
                "title": "EMU visor assembly",
                "contractNumber": "1EVA2003CB4",
                "estimateBeginDate": 10-7-2015,
                "estimateEndDate": 12-10-2015,
                "releasedDate": 10-1-2015,
                "routingRevision": "B4",
                "initiator": "RGILL",
                "typeTPS": "B",
                "qualityApproval": False,
                "nasaApproval": True,
                "startDate": 10-8-2015,
                "applicableDocument": "B200EVA12",
                "area": "EMU",
                "labelNumber": "NES",
                "permanentTemporaryCode": "P",
                "isQAonly": True,
                "approvalCode": "R",
                "approvalDate": 10-10-2015,
                "prePostCode": "B",
                "modsheets": 9,
                "tpsTag": "T100B6",
                "procedure": [{}, {}, ... ],
                "operationSequence": 3,
                "lineNumber": 20,
                "MIP": "M",
                "operationText": "Remove the metal shavings",
                "pickList": [{}, {}, ... ],
                "hardwareCode": "D",
                "expendRefurbCode": "EXP",
                "componentNumber": "C10B200",
                "componentDescription": "Ball joint",
                "componentTracer": "T1002",
                "componentDrawingNumber": "B2A1",
                "componentAsbuiltNumber": "100B",
                "componentSerialNumber": "42001285",
                "componentLotNumber": "B100",
                "componentSide": "L",
                "componentSize": "LG",
                "isSerial": True,
                "isLot": False,
                "isShelfLifeSuspend": True,
                "shelfLife": 9-1-2015,
                "usageLife": 9-1-2016,
                "operationLife": 9-1-2018,
                "componentItemClass": "EVA",
                "componentQuantityPer": 4,
                "componentQuantityRequired": 8,
                "componentUnitOfMeasure": "inches",
                "alternateComponentNumber": "B100C",
                "alternateComponentDescription": "U joint"
            }
        },
        {
            "id": 2,
            "sarahDocumentId": "TPS-4567",
            "type": "TPS",
            "openDate": 01-01-2104,
            "title": "The steps to fix the widget, the first time",
            "comments": "This is a comment on another TPS",
            "components": [{ 
                "id": 1,
                "tracer": "12345abcdef",
                "masterId": 1,
                "itemNumber": "SVG1235"
            }, { 
                "id": 2,
                "tracer": "6789zxyv",
                "masterId": 1,
                "itemNumber": "SVG1236"
            }, { 
                "id": 3,
                "tracer": "5555asdf",
                "masterId": 1,
                "itemNumber": "SEMU987"
            }],
            "masters": [{
                    "id": 2,
                    "itemNumber": "1234ITEM",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678"
                }, {
                    "id": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123"
            }],
            "attributes": { 
                "orderNumber": "1A300",
                "orderStatus": "H",
                "isSeeBelow": True,
                "dueDate": 05-3-2015,
                "itemNumber": "B200",
                "tracer": "1A300B200LSM",
                "drawingNumber": "1A",
                "asbuiltNumber": "300",
                "serialNumber": "B200",
                "lotNumber": "C4",
                "side": "L",
                "itemSize": "SM",
                "itemClass": "FAB",
                "description": "a very good description of the this item",
                "dateComplete": 06-2-2015,
                "quantityOrdered": 10,
                "title": "EMU visor assembly",
                "contractNumber": "1EVA2003CB4",
                "estimateBeginDate": 10-7-2015,
                "estimateEndDate": 12-10-2015,
                "releasedDate": 10-1-2015,
                "routingRevision": "B4",
                "initiator": "RGILL",
                "typeTPS": "B",
                "qualityApproval": False,
                "nasaApproval": True,
                "startDate": 10-8-2015,
                "applicableDocument": "B200EVA12",
                "area": "EMU",
                "labelNumber": "NES",
                "permanentTemporaryCode": "P",
                "isQAonly": True,
                "approvalCode": "R",
                "approvalDate": 10-10-2015,
                "prePostCode": "B",
                "modsheets": 9,
                "tpsTag": "T100B6",
                "procedure": [{}, {}, ... ],
                "operationSequence": 3,
                "lineNumber": 20,
                "MIP": "M",
                "operationText": "Remove the metal shavings",
                "pickList": [{}, {}, ... ],
                "hardwareCode": "D",
                "expendRefurbCode": "EXP",
                "componentNumber": "C10B200",
                "componentDescription": "Ball joint",
                "componentTracer": "T1002",
                "componentDrawingNumber": "B2A1",
                "componentAsbuiltNumber": "100B",
                "componentSerialNumber": "42001285",
                "componentLotNumber": "B100",
                "componentSide": "L",
                "componentSize": "LG",
                "isSerial": True,
                "isLot": False,
                "isShelfLifeSuspend": True,
                "shelfLife": 9-1-2015,
                "usageLife": 9-1-2016,
                "operationLife": 9-1-2018,
                "componentItemClass": "EVA",
                "componentQuantityPer": 4,
                "componentQuantityRequired": 8,
                "componentUnitOfMeasure": "inches",
                "alternateComponentNumber": "B100C",
                "alternateComponentDescription": "U joint"
            }
        }]
        
### EC Model [/document/ec/{id}]

A "EC" document type has the following attributes:

+ **id** - *number* - The ESOC model id. **(primary key, unique)**
+ **sarahDocumentId** - *string* - The SARAH document id. **(primary key SARAH, unique)**
+ **type** - *string* - The document's type.
+ **title** - *string* - The document title.
+ **comments** - *string* - All comments added to the document. 
+ **components** - *array[objects]* - The applicable components of the document.
+ **masters** - *array[objects]* - The applicable masters of the document. (???)
+ **audit** - *object* - The Audit model for the EC
+ **attributes** - *object* - The documents attributes (specific to it's type).
    + **ccbdNumber** - *string* - Configuration Control Board Directive tracking number generated by NASA
    + **effectiveDate** - *date* - The date when the Engineering Change becomes effective
    + **effectivity** - *object* - The disposition for effectivity to incorporate the modification into the hardware *(defined list)* 
        + **effectiveDescription** - *string* - the description of the effectivity.  
        + **effectiveCode** - *string* - Example: AA, XB
    + **effectiveFlight** - *string* - Mandatory ECs’ identified specific flight and/or subsequent flights for which the EC is effective. 
    + **tdDocNumber** - *string* - Identifier for a Technical Directive number from the Project Office giving direction to proceed with incorporation of the change
    + **lineItems** - *array[objects]* - The EC's line items
        + **component** - *object* - The EVA component model
        > [*see Component model*](http://docs.emuapi.apiary.io/#reference/components/component-model)
        + **rollDash** - *string* - The configuration (dash number) the part rolls to authorized by the Engineering Change
        + **authority** - *string* - The document that incorporated the EC for the specific line Item
        + **openDate** - *date* - The date the line item was opened.
        + **closeDate** - *date* - The date the line item was closed.
        + **audit** - *object* - The Audit model for the EC line Item


    
+ Parameters
    + id: 1 (required, number) - ID of the desired EC
    
#### Get EC Model [GET]

    URL
    /document/ec/{id}
    

    PARAMETERS
    id: document's NEDi model id or document's sarahDocumentId id from SARAH
    
+ Response 200 (application/json)

        {
            "id": 1,
            "sarahDocumentId": "EC-1234",
            "type": "EC",
            "openDate": 01-01-2104,
            "title": "The change to the widget",
            "comments": "This is a comment on a EC",
            "components": [{ 
                "id": 1,
                "tracer": "12345abcdef",
                "masterId": 1,
                "itemNumber": "SVG1235"
            }, { 
                "id": 2,
                "tracer": "6789zxyv",
                "masterId": 1,
                "itemNumber": "SVG1236"
            }, { 
                "id": 3,
                "tracer": "5555asdf",
                "masterId": 1,
                "itemNumber": "SEMU987"
            }],
            "masters": [{
                    "id": 2,
                    "itemNumber": "1234ITEM",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678"
                }, {
                    "id": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123"
            }],
            "attributes": { 
                "ccbdNumber": "ABC123",
                "effectiveDate": 05-20-2015,
                "effectivity": {
                    "effectiveDescription": "Effective immediately for all NASA employees",
                    "effectiveCode": "AA"
                }
                "effectiveFlight": "STS-12",
                "tdDocNumber": "B120",
                "lineItems": [
                    {
                        "component": {},
                        "rollDash": "A105",
                        "authority": "BCK",
                        "openDate": 05-15-2015,
                        "closeDate": 06-11-2015,
                        "audit": {}
                    },
                    {
                        "component": {},
                        "rollDash": "A200",
                        "authority": "BCK",
                        "openDate": 03-11-2015,
                        "closeDate": 04-21-2015,
                        "audit": {}
                    }
                ]
            }
        }
        
### EC Collection [/document/ecs(?since)]

+ Parameters
    + since: 01/01/2014 (optional, date) - Only return records that have been updated since the parameter.'
    
#### Get EC Collection [GET]

    URL
    /document/ecs
    
    QUERY STRING OPTIONS
    since:  Only return records that have been updated since the parameter
    
+ Response 200 (application/json)

        [{
            "id": 1,
            "sarahDocumentId": "EC-1234",
            "type": "EC",
            "openDate": 01-01-2104,
            "title": "The steps to fix the widget",
            "comments": "This is a comment on a EC",
            "components": [{ 
                "id": 1,
                "tracer": "12345abcdef",
                "masterId": 1,
                "itemNumber": "SVG1235"
            }, { 
                "id": 2,
                "tracer": "6789zxyv",
                "masterId": 1,
                "itemNumber": "SVG1236"
            }, { 
                "id": 3,
                "tracer": "5555asdf",
                "masterId": 1,
                "itemNumber": "SEMU987"
            }],
            "masters": [{
                    "id": 2,
                    "itemNumber": "1234ITEM",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678"
                }, {
                    "id": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123"
            }],
            "attributes": { 
                "ccbdNumber": "ABC123",
                "effectiveDate": 05-20-2015,
                "effectivity": {
                    "effectiveDescription": "Effective immediately for all NASA employees",
                    "effectiveCode": "AA"
                }
                "effectiveFlight": "STS-12",
                "tdDocNumber": "B120",
                "lineItems": [
                    {
                        "component": {},
                        "rollDash": "A105",
                        "authority": "BCK",
                        "openDate": 05-15-2015,
                        "closeDate": 06-11-2015,
                        "audit": {}
                    },
                    {
                        "component": {},
                        "rollDash": "A200",
                        "authority": "BCK",
                        "openDate": 03-11-2015,
                        "closeDate": 04-21-2015,
                        "audit": {}
                    }
                ]
            }
        },
        {
            "id": 2,
            "sarahDocumentId": "EC-1242",
            "type": "EC",
            "openDate": 01-01-2104,
            "title": "The steps to fix the widget, the first time",
            "comments": "This is a comment on another EC",
            "components": [{ 
                "id": 1,
                "tracer": "12345abcdef",
                "masterId": 1,
                "itemNumber": "SVG1235"
            }, { 
                "id": 2,
                "tracer": "6789zxyv",
                "masterId": 1,
                "itemNumber": "SVG1236"
            }, { 
                "id": 3,
                "tracer": "5555asdf",
                "masterId": 1,
                "itemNumber": "SEMU987"
            }],
            "masters": [{
                    "id": 2,
                    "itemNumber": "1234ITEM",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678"
                }, {
                    "id": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123"
            }],
            "attributes": { 
                "ccbdNumber": "ABC123",
                "effectiveDate": 05-20-2015,
                "effectivity": {
                    "effectiveDescription": "Effective immediately for all NASA employees",
                    "effectiveCode": "AA"
                }
                "effectiveFlight": "STS-12",
                "tdDocNumber": "B120",
                "lineItems": [
                    {
                        "component": {},
                        "rollDash": "A145",
                        "authority": "BWN",
                        "openDate": 09-15-2014,
                        "closeDate": 10-11-2014,
                        "audit": {}
                    },
                    {
                        "component": {},
                        "rollDash": "A230",
                        "authority": "BWN",
                        "openDate": 02-05-2014,
                        "closeDate": 04-16-2014,
                        "audit": {}
                    }
                ]
            }
        }]

### FAB Model [/document/fab/{id}]

A "FAB" document type has the following attributes:

+ **id** - *number* - The ESOC model id. **(primary key, unique)**
+ **sarahDocumentId** - *string* - The SARAH document id. **(primary key SARAH, unique)**
+ **type** - *string* - The document's type.
+ **openDate** - *date* - The date the document was opened.
+ **closeDate** - *date* - The date the document was closed.
+ **title** - *string* - The document title.
+ **comments** - *string* - All comments added to the document.
+ **components** - *array[objects]* - The applicable components of the document.
+ **masters** - *array[objects]* - The applicable masters of the document.
+ **audit** - *object* - The Audit model for the FAB
+ **attributes** - *object* - The documents attributes (specific to it's type).
    + **orderNumber** - *string* - The number designating a specific document.
    + **orderType** - *string* - The type of work authorizing document.
    + **orderStatus** - *string* - The status of a FAB. "I" for initiated, "P" for pendingIE scheduling, “C” for Closed or "X" to cancel.
    + **dueDate** - *date* - The date that the work on the order must be completed.
    + **itemNumber** - *string* - Unique identifier for an item.
    + **tracer** - *string* - Unique identifier for an item. It consists of drawing number, serial number, lot number, side and size.
    + **drawingNumber** - *string* - Unique identifier for a drawing.
    + **asbuiltNumber** - *string* - A configuration version number of a drawing.
    + **serialNumber** - *string* - Unique identifier for a specific instance of an item.
    + **lotNumber** - *string* - The lot number of a group of similiar items.
    + **side** - *string* - Designates an item as right or left.
    + **itemSize** - *string* - Designates the size of an item.
    + **itemClass** - *string* - This is the quality class of an item.
    + **description** - *string* - Nomenclature for describing an item.
    + **isDCN** - *boolean* - A Yes / No flag indicating whether the document has a Drawing Change Notice. 
    + **dateComplete** - *date* - The date when the FAB was completed closed.
    + **quantityOrdered** - *number* - Quantity of material/services to be acquired involved (to be built/fabricated) on the FAB.
    + **title** - *string* - Words describing the purpose or objective of the document(title1).
    + **contractNumber** - *string* - Contract number against which an item is acquired/tracked and what contract the work should be charged.
    + **estimateBeginDate** - *date* - The date used to indicate to processing personnel when the processing of the item will begin.
    + **estimateEndDate** - *date* - The date the work on the order is estimated to be completed.
    + **area** - *string* - Identifies what kind of hardware is being processedand what lab will work the paperwork.  Aids in creating the TPS number.
    + **drawingRevision** - *string* - The revision number of the drawing number to which this FAB is to be processed. 
    + **authority** - *string* - The authority under which the working revision of the MasterFAB was created.
    + **laborLabelNumber** - *string* - The label number to which labor on this FAB is to be charged.
    + **materialLabelNumber** - *string* - The label number to which material on this FAB is to be charged
    + **releaseAuthority** - *string* - Indicates the authority to release a working FAB.
    + **FABtype** - *string* - Designates both the intended use of the item(s) which will be processed on the FAB, as well as the Inspection Level required
    + **FABrevision** - *string* - The current revision of theMaster FABbeing used for the working FAB.
    + **totalAttachment** - *number* - The number of attachments which accompany the printed Working FAB (i.e. drawings, sketches, procedures, etc)
    + **unitCost** - *number* - The per-unit cost of the item being fabricated.
    + **totalCost** - *number* - : Calculated value and is the total cost of the item(s) being fabricated (unitCost * quantityOrdered).
    + **originalDueDate** - *date* - The original due date that can be compared to current due date.
    + **originalStartDate** - *date* - The original date where the work on the Fab was scheduled to start.
    + **originalEndDate** - *date* - The original date when the work on the FAB was due to be completed. 
    + **hasRedline** - *boolean* - "Y" indicates that the FAB was modified (redlined) on the floor. "N" indicates that the FAB was not changed (redlined) before completion.
    + **actualDrawingRevision** - *string* - The revision of the top assembly drawing number to which the top assembly of a red-lined FAB is actually built, as opposed to the top assembly drawing number in effect at the time the FAB was issued.
    + **actualFABRevision** - *string* - The actual FAB revision a red-lined FAB is built to, as opposed to the FAB_REV, which is FAB revision in effect at the time the FAB was issued.
    + **actualQuantityBuilt** - *number* - The quantity of the item actually built on the FAB.
    + **stockUnitMeasure** - *string* - Stock unit of measure.
    + **status** - *string* - The status of a FAB:  “initiated”, "pending” (scheduling) or “cancelled”.
    + **hasDCN** - *boolean* -  A true / flag flag indicating whether the document has a Drawing Change Notice. 
    + **type** - *string* - Designates both the intended use of the item(s) which will be processed on the FAB, as well as the Inspection Level required
    + **revision** - *string* - The current revision of the FAB.   
    + **procedure** - *array[objects]* : The operational steps for a working FAB.
        + **organizationCode** -  *string* - A code to define what organization is responsible for the action.
        + **operationSequence** -  *number* - A number indicating the sequence in which operational steps are to be performed.
        + **requiresInspection** -  *bool* - Indicate if the operation step is a Mandatory Inspection Point (MIP) where the inspector must sign off.
        + **standardTextNumber** -  *number* - The identification of a set of standard text.
        + **lineNumber** - *number* - A number used to order multiple lines of items within one Operation Sequence.
        + **operationText** -  *string* -  the wording of the operation step.
        + **components** -  *array[objects]* - The hardware list for a  master FAB.
        + **operationSequence** -  *number* - A number indicating the sequence in which operational steps are to be performed.
        + **hardwareCode** -  *string* - A code indicating what is to be done with the item at that particular operation sequence. (P = Pick and issue out, T = Transfer to another location, R = Return component to stores, D = Documentation only, I = Incorporate into the higher assembly, F = Floor Stock).
        + **component** -  *object* - The component being used with this FAB.
        + **componentQuantityPer** -  *number* - Quantity required for the component item.
        + **componentQuantityRequired** -  *number* - The total amount of the component required to make the desired number of higher assemblies.
        + **componentUnitOfMeasure** -  *string* - The stock unit measure of the component item.
        + **alternateMaster** -  *object* - Indicates an master (component type) which can be used in lieu of the specified component item.

+ Parameters
    + id: 1 (required, number) - ID of the desired FAB
    
#### Get FAB Model [GET]

    URL
    /document/fab/{id}
    

    PARAMETERS
    id: document's NEDi model id or document's sarahDocumentId id from SARAH
    
+ Response 200 (application/json)

        {
            "id": 1,
            "sarahDocumentId": "EC-1234",
            "type": "EC",
            "openDate": 01-01-2014,
            "closedDate": 02-05-2014
            "title": "The change to the widget",
            "comments": "This is a comment on a EC",
            "components": [{ 
                "id": 1,
                "tracer": "12345abcdef",
                "masterId": 1,
                "itemNumber": "SVG1235"
            }, { 
                "id": 2,
                "tracer": "6789zxyv",
                "masterId": 1,
                "itemNumber": "SVG1236"
            }, { 
                "id": 3,
                "tracer": "5555asdf",
                "masterId": 1,
                "itemNumber": "SEMU987"
            }],
             "masters": [{
                    "id": 2,
                    "itemNumber": "1234ITEM",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678"
                }, {
                    "id": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123",
            }],
            "attributes": { 
                "orderNumber":  "1001A",
                "orderType":  "classified"
                "orderStatus":  "I",
                "dueDate":  02-10-2015,
                "itemNumber":  "100A",
                "tracer":  "1001A1002B2LLG" - Unique identifier for an item. It consists of drawing number, serial number, lot number, side and size."
                "drawingNumber":  "1001",
                "asbuiltNumber":  "A1"
                "serialNumber":  "002",
                "lotNumber":  "B2",
                "side":  "L",
                "itemSize":  "LG",
                "itemClass":  "B",
                "description":  "Liner that attaches to the glove."
                "isDCN":  True,
                "dateComplete":  5-10-2015,
                "quantityOrdered":  2,
                "title":  "Line for glove assembly"
                "contractNumber":  "MD100EVA12"
                "estimateBeginDate":  01-01-2015,
                "estimateEndDate":  06-10-2015,
                "area":  "Latex",
                "drawingRevision":  "REV B", 
                "authority":  "Station",
                "laborLabelNumber":  "SGT",
                "materialLabelNumber":  "LTX",
                "releaseAuthority":  "MIB",
                "FABtype":  "Critical",
                "FABrevision":  "REV A",
                "totalAttachment":  14,
                "unitCost":  10,000,
                "totalCost":  20,000,
                "originalDueDate":  01-01-2015,
                "originalStartDate":  02-10-2015,
                "originalEndDate":  06-15-2015,
                "hasRedline":  True,
                "actualDrawingRevision":  "REV B",
                "actualFABRevision":  "REV A",
                "actualQuantityBuilt":  "CC",
                "stockUnitMeasure":  "inches",
                "status":  "pending",
                "hasDCN":  True,
                "type":   "EC",
                "revision":   "REV B",  
                "procedure":   [{
                    "organizationCode": "UTAS",
                    "operationSequence":   11,
                    "requiresInspection":   True,
                    "standardTextNumber":   12,
                    "lineNumber":  4,
                    "operationText": "Tighten all screws until unit is flush with mount.",
                    "components":   [{},{}, ... ],
                    "hardwareCode":   "F",
                    "component":   "Glove",
                    "componentQuantityPer": 2,
                    "componentQuantityRequired": 4,
                    "componentUnitOfMeasure": "inches",
                    "alternateMaster":   "glove"
                }]
            }
        }
        
### FAB Collection [/document/fabs(?since)]

+ Parameters
    + since: 01/01/2014 (optional, date) - Only return records that have been updated since the parameter.'
    
#### Get FAB Collection [GET]

    URL
    /document/fabs
    
    QUERY STRING OPTIONS
    since:  Only return records that have been updated since the parameter
    
+ Response 200 (application/json)

        [{
            "id": 1,
            "sarahDocumentId": "EC-1234",
            "type": "EC",
            "openDate": 01-01-2104,
            "title": "The change to the widget",
            "comments": "This is a comment on a EC",
            "components": [{ 
                "id": 1,
                "tracer": "12345abcdef",
                "masterId": 1,
                "itemNumber": "SVG1235"
            }, { 
                "id": 2,
                "tracer": "6789zxyv",
                "masterId": 1,
                "itemNumber": "SVG1236"
            }, { 
                "id": 3,
                "tracer": "5555asdf",
                "masterId": 1,
                "itemNumber": "SEMU987"
            }],
            "masters": [{
                    "id": 2,
                    "itemNumber": "1234ITEM",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678"
                }, {
                    "id": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123"
            }],
            "attributes": { 
                "orderNumber":  "1001A",
                "orderType":  "classified"
                "orderStatus":  "I",
                "dueDate":  02-10-2015,
                "itemNumber":  "100A",
                "tracer":  "1001A1002B2LLG",
                "drawingNumber":  "1001",
                "asbuiltNumber":  "A1"
                "serialNumber":  "002",
                "lotNumber":  "B2",
                "side":  "L",
                "itemSize":  "LG",
                "itemClass":  "B",
                "description":  "Liner that attaches to the glove."
                "isDCN":  True,
                "dateComplete":  5-10-2015,
                "quantityOrdered":  2,
                "title":  "Line for glove assembly"
                "contractNumber":  "MD100EVA12"
                "estimateBeginDate":  01-01-2015,
                "estimateEndDate":  06-10-2015,
                "area":  "Latex",
                "drawingRevision":  "REV B", 
                "authority":  "Station",
                "laborLabelNumber":  "SGT",
                "materialLabelNumber":  "LTX",
                "releaseAuthority":  "MIB",
                "FABtype":  "Critical",
                "FABrevision":  "REV A",
                "totalAttachment":  14,
                "unitCost":  10,000,
                "totalCost":  20,000,
                "originalDueDate":  01-01-2015,
                "originalStartDate":  02-10-2015,
                "originalEndDate":  06-15-2015,
                "hasRedline":  True,
                "actualDrawingRevision":  "REV B",
                "actualFABRevision":  "REV A",
                "actualQuantityBuilt":  "CC",
                "stockUnitMeasure":  "inches",
                "status":  "pending",
                "hasDCN":  True,
                "type":   "EC",
                "revision":   "REV B",  
                "procedure":   [
                    "organizationCode": "UTAS",
                    "operationSequence":   11,
                    "requiresInspection":   True,
                    "standardTextNumber":   12,
                    "lineNumber":  4,
                    "operationText": "Tighten all screws until unit is flush with mount.",
                    "components":   [{},{}, ... ],
                    "hardwareCode":   "F",
                    "component":   "Glove",
                    "componentQuantityPer": 2,
                    "componentQuantityRequired": 4,
                    "componentUnitOfMeasure": "inches",
                    "alternateMaster":   "glove"
                ]
            }
        },
        {
            "id": 2,
            "sarahDocumentId": "EC-4567",
            "type": "EC",
            "openDate": 01-01-2104,
            "title": "The change to the widget",
            "comments": "This is a comment on another EC",
            "components": [{ 
                "id": 1,
                "tracer": "12345abcdef",
                "masterId": 1,
                "itemNumber": "SVG1235"
            }, { 
                "id": 2,
                "tracer": "6789zxyv",
                "masterId": 1,
                "itemNumber": "SVG1236"
            }, { 
                "id": 3,
                "tracer": "5555asdf",
                "masterId": 1,
                "itemNumber": "SEMU987"
            }],
            "masters": [{
                    "id": 2,
                    "itemNumber": "1234ITEM",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678"
                }, {
                    "id": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123"
            }],
            "attributes": { 
                "orderNumber":  "1002B",
                "orderType":  "classified"
                "orderStatus":  "I",
                "dueDate":  02-10-2015,
                "itemNumber":  "100B",
                "tracer":  "1001B2002B2LLG",
                "drawingNumber":  "1001",
                "asbuiltNumber":  "B2"
                "serialNumber":  "002",
                "lotNumber":  "B2",
                "side":  "L",
                "itemSize":  "LG",
                "itemClass":  "B",
                "description":  "Liner that attaches to the glove."
                "isDCN":  True,
                "dateComplete":  5-10-2015,
                "quantityOrdered":  2,
                "title":  "Line for glove assembly"
                "contractNumber":  "MD100EVA12"
                "estimateBeginDate":  01-01-2015,
                "estimateEndDate":  06-10-2015,
                "area":  "Latex",
                "drawingRevision":  "REV B", 
                "authority":  "Station",
                "laborLabelNumber":  "SGT",
                "materialLabelNumber":  "LTX",
                "releaseAuthority":  "MIB",
                "FABtype":  "Critical",
                "FABrevision":  "REV A",
                "totalAttachment":  14,
                "unitCost":  10,000,
                "totalCost":  20,000,
                "originalDueDate":  01-01-2015,
                "originalStartDate":  02-10-2015,
                "originalEndDate":  06-15-2015,
                "hasRedline":  True,
                "actualDrawingRevision":  "REV B",
                "actualFABRevision":  "REV A",
                "actualQuantityBuilt":  "CC",
                "stockUnitMeasure":  "inches",
                "status":  "pending",
                "hasDCN":  True,
                "type":   "EC",
                "revision":   "REV B",  
                "procedure":   [
                    "organizationCode": "UTAS",
                    "operationSequence":   11,
                    "requiresInspection":   True,
                    "standardTextNumber":   12,
                    "lineNumber":  4,
                    "operationText": "Tighten all screws until unit is flush with mount.",
                    "components":   [{},{}, ... ],
                    "hardwareCode":   "F",
                    "component":   "Glove",
                    "componentQuantityPer": 2,
                    "componentQuantityRequired": 4,
                    "componentUnitOfMeasure": "inches",
                    "alternateMaster":   "glove"
                ]
            }
        }]
        
### YTN Model [/document/ytn/{id}]

A "YTN" document type has the following attributes:

+ **id** - *number* - The ESOC model id. **(primary key, unique)**
+ **sarahDocumentId** - *string* - The SARAH document id. **(primary key SARAH, unique)**
+ **type** - *string* - The document's type.
+ **openDate** - *date* - The date the document was opened.
+ **closeDate** - *date* - The date the document was closed.
+ **title** - *string* - The document title.
+ **comments** - *string* - All comments added to the document.
+ **components** - *array[objects]* - The applicable components of the document.
+ **masters** - *array[objects]* - The applicable masters of the document.
+ **audit** - *object* - The Audit model for the YTN
+ **attributes** - *object* - The documents attributes (specific to it's type).
    + **lineItems** - *array[objects]* - The YTN line items.
        + **component** -  *object* - The component the YTN is written against.
        + **tps** - *object* - The associated TPS written for the YTN line item.
            > [*see TPS model*](http://docs.emuapi.apiary.io/#reference/documents/TPS-model)
        + **initiator** - *string* - The initiator of the item
        + **audit** - *object* - The Audit model for the YTN line item
    
+ Parameters
    + id: 1 (required, number) - ID of the desired YTN
    
#### Get YTN Model [GET]

    URL
    /document/ytn/{id}
    

    PARAMETERS
    id: document's NEDi model id or document's sarahDocumentId id from SARAH

+ Response 200 (application/json)

        {
            "id": 1,
            "sarahDocumentId": "EC-1234",
            "type": "EC",
            "openDate": 01-01-2104,
            "title": "The change to the widget",
            "comments": "This is a comment on a EC",
            "components": [{ 
                "id": 1,
                "tracer": "12345abcdef",
                "masterId": 1,
                "itemNumber": "SVG1235"
            }, { 
                "id": 2,
                "tracer": "6789zxyv",
                "masterId": 1,
                "itemNumber": "SVG1236"
            }, { 
                "id": 3,
                "tracer": "5555asdf",
                "masterId": 1,
                "itemNumber": "SEMU987"
            }],
            "masters": [{
                    "id": 2,
                    "itemNumber": "1234ITEM",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678"
                }, {
                    "id": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123"
            }],
            "attributes": { 
                "lineItems": [
                    "component": { },
                    "tps": { 
                        "id": 2004,
                        "sarahDocumentId": "A100B200",
                        "type": "FAB",
                        "opentDate": 04-02-2015,
                        "closeDate": 06-1-2015,
                        "title": "Helmet visor",
                        "comments": "There is peeling on the gold coating"
                    },
                    "initiator": "CJESTES",
                    "audit": { }
                ]
            }
        }
        
### YTN Collection [/document/ytns(?since)]

+ Parameters
    + since: 01/01/2014 (optional, date) - Only return records that have been updated since the parameter.'
    
#### Get YTN Collection [GET]

    URL
    /document/ytns
    
    QUERY STRING OPTIONS
    since:  Only return records that have been updated since the parameter
    
+ Response 200 (application/json)

        [{
            "id": 1,
            "sarahDocumentId": "EC-1234",
            "type": "EC",
            "openDate": 01-01-2104,
            "title": "The change to the widget",
            "comments": "This is a comment on a EC",
            "components": [{ 
                "id": 1,
                "tracer": "12345abcdef",
                "masterId": 1,
                "itemNumber": "SVG1235"
            }, { 
                "id": 2,
                "tracer": "6789zxyv",
                "masterId": 1,
                "itemNumber": "SVG1236"
            }, { 
                "id": 3,
                "tracer": "5555asdf",
                "masterId": 1,
                "itemNumber": "SEMU987"
            }],
            "masters": [{
                    "id": 2,
                    "itemNumber": "1234ITEM",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678"
                }, {
                    "id": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123"
            }],
            "attributes": { 
                "lineItems": [
                    "component": { },
                    "tps": { 
                        "id": 2004,
                        "sarahDocumentId": "A100B200",
                        "type": "FAB",
                        "opentDate": 04-02-2015,
                        "closeDate": 06-1-2015,
                        "title": "Helmet visor",
                        "comments": "There is peeling on the gold coating"
                    },
                    "initiator": "CJESTES",
                    "audit": { }
                ]
            }
        },
        {
            "id": 2,
            "sarahDocumentId": "EC-4567",
            "type": "EC",
            "openDate": 01-01-2104,
            "title": "The change to the widget",
            "comments": "This is a comment on another EC",
            "components": [{ 
                "id": 1,
                "tracer": "12345abcdef",
                "masterId": 1,
                "itemNumber": "SVG1235"
            }, { 
                "id": 2,
                "tracer": "6789zxyv",
                "masterId": 1,
                "itemNumber": "SVG1236"
            }, { 
                "id": 3,
                "tracer": "5555asdf",
                "masterId": 1,
                "itemNumber": "SEMU987"
            }],
             "masters": [{
                    "id": 2,
                    "itemNumber": "1234ITEM",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678"
                }, {
                    "id": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123"
            }],
            "attributes": { 
                "lineItems": [
                    "component": { },
                    "tps": { 
                        "id": 2004,
                        "sarahDocumentId": "A100B200",
                        "type": "FAB",
                        "opentDate": 04-02-2015,
                        "closeDate": 06-1-2015,
                        "title": "Helmet visor",
                        "comments": "There is peeling on the gold coating"
                    },
                    "initiator": "CJESTES",
                    "audit": { }
                ]
            }
        }]
        
### OD Model [/document/od/{id}]

A "OD" document type has the following attributes:

+ **id** - *number* - The ESOC model id. **(primary key, unique)**
+ **sarahDocumentId** - *string* - The SARAH document id. **(primary key SARAH, unique)**
+ **type** - *string* - The document's type.
+ **openDate** - *date* - The date the document was opened.
+ **closeDate** - *date* - The date the document was closed.
+ **title** - *string* - The document title.
+ **comments** - *string* - All comments added to the document.
+ **components** - *array[objects]* - The applicable components of the document.
+ **masters** - *array[objects]* - The applicable masters of the document.
+ **audit** - *object* - The Audit model for the OD
+ **attributes** - *object* - The documents attributes (specific to it's type).
    + **qualityStamp** - *string* - TODO:  ADD DESCRIPTION
    + **lineItems** - *array[objects]* - The OD line items.    
        + **component** -  *object* - The component the OD line item is written against.
        + **audit** - *object* - The Audit model for the OD line item


+ Parameters
    + id: 1 (required, number) - ID of the desired OD
    
#### Get OD Model [GET]

    URL
    /document/od/{id}
    

    PARAMETERS
    id: document's NEDi model id or document's sarahDocumentId id from SARAH

+ Response 200 (application/json)

        {
            "id": 1,
            "sarahDocumentId": "OD-1234",
            "type": "OD",
            "openDate": 01-01-2014,
            "title": "The change to the widget",
            "comments": "This is a comment on a OD",
            "components": [{ 
                "id": 1,
                "tracer": "12345abcdef",
                "masterId": 1,
                "itemNumber": "SVG1235"
            }, { 
                "id": 2,
                "tracer": "6789zxyv",
                "masterId": 1,
                "itemNumber": "SVG1236"
            }, { 
                "id": 3,
                "tracer": "5555asdf",
                "masterId": 1,
                "itemNumber": "SEMU987"
            }],
            "masters": [{
                    "id": 2,
                    "itemNumber": "1234ITEM",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678"
                }, {
                    "id": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123"
            }],
            "attributes": { 
                "qualityStamp": "RFD",
                "lineItems": [
                    {
                        "component": {},
                        "audit": {}
                    },
                    {
                        "component": {},
                        "audit": {}
                    }
                ]
            }
        }
        
### OD Collection [/document/ods(?since)]

+ Parameters
    + since: 01/01/2014 (optional, date) - Only return records that have been updated since the parameter.'
    
#### Get OD Collection [GET]

    URL
    /document/ods
    
    QUERY STRING OPTIONS
    since:  Only return records that have been updated since the parameter
    
+ Response 200 (application/json)

        {
            "id": 1,
            "sarahDocumentId": "OD-1234",
            "type": "OD",
            "openDate": 01-01-2014,
            "title": "The change to the widget",
            "comments": "This is a comment on a OD",
            "components": [{ 
                "id": 1,
                "tracer": "12345abcdef",
                "masterId": 1,
                "itemNumber": "SVG1235"
            }, { 
                "id": 2,
                "tracer": "6789zxyv",
                "masterId": 1,
                "itemNumber": "SVG1236"
            }, { 
                "id": 3,
                "tracer": "5555asdf",
                "masterId": 1,
                "itemNumber": "SEMU987"
            }],
            "masters": [{
                    "id": 2,
                    "itemNumber": "1234ITEM",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678"
                }, {
                    "id": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123"
            }],
            "attributes": { 
                "qualityStamp": "RFD",
                "lineItems": [
                    {
                        "component": {},
                        "audit": {}
                    },
                    {
                        "component": {},
                        "audit": {}
                    }
                ]
            }
        },
        {
            "id": 2,
            "sarahDocumentId": "OD-4567",
            "type": "OD",
            "openDate": 01-01-2014,
            "title": "The change to the widget",
            "comments": "This is a comment on another OD",
            "components": [{ 
                "id": 1,
                "tracer": "12345abcdef",
                "masterId": 1,
                "itemNumber": "SVG1235"
            }, { 
                "id": 2,
                "tracer": "6789zxyv",
                "masterId": 1,
                "itemNumber": "SVG1236"
            }, { 
                "id": 3,
                "tracer": "5555asdf",
                "masterId": 1,
                "itemNumber": "SEMU987"
            }],
            "masters": [{
                    "id": 2,
                    "itemNumber": "1234ITEM",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678"
                }, {
                    "id": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123"
            }],
            "attributes": { 
                "qualityStamp": "RFD",
                "lineItems": [
                    {
                        "component": {},
                        "audit": {}
                    },
                    {
                        "component": {},
                        "audit": {}
                    }
                ]
            }
        }
        
### ODT Model [/document/odt/{id}]

A "ODT" document type has the following attributes:

+ **id** - *number* - The ESOC model id. **(primary key, unique)**
+ **sarahDocumentId** - *string* - The SARAH document id. **(primary key SARAH, unique)**
+ **type** - *string* - The document's type.
+ **openDate** - *date* - The date the document was opened.
+ **closeDate** - *date* - The date the document was closed.
+ **title** - *string* - The document title.
+ **comments** - *string* - All comments added to the document.
+ **components** - *array[objects]* - The applicable components of the document.
+ **masters** - *array[objects]* - The applicable masters of the document. (???)
+ **audit** - *object* - The Audit model for the ODT
+ **attributes** - *object* - The documents attributes (specific to it's type).
    + **initiator** - *string* - TODO:  The name of the person that initiated the overdue tag
    + **authorizingDocument** - *object* - The document model of the authorizing document that performed the maint. on the overdue component. (typically a TPS or DR but doesn’t have to be)
        > [*see general Document model*](http://docs.emuapi.apiary.io/#reference/documents/document-model)
    + **lineItems** - *array[objects]* - The ODT line items.    
        + **component** -  *object* - The component the ODT line item is written against.
        + **audit** - *object* - The Audit model for the ODT line item

    
    
+ Parameters
    + id: 1 (required, number) - ID of the desired ODT
    
#### Get ODT Model [GET]

    URL
    /document/odt/{id}
    

    PARAMETERS
    id: document's NEDi model id or document's sarahDocumentId id from SARAH

+ Response 200 (application/json)

        {
            "id": 1,
            "sarahDocumentId": "ODT-1234",
            "type": "ODT",
            "openDate": 01-01-2104,
            "title": "The change to the widget",
            "comments": "This is a comment on a ODT",
            "components": [{ 
                "id": 1,
                "tracer": "12345abcdef",
                "masterId": 1,
                "itemNumber": "SVG1235"
            }, { 
                "id": 2,
                "tracer": "6789zxyv",
                "masterId": 1,
                "itemNumber": "SVG1236"
            }, { 
                "id": 3,
                "tracer": "5555asdf",
                "masterId": 1,
                "itemNumber": "SEMU987"
            }],
            "masters": [{
                    "id": 2,
                    "itemNumber": "1234ITEM",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678"
                }, {
                    "id": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123"
            }],
            "attributes": { 
                "initiator": "RJGILL",
                "authorizingDocument": {
                    "id": 1,
                    "sarahDocumentId": "ODT-1234",
                    "type": "ODT",
                    "openDate": 01-01-2104,
                    "title": "The change to the widget",
                    "comments": "This is a comment on a ODT"
                },
                "lineItems": [
                    {
                        "component": {
                           "id": 1,
                            "tracer": "12345abcdef",
                            "masterId": 1,
                            "itemNumber": "SVG1235",
                            "description": "EMU GLOVE",
                            "drawingNumber": "1234Draw",
                            "serialNumber": "3001",
                            "lotNumber": null,
                            "side": "right",
                            "itemSize": "YG"
                        },
                        "audit": {
                            "id": 1,
                            "itemNumber": 1,
                            "createdBy": "CJESTES",
                            "createdDate": 01-01-2015,
                            "closedDate": 01-30-2015,
                            "closedBy": "MFIELDEN",
                            "lastUpdatedBy": "MFIELDEN",
                            "lastUpdatedDate": 01-30-2015
                        }
                    },
                    {
                        {
                        "component": {
                           "id": 2,
                            "tracer": "21445abcdef",
                            "masterId": 2,
                            "itemNumber": "SVG3235",
                            "description": "EMU GLOVE",
                            "drawingNumber": "1444Draw",
                            "serialNumber": "3002",
                            "lotNumber": null,
                            "side": "left",
                            "itemSize": "YG"
                        },
                        "audit": {
                            "id": 2,
                            "itemNumber": 3,
                            "createdBy": "CJESTES",
                            "createdDate": 01-01-2015,
                            "closedDate": 01-30-2015,
                            "closedBy": "MFIELDEN",
                            "lastUpdatedBy": "MFIELDEN",
                            "lastUpdatedDate": 01-30-2015
                        }
                    }
                ]
                
            }
        }
        
### ODT Collection [/document/odts(?since)]

+ Parameters
    + since: 01/01/2014 (optional, date) - Only return records that have been updated since the parameter.'
    
#### Get ODT Collection [GET]

    URL
    /document/odts
    
    QUERY STRING OPTIONS
    since:  Only return records that have been updated since the parameter
    
+ Response 200 (application/json)

        [{
            "id": 1,
            "sarahDocumentId": "ODT-1234",
            "type": "ODT",
            "openDate": 01-01-2104,
            "title": "The change to the widget",
            "comments": "This is a comment on a ODT",
            "components": [{ 
                "id": 1,
                "tracer": "12345abcdef",
                "masterId": 1,
                "itemNumber": "SVG1235"
            }, { 
                "id": 2,
                "tracer": "6789zxyv",
                "masterId": 1,
                "itemNumber": "SVG1236"
            }, { 
                "id": 3,
                "tracer": "5555asdf",
                "masterId": 1,
                "itemNumber": "SEMU987"
            }],
            "masters": [{
                    "id": 2,
                    "itemNumber": "1234ITEM",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678"
                }, {
                    "id": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123"
            }],
            "attributes": { 
                "initiator": "RJGILL",
                "authorizingDocument": {
                    "id": 1,
                    "sarahDocumentId": "ODT-1234",
                    "type": "ODT",
                    "openDate": 01-01-2104,
                    "title": "The change to the widget",
                    "comments": "This is a comment on a ODT"
                },
                "lineItems": [
                    {
                        "component": {
                           "id": 1,
                            "tracer": "12345abcdef",
                            "masterId": 1,
                            "itemNumber": "SVG1235",
                            "description": "EMU GLOVE",
                            "drawingNumber": "1234Draw",
                            "serialNumber": "3001",
                            "lotNumber": null,
                            "side": "right",
                            "itemSize": "YG"
                        },
                        "audit": {
                            "id": 1,
                            "itemNumber": 1,
                            "createdBy": "CJESTES",
                            "createdDate": 01-01-2015,
                            "closedDate": 01-30-2015,
                            "closedBy": "MFIELDEN",
                            "lastUpdatedBy": "MFIELDEN",
                            "lastUpdatedDate": 01-30-2015
                        }
                    },
                    {
                        {
                        "component": {
                           "id": 2,
                            "tracer": "21445abcdef",
                            "masterId": 2,
                            "itemNumber": "SVG3235",
                            "description": "EMU GLOVE",
                            "drawingNumber": "1444Draw",
                            "serialNumber": "3002",
                            "lotNumber": null,
                            "side": "left",
                            "itemSize": "YG"
                        },
                        "audit": {
                            "id": 2,
                            "itemNumber": 3,
                            "createdBy": "CJESTES",
                            "createdDate": 01-01-2015,
                            "closedDate": 01-30-2015,
                            "closedBy": "MFIELDEN",
                            "lastUpdatedBy": "MFIELDEN",
                            "lastUpdatedDate": 01-30-2015
                        }
                    }
                ]
                
            }
        },
        {
            "id": 2,
            "sarahDocumentId": "ODT-4567",
            "type": "ODT",
            "openDate": 01-01-2104,
            "title": "The change to the widget",
            "comments": "This is a comment on another ODT",
            "components": [{ 
                "id": 1,
                "tracer": "12345abcdef",
                "masterId": 1,
                "itemNumber": "SVG1235"
            }, { 
                "id": 2,
                "tracer": "6789zxyv",
                "masterId": 1,
                "itemNumber": "SVG1236"
            }, { 
                "id": 3,
                "tracer": "5555asdf",
                "masterId": 1,
                "itemNumber": "SEMU987"
            }],
            "masters": [{
                    "id": 2,
                    "itemNumber": "1234ITEM",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678"
                }, {
                    "id": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123"
            }],
            "attributes": { 
                "initiator": "RJGILL",
                "authorizingDocument": {
                    "id": 1,
                    "sarahDocumentId": "ODT-1234",
                    "type": "ODT",
                    "openDate": 01-01-2104,
                    "title": "The change to the widget",
                    "comments": "This is a comment on a ODT"
                },
                "lineItems": [
                    {
                        "component": {
                           "id": 1,
                            "tracer": "12345abcdef",
                            "masterId": 1,
                            "itemNumber": "SVG1235",
                            "description": "EMU GLOVE",
                            "drawingNumber": "1234Draw",
                            "serialNumber": "3001",
                            "lotNumber": null,
                            "side": "right",
                            "itemSize": "YG"
                        },
                        "audit": {
                            "id": 1,
                            "itemNumber": 1,
                            "createdBy": "CJESTES",
                            "createdDate": 01-01-2015,
                            "closedDate": 01-30-2015,
                            "closedBy": "MFIELDEN",
                            "lastUpdatedBy": "MFIELDEN",
                            "lastUpdatedDate": 01-30-2015
                        }
                    },
                    {
                        {
                        "component": {
                           "id": 2,
                            "tracer": "21445abcdef",
                            "masterId": 2,
                            "itemNumber": "SVG3235",
                            "description": "EMU GLOVE",
                            "drawingNumber": "1444Draw",
                            "serialNumber": "3002",
                            "lotNumber": null,
                            "side": "left",
                            "itemSize": "YG"
                        },
                        "audit": {
                            "id": 2,
                            "itemNumber": 3,
                            "createdBy": "CJESTES",
                            "createdDate": 01-01-2015,
                            "closedDate": 01-30-2015,
                            "closedBy": "MFIELDEN",
                            "lastUpdatedBy": "MFIELDEN",
                            "lastUpdatedDate": 01-30-2015
                        }
                    }
                ]
                
            }
        }]
        
### WAIVER Model [/document/waiver/{id}]

A "WAIVER" document type has the following attributes:

+ **id** - *number* - The ESOC model id. **(primary key, unique)**
+ **sarahDocumentId** - *string* - The SARAH document id. **(primary key SARAH, unique)**
+ **type** - *string* - The document's type.
+ **openDate** - *date* - The date the document was opened.
+ **closeDate** - *date* - The date the document was closed.
+ **title** - *string* - The document title.
+ **comments** - *string* - All comments added to the document. 
+ **components** - *array[objects]* - The applicable components of the document.
+ **attributes** - *object* - The documents attributes (specific to it's type).
    + **status** - *string* - The status of the waiver
    + **effectiveFlightNumber** - *string* - Flight numbers or planned usage that the waiver is in effect for.
    + **crNumber** - *string* -  Change request number that authorized the waiver
    + **lineItems** - *array[objects]* - The Waiver's line items. 
        + **component** -  *object* - The component the Waiver line item is written against.
        + **estimatedCloseDate** - *date* - The projected/estimated close date for the Waiver line item.
        + **actualCloseDate** - *date* - The actual close date for the Waiver line item.
        + **audit** - *object* - The Audit model for the Waiver.
    
    
+ Parametersl
    + id: 1 (required, number) - ID of the desired WAIVER
    
#### Get WAIVER Model [GET]

    URL
    /document/waiver/{id}
    

    PARAMETERS
    id: document's NEDi model id or document's sarahDocumentId id from SARAH
    
+ Response 200 (application/json)

        {
            "id": 1,
            "sarahDocumentId": "WAIVER-1234",
            "type": "WAIVER",
            "openDate": 01-01-2014,
            "closeDate": 02-01-2015,
            "title": "EMU Waiver for CR 1234",
            "comments": "This is a comment on a WAIVER.  More comments are also included.",
            "components": [{ 
                "id": 1,
                "tracer": "12345abcdef",
                "masterId": 1,
                "itemNumber": "SVG1235"
            }, { 
                "id": 2,
                "tracer": "6789zxyv",
                "masterId": 1,
                "itemNumber": "SVG1236"
            }, { 
                "id": 3,
                "tracer": "5555asdf",
                "masterId": 1,
                "itemNumber": "SEMU987"
            }],
            "masters": [{
                    "id": 2,
                    "itemNumber": "1234ITEM",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678"
                }, {
                    "id": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123"
            }],,
            "attributes": { 
                "status": "Open",
                "effectiveFlightNumber": "",
                "crNumber": "",
                "lineItems": [{
                    "id": 1,
                    "tracer": "12345abcdef",
                    "masterId": 1,
                    "itemNumber": "SVG1235"
                
                }, {
                    "id": 2,
                    "tracer": "6789zxyv",
                    "masterId": 1,
                    "itemNumber": "SVG1235"
                }, {
                    "id": 3,
                    "tracer": "5555asdf",
                    "masterId": 1,
                    "itemNumber": "SEMU9876"
                
                }],
                "estimatedCloseDate": 01-01-2015,
                "actualCloseDate": 01-01-2015,
                "audit": {
                    
                }
            }
        }
        
### WAIVER Collection [/document/waivers(?since)]

+ Parameters
    + since: 01/01/2014 (optional, date) - Only return records that have been updated since the parameter.'
    
#### Get WAIVER Collection [GET]

    URL
    /document/waivers
    
    QUERY STRING OPTIONS
    since:  Only return records that have been updated since the parameter
    
+ Response 200 (application/json)

        [{
            "id": 1,
            "sarahDocumentId": "WAIVER-1234",
            "type": "WAIVER",
            "openDate": 01-01-2104,
            "title": "The change to the widget",
            "comments": "This is a comment on a WAIVER",
            "components": [{ 
                "id": 1,
                "tracer": "12345abcdef",
                "masterId": 1,
                "itemNumber": "SVG1235"
            }, { 
                "id": 2,
                "tracer": "6789zxyv",
                "masterId": 1,
                "itemNumber": "SVG1236"
            }, { 
                "id": 3,
                "tracer": "5555asdf",
                "masterId": 1,
                "itemNumber": "SEMU987"
            }],
            "masters": [{
                    "id": 2,
                    "itemNumber": "1234ITEM",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678"
                }, {
                    "id": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123"
            }],
            "attributes": { 
                "status": "Open",
                "effectiveFlightNumber": "",
                "crNumber": "",
                "lineItems": [{
                    "id": 1,
                    "tracer": "12345abcdef",
                    "masterId": 1,
                    "itemNumber": "SVG1235"
                
                }, {
                    "id": 2,
                    "tracer": "6789zxyv",
                    "masterId": 1,
                    "itemNumber": "SVG1235"
                }, {
                    "id": 3,
                    "tracer": "5555asdf",
                    "masterId": 1,
                    "itemNumber": "SEMU9876"
                
                }],
                "estimatedCloseDate": 01-01-2015,
                "actualCloseDate": 01-01-2015,
                "audit": {
                    
                }
            }
        },
        {
            "id": 2,
            "sarahDocumentId": "WAIVER-4567",
            "type": "WAIVER",
            "openDate": 01-01-2104,
            "title": "The change to the widget",
            "comments": "This is a comment on another WAIVER",
            "components": [{ 
                "id": 1,
                "tracer": "12345abcdef",
                "masterId": 1,
                "itemNumber": "SVG1235"
            }, { 
                "id": 2,
                "tracer": "6789zxyv",
                "masterId": 1,
                "itemNumber": "SVG1236"
            }, { 
                "id": 3,
                "tracer": "5555asdf",
                "masterId": 1,
                "itemNumber": "SEMU987"
            }],
            "masters": [{
                    "id": 2,
                    "itemNumber": "1234ITEM",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678"
                }, {
                    "id": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123"
            }],
            "attributes": { 
                "status": "Open",
                "effectiveFlightNumber": "",
                "crNumber": "",
                "lineItems": [{
                    "id": 4,
                    "tracer": "12345abcdef",
                    "masterId": 1,
                    "itemNumber": "SVG1235"
                
                }, {
                    "id": 5,
                    "tracer": "6789zxyv",
                    "masterId": 1,
                    "itemNumber": "SVG1235"
                }, {
                    "id": 6,
                    "tracer": "5555asdf",
                    "masterId": 1,
                    "itemNumber": "SEMU9876"
                
                }],
                "estimatedCloseDate": 01-01-2015,
                "actualCloseDate": 01-01-2015,
                "audit": {
                    
                }
            }
        }]
        
### ADCN Model [/document/adcn/{id}]

A "ADCN" document type has the following attributes:

+ **id** - *number* - The ESOC model id. **(primary key, unique)**
+ **sarahDocumentId** - *string* - The SARAH document id. **(primary key SARAH, unique)**
+ **type** - *string* - The document's type.
+ **openDate** - *date* - The date the document was opened.
+ **closeDate** - *date* - The date the document was closed.
+ **title** - *string* - The document title.
+ **comments** - *string* - All comments added to the document.
+ **components** - *array[objects]* - The applicable components of the document.
+ **masters** - *array[objects]* - The applicable masters of the document.
+ **attributes** - *object* - The documents attributes (specific to it's type).
    + **isCadDrawing** - *bool* - Indicates if the drawing is available on the FCE/EVA Engineering Support CAD System.
    + **engineer** - *string* - The name of the engineer responsible for the equipment group.
    + **releaseDate** - *date* - The date that the drawing entered was released.
    + **revisionLetter** - *string* - The revision of the document or drawing.
    + **fileName** - *string* - The name of the file.
    + **directoryName** - *string* - The name of the directory
    + **fileCopyDate** - *date* - The date that the drawing was placed on file
    + **engineeringReleaseId** - *string* - A id for the engineering release completion record **(unique id)**
    + **equipmentGroup** - *string* - equipment groupings are used for standard routing determinations for approval processing.
    
+ Parameters
    + id: 1 (required, number) - ID of the desired WAIVER
    
#### Get ADCN Model [GET]

    URL
    /document/adcn/{id}
    

    PARAMETERS
    id: document's NEDi model id or document's sarahDocumentId id from SARAH
    
+ Response 200 (application/json)

        {
            "id": 1,
            "sarahDocumentId": "ADCN-1234",
            "type": "ADCN",
            "openDate": 01-01-2015,
            "title": "Advanced notice of a change to the widget",
            "comments": "This is a comment on a ADCN",
            "components": [{ 
                "id": 1,
                "tracer": "12345abcdef",
                "masterId": 1,
                "itemNumber": "SVG1235"
            }, { 
                "id": 2,
                "tracer": "6789zxyv",
                "masterId": 1,
                "itemNumber": "SVG1236"
            }, { 
                "id": 3,
                "tracer": "5555asdf",
                "masterId": 1,
                "itemNumber": "SEMU987"
            }],
            "masters": [{
                    "id": 2,
                    "itemNumber": "1234ITEM",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678"
                }, {
                    "id": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123",
            }],
            "attributes": { 
                "isCadDrawing": true,
                "engineer": "John Doe",
                "releaseDate": 01-15-2015,
                "revisionLetter": "A",
                "fileName": "CADDrawingName123",
                "directoryName": "ADCNFolderName",
                "fileCopyDate": 01-12-2015,
                "engineeringReleaseId": "Abc123",
                "equipmentGroup": "C"
            }
        }
        
### ADCN Collection [/document/adcn(?since)]

+ Parameters
    + since: 01/01/2014 (optional, date) - Only return records that have been updated since the parameter.'
    
#### Get ADCN Collection [GET]

    URL
    /document/adcn
    
    QUERY STRING OPTIONS
    since:  Only return records that have been updated since the parameter
    
+ Response 200 (application/json)

        [
            {
            "id": 1,
            "sarahDocumentId": "ADCN-1234",
            "type": "ADCN",
            "openDate": 01-01-2015,
            "title": "Advanced notice of a change to the widget",
            "comments": "This is a comment on a ADCN",
            "components": [{ 
                "id": 1,
                "tracer": "12345abcdef",
                "masterId": 1,
                "itemNumber": "SVG1235"
            }, { 
                "id": 2,
                "tracer": "6789zxyv",
                "masterId": 1,
                "itemNumber": "SVG1236"
            }, { 
                "id": 3,
                "tracer": "5555asdf",
                "masterId": 1,
                "itemNumber": "SEMU987"
            }],
            "masters": [{
                    "id": 2,
                    "itemNumber": "1234ITEM",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678"
                }, {
                    "id": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123"
            }],
            "attributes": { 
                "isCadDrawing": true,
                "engineer": "John Doe",
                "releaseDate": 01-15-2015,
                "revisionLetter": "A",
                "fileName": "CADDrawingName123",
                "directoryName": "ADCNFolderName",
                "fileCopyDate": 01-12-2015,
                "engineeringReleaseId": "Abc123",
                "equipmentGroup": "C"
            }
        },
        {
            "id": 2,
            "sarahDocumentId": "ADCN-9876",
            "type": "ADCN",
            "openDate": 01-01-2014,
            "title": "Advanced notice of a change to the widget",
            "comments": "This is a comment on a ADCN",
            "components": [{ 
                "id": 1,
                "tracer": "12345abcdef",
                "masterId": 1,
                "itemNumber": "SVG1235"
            }, { 
                "id": 2,
                "tracer": "6789zxyv",
                "masterId": 1,
                "itemNumber": "SVG1236"
            }, { 
                "id": 3,
                "tracer": "5555asdf",
                "masterId": 1,
                "itemNumber": "SEMU987"
            }],
            "masters": [{
                    "id": 2,
                    "itemNumber": "1234ITEM",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678"
                }, {
                    "id": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123"
            }],
            "attributes": { 
                "isCadDrawing": true,
                "engineer": "John Doe",
                "releaseDate": 01-15-2014,
                "revisionLetter": "A",
                "fileName": "CADDrawingName987",
                "directoryName": "ADCNFolderName",
                "fileCopyDate": 01-12-2015,
                "engineeringReleaseId": "Abc123",
                "equipmentGroup": "C"
            }
        }
        ]
        
### DCN Model [/document/dcn/{id}]

A "DCN" document type has the following attributes:

+ **id** - *number* - The ESOC model id. **(primary key, unique)**
+ **sarahDocumentId** - *string* - The SARAH document id. **(primary key SARAH, unique)**
+ **type** - *string* - The document's type.
+ **openDate** - *date* - The date the document was opened.
+ **closeDate** - *date* - The date the document was closed.
+ **title** - *string* - The document title.
+ **comments** - *string* - All comments added to the document.
+ **components** - *array[objects]* - The applicable components of the document.
+ **masters** - *array[objects]* - The applicable masters of the document.
+ **attributes** - *object* - The documents attributes (specific to it's type).
    + **isCadDrawing** - *bool* - Indicates if the drawing is available on the FCE/EVA Engineering Support CAD System.
    + **engineer** - *string* - The name of the engineer responsible for the equipment group.
    + **releaseDate** - *date* - The date that the drawing entered was released.
    + **revisionLetter** - *string* - The revision of the document or drawing.
    + **fileName** - *string* - The name of the file.
    + **directoryName** - *string* - The name of the directory
    + **fileCopyDate** - *date* - The date that the drawing was placed on file
    + **engineeringReleaseId** - *string* - A id for the engineering release completion record **(unique id)**
    + **equipmentGroup** - *string* - equipment groupings are used for standard routing determinations for approval processing.
    
+ Parameters
    + id: 1 (required, number) - ID of the desired WAIVER
    
#### Get DCN Model [GET]

    URL
    /document/dcn/{id}
    

    PARAMETERS
    id: document's NEDi model id or document's sarahDocumentId id from SARAH

+ Response 200 (application/json)

        {
            "id": 1,
            "sarahDocumDCNentId": "DCN-1234",
            "type": "DCN",
            "openDate": 01-01-2015,
            "title": "Advanced notice of a change to the widget",
            "comments": "This is a comment on a DCN",
            "components": [{ 
                "id": 1,
                "tracer": "12345abcdef",
                "masterId": 1,
                "itemNumber": "SVG1235"
            }, { 
                "id": 2,
                "tracer": "6789zxyv",
                "masterId": 1,
                "itemNumber": "SVG1236"
            }, { 
                "id": 3,
                "tracer": "5555asdf",
                "masterId": 1,
                "itemNumber": "SEMU987"
            }],
            "masters": [{
                "id": 2,
                "itemNumber": "1234ITEM",
                "description": "EMU GLOVE",
                "drawingNumber": "ABC678"
             }, {
                "id": 3,
                "itemNumber": "ThirdItem1234",
                "description": "EMU GLOVE",
                "drawingNumber": "Draw123",
            }],
            "attributes": { 
                "isCadDrawing": true,
                "engineer": "John Doe",
                "releaseDate": 01-15-2015,
                "revisionLetter": "A",
                "fileName": "CADDrawingName123",
                "directoryName": "DCNFolderName",
                "fileCopyDate": 01-12-2015,
                "engineeringReleaseId": "Abc123",
                "equipmentGroup": "C"
            }
        }
        
### DCN Collection [/document/dcn(?since)]

+ Parameters
    + since: 01/01/2014 (optional, date) - Only return records that have been updated since the parameter.'
    
#### Get DCN Collection [GET]

    URL
    /document/dcn
    
    QUERY STRING OPTIONS
    since:  Only return records that have been updated since the parameter
    
+ Response 200 (application/json)

        [
            {
            "id": 1,
            "sarahDocumentId": "DCN-1234",
            "type": "DCN",
            "openDate": 01-01-2015,
            "title": "Advanced notice of a change to the widget",
            "comments": "This is a comment on a DCN",
            "components": [{ 
                "id": 1,
                "tracer": "12345abcdef",
                "masterId": 1,
                "itemNumber": "SVG1235"
            }, { 
                "id": 2,
                "tracer": "6789zxyv",
                "masterId": 1,
                "itemNumber": "SVG1236"
            }, { 
                "id": 3,
                "tracer": "5555asdf",
                "masterId": 1,
                "itemNumber": "SEMU987"
            }],
            "masters": [{
                    "id": 2,
                    "itemNumber": "1234ITEM",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678"
                }, {
                    "id": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123",
            }],
            "attributes": { 
                "isCadDrawing": true,
                "engineer": "John Doe",
                "releaseDate": 01-15-2015,
                "revisionLetter": "A",
                "fileName": "CADDrawingName123",
                "directoryName": "DCNFolderName",
                "fileCopyDate": 01-12-2015,
                "engineeringReleaseId": "Abc123",
                "equipmentGroup": "C"
            }
        },
        {
            "id": 1,
            "sarahDocumentId": "DCN-9876",
            "type": "DCN",
            "openDate": 01-01-2014,
            "title": "Advanced notice of a change to the widget",
            "comments": "This is a comment on a DCN",
            "components": [{ 
                "id": 1,
                "tracer": "12345abcdef",
                "masterId": 1,
                "itemNumber": "SVG1235"
            }, { 
                "id": 2,
                "tracer": "6789zxyv",
                "masterId": 1,
                "itemNumber": "SVG1236"
            }, { 
                "id": 3,
                "tracer": "5555asdf",
                "masterId": 1,
                "itemNumber": "SEMU987"
            }],
            "masters": [{
                    "id": 2,
                    "itemNumber": "1234ITEM",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678"
                }, {
                    "id": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123",
            }],
            "attributes": { 
                "isCadDrawing": true,
                "engineer": "John Doe",
                "releaseDate": 01-15-2014,
                "revisionLetter": "A",
                "fileName": "CADDrawingName987",
                "directoryName": "DCNFolderName",
                "fileCopyDate": 01-12-2015,
                "engineeringReleaseId": "Abc123",
                "equipmentGroup": "C"
            }
        }]
        
### ECM Model [/document/ecm/{id}]

A "ECM" document type has the following attributes:

+ **id** - *number* - The ESOC model id. **(primary key, unique)**
+ **sarahDocumentId** - *string* - The SARAH document id. **(primary key SARAH, unique)**
+ **type** - *string* - The document's type.
+ **openDate** - *date* - The date the document was opened.
+ **closeDate** - *date* - The date the document was closed.
+ **title** - *string* - The document title.
+ **comments** - *string* - All comments added to the document.
+ **components** - *array[objects]* - The applicable components of the document.
+ **masters** - *array[objects]* - The applicable masters of the document.
+ **attributes** - *object* - The documents attributes (specific to it's type).
    + **isCadDrawing** - *bool* - Indicates if the drawing is available on the FCE/EVA Engineering Support CAD System.
    + **engineer** - *string* - The name of the engineer responsible for the equipment group.
    + **releaseDate** - *date* - The date that the drawing entered was released.
    + **revisionLetter** - *string* - The revision of the document or drawing.
    + **fileName** - *string* - The name of the file.
    + **directoryName** - *string* - The name of the directory
    + **fileCopyDate** - *date* - The date that the drawing was placed on file
    + **engineeringReleaseId** - *string* - A id for the engineering release completion record **(unique id)**
    + **equipmentGroup** - *string* - equipment groupings are used for standard routing determinations for approval processing.
    
+ Parameters
    + id: 1 (required, number) - ID of the desired WAIVER
    
#### Get ECM Model [GET]

    URL
    /document/ecm/{id}
    

    PARAMETERS
    id: document's NEDi model id or document's sarahDocumentId id from SARAH
    
+ Response 200 (application/json)

        {
            "id": 1,
            "sarahDocumDCNentId": "ECM-1234",
            "type": "ECM",
            "openDate": 01-01-2015,
            "title": "Advanced notice of a change to the widget",
            "comments": "This is a comment on a ECM",
            "components": [{ 
                "id": 1,
                "tracer": "12345abcdef",
                "masterId": 1,
                "itemNumber": "SVG1235"
            }, { 
                "id": 2,
                "tracer": "6789zxyv",
                "masterId": 1,
                "itemNumber": "SVG1236"
            }, { 
                "id": 3,
                "tracer": "5555asdf",
                "masterId": 1,
                "itemNumber": "SEMU987"
            }],
            "masters": [{
                    "id": 2,
                    "itemNumber": "1234ITEM",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678"
                }, {
                    "id": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123",
            }],
            "attributes": { 
                "isCadDrawing": true,
                "engineer": "John Doe",
                "releaseDate": 01-15-2015,
                "revisionLetter": "A",
                "fileName": "CADDrawingName123",
                "directoryName": "ECMFolderName",
                "fileCopyDate": 01-12-2015,
                "engineeringReleaseId": "Abc123",
                "equipmentGroup": "C"
            }
        }
        
### ECM Collection [/document/ecms(?since)]

+ Parameters
    + since: 01/01/2014 (optional, date) - Only return records that have been updated since the parameter.'
    
#### Get ECM Collection [GET]

    URL
    /document/ecms
    
    QUERY STRING OPTIONS
    since:  Only return records that have been updated since the parameter
    
+ Response 200 (application/json)

        [
            {
            "id": 1,
            "sarahDocumentId": "ECM-1234",
            "type": "ECM",
            "openDate": 01-01-2015,
            "title": "Advanced notice of a change to the widget",
            "comments": "This is a comment on a ECM",
            "components": [{ 
                "id": 1,
                "tracer": "12345abcdef",
                "masterId": 1,
                "itemNumber": "SVG1235"
            }, { 
                "id": 2,
                "tracer": "6789zxyv",
                "masterId": 1,
                "itemNumber": "SVG1236"
            }, { 
                "id": 3,
                "tracer": "5555asdf",
                "masterId": 1,
                "itemNumber": "SEMU987"
            }],
            "masters": [{
                    "id": 2,
                    "itemNumber": "1234ITEM",
                    "description": "EMU GLOVE",
                    "drawingNumber": "ABC678"
                }, {
                    "id": 3,
                    "itemNumber": "ThirdItem1234",
                    "description": "EMU GLOVE",
                    "drawingNumber": "Draw123",
            }],
            "attributes": { 
                "isCadDrawing": true,
                "engineer": "John Doe",
                "releaseDate": 01-15-2015,
                "revisionLetter": "A",
                "fileName": "CADDrawingName123",
                "directoryName": "ECMFolderName",
                "fileCopyDate": 01-12-2015,
                "engineeringReleaseId": "Abc123",
                "equipmentGroup": "C"
            }
        },
        {
            "id": 2,
            "sarahDocumentId": "ECM-9876",
            "type": "ECM",
            "openDate": 01-01-2014,
            "title": "Advanced notice of a change to the widget",
            "comments": "This is a comment on a ECM",
            "components": [{ 
                "id": 1,
                "tracer": "12345abcdef",
                "masterId": 1,
                "itemNumber": "SVG1235"
            }, { 
                "id": 2,
                "tracer": "6789zxyv",
                "masterId": 1,
                "itemNumber": "SVG1236"
            }, { 
                "id": 3,
                "tracer": "5555asdf",
                "masterId": 1,
                "itemNumber": "SEMU987"
            }],
            "masters": [{
                "id": 2,
                "itemNumber": "1234ITEM",
                "description": "EMU GLOVE",
                "drawingNumber": "ABC678"
            }, {
                "id": 3,
                "itemNumber": "ThirdItem1234",
                "description": "EMU GLOVE",
                "drawingNumber": "Draw123",
            }],
            "attributes": { 
                "isCadDrawing": true,
                "engineer": "John Doe",
                "releaseDate": 01-15-2014,
                "revisionLetter": "A",
                "fileName": "CADDrawingName987",
                "directoryName": "ECMFolderName",
                "fileCopyDate": 01-12-2015,
                "engineeringReleaseId": "Abc123",
                "equipmentGroup": "C"
            }
        }
        ]
        




## Group Shippers
TODO:  ADD SUMMARY

### Shipper Model [/shipper/{id}]

A "Shipper" model has the following attributes:

+ id - number - The ESOC model id (primary key, unique)
+ ptsId - string - The PTS document id (primary key PTS, unique)
+ type - string - The shipper type.
+ attributes - object - The shipper's attributes.
    + date - date - The shippers date
    + TODO:  ADD MORE
+ components - array[object] - The collection of component models associated with the shipper
    
+ Parameters
    + id: 1 (required, number) - ID of the desired document
    
#### Get Shipper Model [GET]

+ Response 200 (application/json)

        {
            "id": 1,
            "ptsId": "1234ABC,
            "type": "DD1149",
            "attributes": { },
            "components": { }
        }
        
### Shipper Collection [/shippers(?since)]

+ Parameters
    + since: 01/01/2014 (optional, date) - Only return records that have been updated since the parameter.'
    
#### Get Shipper Collection [GET]

+ Response 200 (application/json)

        [{
            "id": 1,
            "ptsId": "1234ABC,
            "type": "DD1149",
            "attributes": { },
            "components": { }
        }, {
            "id": 2,
            "ptsId": "1234ABC,
            "type": "JSC250",
            "attributes": { },
            "components": { }
            }
        }]
        
        
        
        
        
        

## Group CrewMembers
TODO:  ADD SUMMARY

### CrewMember Model [/crewmember/{id}]

A "CrewMember" model has the following attributes:

+ **id** - *number* - The ESOC model id **(primary key, unique)**
+ **crewId** - *string* - The SARAH crew member id **(primary key SARAH, unique)**
+ **firstName** - *string* - The crew member's first name
+ **lastName** - *string* - The crew member's last name
+ **middleInitial** - *string* - The crew member's middle initial
+ **nasaInitials** - *string* - The crew member's initials as assigned by NASA.
+ **sex** - *string* - The crew member's sex
+ **type** - *string* - The crew member's type
+ **isActive** - *bool* - Shows if crewmember is currently active
+ **antropometric** - *object* - The crew member's antropometric sizing data
    + **measurementCollector** - *string* - The name of the technician entering the measurements
    + **height** - *number* - The measurement of the vertical distance from the standing surface to the top of the subject's head.
    + **cervicalHeight** - *number* - The measurement of the vertical distance from the standing surface to the subject's cervical landmark (point on the back of the neck).
    + **midShoulderHeightLeft** - *number* - The measurement of the vertical distance from the standing surface to the left midshoulder landmark (approximately half the distance across the top of the shoulder).
    + **midShoulderHeightRight** - *number* - The measurement of the vertical distance from the standing surface to the right midshoulder landmark (approximately half the distance across the top of the shoulder).
    + **acromionHeight** - *number* - The measurement of the vertical distance from the standing surface to the right acromian landmark (the point where the arm and the clavicle join).
    + **crotchHeight** - *number* - The measurement of the vertical distance from the standing surface up into the crotch until tendon contact is made.
    + **tibialHeight** - *number* - The measurement of the vertical distance from the standing surface to the tibial landmark on the right leg (approximately back of the knee).
    + **armReachLeft** - *number* - The measurement taken from the left hand middle finger tip to the wall when the subject is standing with their back against the wall and arms extended to the front and horizontal to the floor.
    + **armReachRight** - *number* - The measurement taken from the right hand middle finger tip to the all when the subject is standing with their back against the wall and arms extended to the front and horizontal to the floor.
    + **instepHeightLeft** - *number* - The measurement of the subject's left instep at its highest point.
    + **instepHeightRight** - *number* - The measurement of the subject's right instep at its highest point.
    + **footLengthLeft** - *number* - The measurement made of the left foot from the tip of the most protruding toe to the back of the foot.
    + **footLengthRight** - *number* - The measurement made of the right foot from the tip of the most protruding toe to the back of the foot.
    + **footBreadthLeft** - *number* - The measurement made of the left foot at the widest part of the foot.
    + **footBreadthRight** - *number* - The measurement made of the right foot at the widest part of the foot.
    + **shoeSize** - *number* - The size of shoe the subject wears.
    + **shoeWidth** - *string* - The width of the shoe the subject wears.  (A, B, C, D, AA, AAA, E, EE, EEE)
    + **verticalTrunkDiameterLeft** - *number* - The vertical measurement made from the crotch to the left midshoulder landmark.
    + **verticalTrunkDiameterRight** - *number* - The vertical measurement made from the crotch to the right midshoulder landmark.
    + **expandedChest** - *number* - The measurement made of the horizontal depth of the trunk at the level of the bustpoint landmarks at maximum inspiration (deep breath).
    + **interAcromionDistance** - *number* - The measurement of the distance between the acromion tips with arms relaxed at the side.
    + **chestBreadth** - *number* - The horizontal measurement made across the trunk at the level of the bustpoint landmarks.
    + **hipBreadth** - *number* - The measurement of the maximum horizontal breadth of the hips.
    + **bideltoidBreadth** - *number* - The horizontal measurement made across the body at the level of the deltoid landmark.
    + **interFingerTip** - *number* - The measurement of the distance between the two middle finger tips with the arms out stretched parallel to the floor.
    + **interWristDistance** - *number* - The measurement of the distance between the two wrist crease landmarks with arms stretched to the sides parallel with the floor.
    + **interElbowDistance** - *number* - The measurement of the distance between the two radial landmarks.
    + **acromionRadialeLengthLeft** - *number* - The measurement of the distance from the left acromial landmark (shoulder) to the left radial landmark (elbow).
    + **acromionRadialeLengthRight** - *number* - The measurement of the distance from the right acromial landmark (shoulder) to the right radial landmark (elbow).
    + **radialeStylionLengthLeft** - *number* - The measurement of the distance from the left radial landmark to the left stylion landmark.
    + **radialeStylionLengthRight** - *number* - The measurement of the distance from the right radial landmark to the right stylion landmark.
    + **lowerArmLeft** - *number* - The measurement of the distance from the left middle finger to the ulna tip (elbow tip).
    + **lowerArmRight** - *number* - The measurement of the distance from the right middle finger to the ulna tip (elbow tip).
    + **neckCircumference** - *number* - The measurement of the circumference of the neck at the neck shoulder junction.
    + **shoulderCircumference** - *number* - The horizontal measurement of the circumference of the body at the level of the deltoid landmark.
    + **chestCircumference** - *number* - The horizontal measurement of the circumference of the trunk at the level of the bustpoint landmarks (normal inspiration).
    + **bicepsCircumference** - *number* - The measurement of the circumference of the right arm (left arm is not measured) at the level of the biceps landmark.
    + **waistCircumference** - *number* - The measurement of the circumference of the trunk at the level of the waist landmarks.
    + **hipCircumference** - *number* - The measurement of the circumference of the trunk at the maximum protuberence of the buttocks.
    + **thighCircumference** - *number* - The measurement of the circumference of the right upper leg as high in the crotch as possible(left not measured).
    + **verticalTrunkCircumferenceLeft** - *number* - The measurement made with a length of tape passed between the legs, over the protrusion of the left buttock, and up the back to lie over the mid-shoulder landmark and brought over the left bustpoint landmark (tape follows the body contour).
    + **verticalTrunkCircumferenceRight** - *number* - The measurement made with a length of tape passed between the legs, over the protrusion of the left buttock, and up the back to lie over the mid-shoulder landmark and brought over the right bustpoint landmark (tape follows the body contour).
    + **headLength** - *number* - The measurement made from the frontal lobe (forehead) to the occipital bone (bump on the back of the head).
    + **headBreadth** - *number* - The measurement of the maximum width of the head excluding the ears.
    + **bitragionInionArc** - *number* - A measurement between the small projections in front of the external opening of the ears as measured over the back of the head.
    + **sagittalArch** - *number* - The measurement of the distance across the top of the head from glabella (between the brow ridges) to the nuchale at the base of the skull.
    + **headCircumference** - *number* - The measurement of the maximum circumference of the head (passing above the brow ridges).
    + **weight** - *number* - The weight of the crew member, candidate or test subject.
    + **handDominance** - *number* - The subject's dominant hand.
    + **abnormalities** - *number* - Any physical abnormalities noted during sizing.
    + **facialContour** - *number* - This measurement is currently stored in the abnormalities field as text.
    + **InterMidShoulder** - *number* - This measurement is currently stored in the abnormalities field as text.
    + **handMeasurementLeft1** - *number* - One of 22 possible measurements of the left hand, only 13 are currently taken. There is a graphic illustration of the hand that shows the location of where each measurement is to be taken.
    + **handMeasurementLeft3** - *number* - see handMeasurementLeft1 description.
    + **handMeasurementLeft7** - *number* - see handMeasurementLeft1 description.
    + **handMeasurementLeft8** - *number* - see handMeasurementLeft1 description.
    + **handMeasurementLeft9** - *number* - see handMeasurementLeft1 description.
    + **handMeasurementLeft11** - *number* - see handMeasurementLeft1 description.
    + **handMeasurementLeft13** - *number* - see handMeasurementLeft1 description.
    + **handMeasurementLeft15** - *number* - see handMeasurementLeft1 description.
    + **handMeasurementLeft17** - *number* - see handMeasurementLeft1 description.
    + **handMeasurementLeft19** - *number* - see handMeasurementLeft1 description.
    + **handMeasurementLeft20** - *number* - see handMeasurementLeft1 description.
    + **handMeasurementLeft21** - *number* - see handMeasurementLeft1 description.
    + **handMeasurementLeft22** - *number* - see handMeasurementLeft1 description.
    + **handMeasurementRight1** - *number* - One of 22 possible measurements of the right hand, only 13 are currently taken. There is a graphic illustration that shows the location of where each measurement is to be taken.
    + **handMeasurementRight3** - *number* - see handMeasurementRight1 description.
    + **handMeasurementRight5** - *number* - see handMeasurementRight1 description.
    + **handMeasurementRight7** - *number* - see handMeasurementRight1 description.
    + **handMeasurementRight9** - *number* - see handMeasurementRight1 description.
    + **handMeasurementRight11** - *number* - see handMeasurementRight1 description.
    + **handMeasurementRight13** - *number* - see handMeasurementRight1 description.
    + **handMeasurementRight15** - *number* - see handMeasurementRight1 description.
    + **handMeasurementRight17** - *number* - see handMeasurementRight1 description.
    + **handMeasurementRight19** - *number* - see handMeasurementRight1 description.
    + **handMeasurementRight20** - *number* - see handMeasurementRight1 description.
    + **handMeasurementRight21** - *number* - see handMeasurementRight1 description.
    + **handMeasurementRight22** - *number* - see handMeasurementRight1 description.
    
+ Parameters
    + id: 1 (required, number) - ID of the desired document
    
#### Get Crewmember Model [GET]

+ Response 200 (application/json)

        {
            "id": 1,
            "crewId": "1234ABC,
            "firstName": "Collin",
            "lastName": "Estes",
            "middelInitial": "J",
            "nasaInitials": "CJE",
            "sex": "male",
            "type": "astronaut",
            "isActive": true,
            "antropometric": { },
            "audit": { }
        }
        
### CrewMember Collection [/crewmembers(?since)]

+ Parameters
    + since: 01/01/2014 (optional, date) - Only return records that have been updated since the parameter.'
    
#### Get CrewMember Collection [GET]

+ Response 200 (application/json)

        [{
            "id": 1,
            "ptsId": "1234ABC,
            "type": "DD1149",
            "attributes": { },
            "components": { }
        }, {
            "id": 2,
            "ptsId": "1234ABC,
            "type": "JSC250",
            "attributes": { },
            "components": { }
            }
        }]



## group STILL IN WORK
The following items are not incorporated or finalized yet, documentation of these following is in work:

+ **MOCK DATA FIDELITY**
+ Master attributes
+ Master Quantity Model
+ Master/Component calibrations
+ Audit format
+ Shipper Attributes
+ Limited Life format
+ Component Transactions
+ Specific document attributes
+ NBL Immersions
+ Receiving
+ Work Breakdown Structure



## group READY MODELS
The following items are currently ready to work with, including mock data endpoints ready to be consumed.  

There may be further properties added to these models as we iterate over the next couple months. 



###Mock API BASEURL:
> http://private-4a158-emuapi.apiary-mock.com

####[Most Component endpoints](http://docs.emuapi.apiary.io/#reference/components) 
(*not transactions yet*)

####[Most Master endpoints](http://docs.emuapi.apiary.io/#reference/masters) 
(*not quantity yet*)

####[All Event endpoints](http://docs.emuapi.apiary.io/#reference/events)







