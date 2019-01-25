---
title: 'Como: Validar a entrada com o controle DataGrid dos Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid control [Windows Forms], examples
- user input [Windows Forms], validating
- examples [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], validating input
- validation [Windows Forms], user input
ms.assetid: f1e9c3a0-d0a1-4893-a615-b4b0db046c63
ms.openlocfilehash: 55de6fc1ef4fdf94495ddb07f3329ef9d46b5818
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609480"
---
# <a name="how-to-validate-input-with-the-windows-forms-datagrid-control"></a>Como: Validar a entrada com o controle DataGrid dos Windows Forms
> [!NOTE]
>  O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado. Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Há dois tipos de validação de entrada disponíveis para os formulários do Windows <xref:System.Windows.Forms.DataGrid> controle. Se o usuário tentar inserir um valor que é de um tipo de dados inaceitável para a célula, por exemplo uma cadeia de caracteres em um número inteiro, o valor inválido será substituído pelo valor anterior. Esse tipo de validação de entrada é feita automaticamente e não pode ser personalizada.  
  
 O outro tipo de validação de entrada pode ser usado para rejeitar quaisquer dados inaceitáveis, por exemplo, um valor 0 em um campo que deve ser maior ou igual a 1 ou uma cadeia de caracteres inadequada. Isso é feito no conjunto de dados, escrevendo um manipulador de eventos para o <xref:System.Data.DataTable.ColumnChanging> ou <xref:System.Data.DataTable.RowChanging> eventos. O exemplo a seguir usa o <xref:System.Data.DataTable.ColumnChanging> evento porque o valor inaceitável não é permitido para a coluna "Produto" em particular. Você pode usar o <xref:System.Data.DataTable.RowChanging> evento para verificar se o valor de uma coluna "Data de término" é posterior a coluna "Data de início" na mesma linha.  
  
### <a name="to-validate-user-input"></a>Validando entrada do usuário  
  
1.  Escrever código para manipular o <xref:System.Data.DataTable.ColumnChanging> evento na tabela apropriada. Quando for detectada entrada inadequada, chame o <xref:System.Data.DataRow.SetColumnError%2A> método da <xref:System.Data.DataRow> objeto.  
  
    ```vb  
    Private Sub Customers_ColumnChanging(ByVal sender As Object, _  
    ByVal e As System.Data.DataColumnChangeEventArgs)  
       ' Only check for errors in the Product column  
       If (e.Column.ColumnName.Equals("Product")) Then  
          ' Do not allow "Automobile" as a product.  
          If CType(e.ProposedValue, String) = "Automobile" Then  
             Dim badValue As Object = e.ProposedValue  
             e.ProposedValue = "Bad Data"  
             e.Row.RowError = "The Product column contians an error"  
             e.Row.SetColumnError(e.Column, "Product cannot be " & _  
             CType(badValue, String))  
          End If  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    //Handle column changing events on the Customers table  
    private void Customers_ColumnChanging(object sender, System.Data.DataColumnChangeEventArgs e) {  
  
       //Only check for errors in the Product column  
       if (e.Column.ColumnName.Equals("Product")) {  
  
          //Do not allow "Automobile" as a product  
          if (e.ProposedValue.Equals("Automobile")) {  
             object badValue = e.ProposedValue;  
             e.ProposedValue = "Bad Data";  
             e.Row.RowError = "The Product column contains an error";  
             e.Row.SetColumnError(e.Column, "Product cannot be " + badValue);  
          }  
       }  
    }  
    ```  
  
2.  Conecte o manipulador de eventos ao evento.  
  
     Coloque o seguinte código dentro de qualquer um do formulário <xref:System.Windows.Forms.Form.Load> evento ou do construtor.  
  
    ```vb  
    ' Assumes the grid is bound to a dataset called customersDataSet1  
    ' with a table called Customers.  
    ' Put this code in the form's Load event or its constructor.  
    AddHandler customersDataSet1.Tables("Customers").ColumnChanging, AddressOf Customers_ColumnChanging  
    ```  
  
    ```csharp  
    // Assumes the grid is bound to a dataset called customersDataSet1  
    // with a table called Customers.  
    // Put this code in the form's Load event or its constructor.  
    customersDataSet1.Tables["Customers"].ColumnChanging += new DataColumnChangeEventHandler(this.Customers_ColumnChanging);  
    ```  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.DataGrid>
- <xref:System.Data.DataTable.ColumnChanging>
- <xref:System.Data.DataRow.SetColumnError%2A>
- [Controle DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
