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

-------------------------------------------------------------------------------------------------------------

Dưới đây là thêm một số annotations phổ biến khác trong SAP CDS:

1. `@OData.publish`: Được sử dụng để xuất bản một service hoặc entity set dưới dạng OData service.

2. `@UI.selectionVariant`: Được sử dụng để xác định các trường được sử dụng như các trường chọn trong một selection screen.

3. `@UI.presentationVariant`: Được sử dụng để xác định cách các dữ liệu được sắp xếp và hiển thị trong UI.

4. `@UI.facet`: Được sử dụng để định rõ cấu trúc và hiển thị của các phần khác nhau của một trang chi tiết.

5. `@Analytics.query`: Được sử dụng để xác định rằng một thực thể hoặc view nên được sử dụng như một query để phân tích.

6. `@ObjectModel.createEnabled`: Được sử dụng để xác định rằng người dùng có thể tạo mới các bản ghi của một thực thể hoặc không.

7. `@ObjectModel.updateEnabled`: Được sử dụng để xác định rằng người dùng có thể cập nhật các bản ghi của một thực thể hoặc không.

8. `@ObjectModel.deleteEnabled`: Được sử dụng để xác định rằng người dùng có thể xóa các bản ghi của một thực thể hoặc không.

9. `@Metadata.allowedValues`: Được sử dụng để chỉ định các giá trị cho phép cho một trường cụ thể.

10. `@Common.text`: Được sử dụng để cung cấp mô tả văn bản cho một trường hoặc một thực thể.

Như đã nói ở trên, đây chỉ là một số annotations phổ biến. SAP CDS cung cấp rất nhiều annotations khác nữa cho các mục đích và yêu cầu khác nhau.


______________________________________________


Tần suất sử dụng và mức độ phổ biến của các annotations trong SAP CDS có thể phụ thuộc rất nhiều vào ngữ cảnh và yêu cầu cụ thể của ứng dụng bạn đang phát triển. Tuy nhiên, dựa trên kinh nghiệm chung, dưới đây là một sắp xếp gần đúng theo mức độ phổ biến:

1. `@UI.hidden`
2. `@UI.lineItem`
3. `@EndUserText.label`
4. `@UI.selectionField`
5. `@UI.identification`
6. `@OData.publish`
7. `@UI.fieldGroup`
8. `@UI.headerInfo`
9. `@ObjectModel.readOnly`
10. `@ObjectModel.createEnabled`
11. `@ObjectModel.updateEnabled`
12. `@ObjectModel.deleteEnabled`
13. `@UI.selectionVariant`
14. `@UI.presentationVariant`
15. `@UI.facet`
16. `@Analytics.query`
17. `@Metadata.allowedValues`
18. `@Common.text`
19. `@Communication.contactPerson`

Lưu ý rằng sắp xếp này có thể khác nhau tùy thuộc vào yêu cầu cụ thể của dự án và mô hình dữ liệu mà bạn đang làm việc. Cũng nhớ rằng có nhiều annotation khác không được liệt kê ở đây mà bạn có thể tìm thấy hữu ích trong các tình huống cụ thể.
