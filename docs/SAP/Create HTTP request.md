## HTTP GET

```ABAP {13-23}

CLASS z_hello123 DEFINITION
  PUBLIC .

  PUBLIC SECTION.
    INTERFACES: if_oo_adt_classrun.
ENDCLASS.

CLASS z_hello123 IMPLEMENTATION.

  METHOD if_oo_adt_classrun~main.

    DATA: lo_http_client TYPE REF TO if_web_http_client.

    lo_http_client = cl_web_http_client_manager=>create_by_http_destination(
    i_destination = cl_http_destination_provider=>create_by_url( 'https://jsonplaceholder.typicode.com/todos1' )
    ).

    DATA(lo_request) = lo_http_client->get_http_request(  ).

    DATA(lv_response) = lo_http_client->execute( i_method = if_web_http_client=>get )->get_text(  ).

    out->write( lv_response ).

ENDMETHOD.

ENDCLASS.

```

**Run**

![](/img/SAP/2023-03-20_14-23-44.png)
