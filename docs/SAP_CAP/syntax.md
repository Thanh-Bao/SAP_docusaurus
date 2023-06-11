Annotation trong SAP CAP thường tuân theo cú pháp chuẩn như sau:

```CDS
annotate <Entity|Service> with {
    @<AnnotationType>: <AnnotationValue>
};
```

Trong đó:

- `<Entity|Service>` là tên của thực thể (Entity) hoặc dịch vụ (Service) mà bạn muốn thêm annotation vào.

- `<AnnotationType>` là tên của annotation mà bạn muốn thêm. Có nhiều loại annotation khác nhau, mỗi loại có mục đích và cú pháp giá trị riêng.

- `<AnnotationValue>` là giá trị của annotation. Cú pháp của giá trị này phụ thuộc vào loại annotation.

Ví dụ:

```CDS
annotate ProductService.Products with {
    @UI.LineItem: [
        {
            $Type: 'UI.DataField',
            Value: 'name',
            Label: 'Product Name'
        },
        {
            $Type: 'UI.DataField',
            Value: 'price',
            Label: 'Price'
        }
    ]
};
```

Trong ví dụ trên, `ProductService.Products` là thực thể được annotate; `UI.LineItem` là loại annotation, và mảng các đối tượng `{ $Type: 'UI.DataField', ... }` là giá trị của annotation. Với annotation này, hai trường 'name' và 'price' của thực thể 'Products' sẽ được hiển thị trong danh sách hoặc bảng với nhãn 'Product Name' và 'Price' tương ứng.


_______________________________________________


Trong một số trường hợp, việc sử dụng `$Type` trong annotation không bắt buộc. `$Type` được sử dụng để chỉ định loại của một đối tượng cụ thể trong một mảng annotations.

Ví dụ, khi bạn đang làm việc với `@UI.LineItem`, `$Type` có thể được sử dụng để chỉ định loại của mỗi trường dữ liệu, ví dụ `$Type: 'UI.DataField'` hoặc `$Type: 'UI.DataFieldForAnnotation'`.

Tuy nhiên, nếu bạn không cung cấp `$Type`, mặc định sẽ là `UI.DataField`. Điều này có nghĩa là nếu bạn chỉ muốn hiển thị một số trường cơ bản mà không cần tùy chỉnh gì thêm, bạn có thể bỏ qua `$Type` và chỉ cần cung cấp `Value` cho mỗi trường.

Dưới đây là một ví dụ:

```CDS
annotate ProductService.Products with {
    @UI.LineItem: [
        { Value: 'name' },
        { Value: 'price' }
    ]
};
```

Trong ví dụ này, `name` và `price` sẽ được hiển thị mà không cần tùy chỉnh label hoặc các thuộc tính khác.
