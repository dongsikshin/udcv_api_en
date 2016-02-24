.. _api-mq-label:

Message Queue API
------------------

Summary
^^^^^^^^^^^

uDCV leverage Apache Active MQ http://activemq.apache.org , as Message API, which:

.. csv-table:: **MQ**
    :header: Queue Name, Usage
    :widths: 40,60

    asset,Asset Data
    perf,Performance Data
    event,Event Data

.. note::
   * The data format of Message body is JSON.
   * Default MQ listening port is ``61616``

asset 
^^^^^^^^^^

.. csv-table:: **asset**
    :header: Name, Value, Type 
    :widths: 40,40, 20

    _operation_,add|upd|del,String
    _sc_,scene name, String
    _pool_,catalog,String
    _id_,primary key,String
    _data_,asset properties,JSON

**Example**

.. code-block:: json
    :linenos:

    [  
       {  
          "_operation_":"upd",
          "_sc_":"t1",
          "_pool_":"rackDevice",
          "_id_":"dtz",
          "_data_":{  
             "ID":"dtz",
             "Name":"VM-DB2",
             "belongTo":"P311-A1-01",
             "CPU":"4",
             "Memory":"4096111M",
             "OS":"WinServer 2008 R2 (64-bit)",
             "site":"23-25",
             "layout":"12",
             "deviceType":"IBMSystem"
          }
       }
    ]


perf
^^^^^^^^^^^^^

.. csv-table:: **perf**
    :header: Name, Value, Type 
    :widths: 40,40, 20

    scene,scene name,String
    id,CI id,String
    app,Performance group name,Stirng
    inst,Performance instance name,String
    param,Performance name,String
    type,numerical|status,String
    unit,Performance unit,String
    val, Performance value, String or Double

**Example**

.. code-block:: json
    :linenos:

    [
       {
          "scene":"demo",
          "key":"",
          "id":"ds003Server",
          "app":"seltImport",
          "inst":"_",
          "param":"temperature",
          "type":"numerical",
          "unit":"%",
          "val":"58",
          "time":1431405196437
       },
       {
          "scene":"demo",
          "key":"",
          "id":"ds002Server",
          "app":"seltImport",
          "inst":"_",
          "param":"temperature",
          "type":"status",
          "unit":"%",
          "val":"xxx58",
          "time":1431405196437
       }
    ]

event
^^^^^^^^^^^^

.. csv-table:: **perf**
    :header: Name, Value, Type 
    :widths: 40,40, 20

    scene,scene name,String
    id,CI id,String
    title,Event title,Stirng
    status,open|close,String
    severity,1|2|3|4|5|6,String
    msg,Event body,String
    time,Event occurrence time,Long
    modifyTime,Event modify time,Long
    arg1,Extended field (optional),String
    arg2,Extended field (optional),String

**Example**

.. code-block:: json
    :linenos:

    [
       {
          "scene":"demo",
          "key":"",
          "id":"d03server",
          "title":"CPU High",
          "status":"OPEN",
          "severity":"1",
          "msg":"CPU usage is over 90% over 5 minutes",
          "time":1431405196437,
          "modifyTime":1431405196437,
          "arg1":"",
          "arg2":""
       },
       {
          "scene":"demo",
          "key":"",
          "id":"d03server",
          "title":"Disk Full",
          "status":"CLOSED",
          "severity":"1",
          "msg":"Disk usage is over 70%",
          "time":1431405196437,
          "modifyTime":1431405196437,
          "arg1":"",
          "arg2":""
       }
    ]







