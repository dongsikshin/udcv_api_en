.. _api-ws-label:

Web Service API
================

Summary
--------

uDCV provides web service API to manipulate assets, performance and event data.
A typical web service invoke in Java  as following :

.. code-block:: java
    :linenos:

    import org.apache.cxf.endpoint.Client;
    import org.apache.cxf.jaxws.endpoint.dynamic.JaxWsDynamicClientFactory;

    /**
    * @Title: callService
    * @Description: 
    * @return：Client
    */

    public static Client callService() {
        JaxWsDynamicClientFactory dcf = JaxWsDynamicClientFactory.newInstance();
        Client client = dcf.createClient("http://localhost:8080/uinv_dev/services/DataStream?wsdl");
        return client;
    }

    public static void main(String[] args) {
        String pushData = "[{"scene":"demo","key":"","id":"ds003Server","app":"seltImport","inst":"_","param":"temperature","type":"numberic","unit":"%","val":"58","time": 1431405196437},{"scene":"demo","key":"","id":"ds002Server","app":"seltImport","inst":"_","param":"temperature","type":"status","unit":"%","val":"xxx58","time":1431405196437}]";
        Object[] res = null;
        try {
            res = client.invoke("pushMonitor", pushData);
        } catch (Exception e) {
            e.printStackTrace();
        }
        return (String) res[0];
    }


Performance Service
---------------------

.. csv-table:: **Usage**
    :header: Arguments, Value
    :widths: 40,60

    URL, "http://localhost:8080/uinv_dev/services/DataStream?wsdl"
    Function Name,pushMonitor
    Input Parameter, performance data in JSON format

**Example**

.. code-block:: java
    :linenos:

    public static void main(String[] args) {
        String pushData = "[{"scene":"demo","key":"","id":"ds003Server","app":"seltImport","inst":"_","param":"temperature","type":"numberic","unit":"%","val":"58","time": 1431405196437},{"scene":"demo","key":"","id":"ds002Server","app":"seltImport","inst":"_","param":"temperature","type":"status","unit":"%","val":"xxx58","time":1431405196437}]";
        Object[] res = null;
        try {
            res = client.invoke("pushMonitor", pushData);
        } catch (Exception e) {
            e.printStackTrace();
        }
        return (String) res[0];
    }

|

Monitoring Service
---------------------

.. csv-table:: **Usage**
    :header: Arguments, Value
    :widths: 40,60

    URL, "http://localhost:8080/uinv_dev/services/DataStream?wsdl"
    Function Name,pushAlarm
    Input Parameter, alarm data in JSON format

**Example**

.. code-block:: java
    :linenos:

    String pushData= "[{"scene":"demo","key":"","id":"d03server","title":"alarm title","status":"OPEN","severity":"1","msg":"alarm boday","time":1431405196437,"modifyTime":1431405196437,"arg1":"","arg2":""},{"scene":"demo","key":"","id":"d03server","title":"alarm title2","status":"CLOSED","severity":"1","msg":"alarm body 2","time":1431405196437,"modifyTime":1431405196437,"arg1":"","arg2":""}]";
    
    Object[] res = null;

    try {
        res = client.invoke("pushAlarm", pushData);
    } catch (Exception e) {
        e.printStackTrace();
    }
        return (String) res[0];
    }

Asset Service
---------------------

Add Asset
^^^^^^^^^^^^

.. csv-table:: **Usage**
    :header: Arguments, Value
    :widths: 40,60

    URL, "http://localhost:8080/uinv_dev/services/DataStream?wsdl"
    Function Name,addRackEquipment
    Input Parameter, data in JSON format


.. code-block:: java
    :linenos:

    public static void main(String[] args) {
        String pushData= "{\"type\":\"rackDevice\",\"BizID\":\"FX10023100234\",\"Name\" : \"FX10023100234\",\"belongTo\" : \"P310-E-08\", \"location\" : \"\",\"deviceType\" : \"IBM System x3650\",\"site\":\"12-13\",\"ID\": \"IBM System x3650\", \"CabinetID\": \"\", \"Name\": \"FX10023100234\"}";
        Object[] res = null;
        try {
            res = client.invoke("addRackEquipment", pushData);
        } catch (Exception e) {
            e.printStackTrace();
        }
        return (String) res[0];
    }







