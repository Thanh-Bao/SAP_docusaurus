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

-------------------------------------------------------------------------------------------------------

Dưới đây là một số nguyên tắc cơ bản về việc chọn lựa cách sử dụng annotation trong Core Data Services (CDS) của SAP:

1. **Inline Annotations (sử dụng dấu `@`)**
   - Đây là cách đơn giản nhất để thêm annotation vào một phần tử trong mô hình dữ liệu CDS.
   - Sử dụng khi bạn đang tạo mô hình dữ liệu và muốn thêm các annotation ngay lập tức.
   - Nó giúp giữ cho mô hình dữ liệu và các annotation của nó cùng một chỗ, dễ quản lý hơn.

2. **Annotate with {} (sử dụng từ khóa `annotate` với dấu `{}`)**
   - Sử dụng khi bạn muốn thêm hoặc sửa đổi các annotation sau khi mô hình dữ liệu đã được tạo.
   - Điều này đặc biệt hữu ích khi bạn muốn thêm các annotation mà không muốn (hoặc không thể) sửa đổi mô hình dữ liệu gốc.

3. **Annotate with @() (sử dụng từ khóa `annotate` với dấu `@()`)**
   - Tương tự như cách thứ hai, cú pháp này sử dụng khi bạn muốn thêm hoặc sửa đổi các annotation sau khi mô hình dữ liệu đã được tạo.
   - Sự khác biệt là, nó cung cấp cấu trúc rõ ràng hơn cho các annotation phức tạp hơn.

Chung quy lại, lựa chọn cách sử dụng annotation tùy thuộc vào ngữ cảnh và yêu cầu của bạn. Nếu bạn đang tạo mô hình dữ liệu và biết rõ các annotation bạn muốn thêm, sử dụng inline annotations có thể là lựa chọn tốt. Ngược lại, nếu bạn cần thêm các annotation vào một mô hình dữ liệu hiện có, sử dụng `annotate` sẽ là lựa chọn phù hợp.
