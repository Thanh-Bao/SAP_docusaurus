## HTTP GET

```ABAP {13-19}

CLASS z_hello123 DEFINITION
  PUBLIC .

  PUBLIC SECTION.
    INTERFACES: if_oo_adt_classrun.
ENDCLASS.

CLASS z_hello123 IMPLEMENTATION.

  METHOD if_oo_adt_classrun~main.

    DATA(lo_http_client) = cl_web_http_client_manager=>create_by_http_destination( cl_http_destination_provider=>create_by_url( 'https://jsonplaceholder.typicode.com/todos/1' ) ).

    DATA(lo_request) = lo_http_client->get_http_request(  ).

    DATA(lv_response) = lo_http_client->execute( if_web_http_client=>GET )->get_text(  ).

    out->write( lv_response  ).

ENDMETHOD.

ENDCLASS.

```

❇️ **Run**

![](/img/SAP/2023-03-20_14-23-44.png)

❇️ **Check data type of response**

```
out->write( cl_abap_typedescr=>describe_by_data( lv_response )->absolute_name ).
```

result: `\TYPE=STRING`
