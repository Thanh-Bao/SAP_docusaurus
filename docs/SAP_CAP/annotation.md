### Phân loại data annotation

 CDS (Core Data Services) của SAP cung cấp ba cú pháp khác nhau để tạo ra annotation. Chúng được sử dụng tùy thuộc vào ngữ cảnh cụ thể và yêu cầu của mô hình dữ liệu. 

1. **Inline Annotations**: Sử dụng dấu `@` ngay trước khai báo phần tử dữ liệu. Inline annotations được viết ngay tại vị trí của phần tử được chú thích.

    ```CDS
    @UI.headerInfo: {
      title: 'Employee',
      typeName: 'Employee',
      typeNamePlural: 'Employees',
      description: { value: 'firstName' }
    }
    entity Employees {
      key EmployeeID : Integer;
      FirstName : String;
      LastName : String;
      Country : String;
    }
    ```

2. **Annotate with {}**: Dùng từ khóa `annotate` với dấu `{}` để thêm annotations sau khi phần tử dữ liệu đã được khai báo. 

    ```CDS
    annotate Employees with {
      @UI.headerInfo: {
        title: 'Employee',
        typeName: 'Employee',
        typeNamePlural: 'Employees',
        description: { value: 'firstName' }
      }
      FirstName;
      LastName;
      Country;
    }
    ```

3. **Annotate with @()**: Kết hợp cả từ khóa `annotate` và dấu `@()`. 

    ```CDS
    annotate Employees with @(
      UI: {
        headerInfo: {
          title: 'Employee',
          typeName: 'Employee',
          typeNamePlural: 'Employees',
          description: { value: 'firstName' }
        }
      }
    ) FirstName;
    ```
    
    ***Summary***
    
- Inline Annotations (dùng dấu @)
- Annotate with {} (sử dụng từ khóa annotate với dấu {})
- Annotate with @() (sử dụng từ khóa annotate với dấu @())

.
