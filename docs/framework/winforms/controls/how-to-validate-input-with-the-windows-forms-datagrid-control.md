---
title: 'Como: Validar a entrada com o controle DataGrid do Windows Forms'
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
ms.openlocfilehash: dc8c8f157e6673c1bddc68bfb511683e6d2b99be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796468"
---
# <a name="how-to-validate-input-with-the-windows-forms-datagrid-control"></a><span data-ttu-id="d4947-102">Como: Validar a entrada com o controle DataGrid do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d4947-102">How to: Validate Input with the Windows Forms DataGrid Control</span></span>

> [!NOTE]
> <span data-ttu-id="d4947-103">O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.</span><span class="sxs-lookup"><span data-stu-id="d4947-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="d4947-104">Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="d4947-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>

<span data-ttu-id="d4947-105">Há dois tipos de validação de entrada disponíveis para os formulários do Windows <xref:System.Windows.Forms.DataGrid> controle.</span><span class="sxs-lookup"><span data-stu-id="d4947-105">There are two types of input validation available for the Windows Forms <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="d4947-106">Se o usuário tentar inserir um valor que é de um tipo de dados inaceitável para a célula, por exemplo uma cadeia de caracteres em um número inteiro, o valor inválido será substituído pelo valor anterior.</span><span class="sxs-lookup"><span data-stu-id="d4947-106">If the user attempts to enter a value that is of an unacceptable data type for the cell, for example a string into an integer, the new invalid value is replaced with the old value.</span></span> <span data-ttu-id="d4947-107">Esse tipo de validação de entrada é feita automaticamente e não pode ser personalizada.</span><span class="sxs-lookup"><span data-stu-id="d4947-107">This kind of input validation is done automatically and cannot be customized.</span></span>

<span data-ttu-id="d4947-108">O outro tipo de validação de entrada pode ser usado para rejeitar quaisquer dados inaceitáveis, por exemplo, um valor 0 em um campo que deve ser maior ou igual a 1 ou uma cadeia de caracteres inadequada.</span><span class="sxs-lookup"><span data-stu-id="d4947-108">The other type of input validation can be used to reject any unacceptable data, for example a 0 value in a field that must be greater than or equal to 1, or an inappropriate string.</span></span> <span data-ttu-id="d4947-109">Isso é feito no conjunto de dados, escrevendo um manipulador de eventos para o <xref:System.Data.DataTable.ColumnChanging> ou <xref:System.Data.DataTable.RowChanging> eventos.</span><span class="sxs-lookup"><span data-stu-id="d4947-109">This is done in the dataset by writing an event handler for the <xref:System.Data.DataTable.ColumnChanging> or <xref:System.Data.DataTable.RowChanging> event.</span></span> <span data-ttu-id="d4947-110">O exemplo a seguir usa o <xref:System.Data.DataTable.ColumnChanging> evento porque o valor inaceitável não é permitido para a coluna "Produto" em particular.</span><span class="sxs-lookup"><span data-stu-id="d4947-110">The example below uses the <xref:System.Data.DataTable.ColumnChanging> event because the unacceptable value is disallowed for the "Product" column in particular.</span></span> <span data-ttu-id="d4947-111">Você pode usar o <xref:System.Data.DataTable.RowChanging> evento para verificar se o valor de uma coluna "Data de término" é posterior a coluna "Data de início" na mesma linha.</span><span class="sxs-lookup"><span data-stu-id="d4947-111">You might use the <xref:System.Data.DataTable.RowChanging> event for checking that the value of an "End Date" column is later than the "Start Date" column in the same row.</span></span>

## <a name="to-validate-user-input"></a><span data-ttu-id="d4947-112">Validando entrada do usuário</span><span class="sxs-lookup"><span data-stu-id="d4947-112">To validate user input</span></span>

1. <span data-ttu-id="d4947-113">Escrever código para manipular o <xref:System.Data.DataTable.ColumnChanging> evento na tabela apropriada.</span><span class="sxs-lookup"><span data-stu-id="d4947-113">Write code to handle the <xref:System.Data.DataTable.ColumnChanging> event for the appropriate table.</span></span> <span data-ttu-id="d4947-114">Quando for detectada entrada inadequada, chame o <xref:System.Data.DataRow.SetColumnError%2A> método da <xref:System.Data.DataRow> objeto.</span><span class="sxs-lookup"><span data-stu-id="d4947-114">When inappropriate input is detected, call the <xref:System.Data.DataRow.SetColumnError%2A> method of the <xref:System.Data.DataRow> object.</span></span>

    ```vb
    Private Sub Customers_ColumnChanging(ByVal sender As Object, _
    ByVal e As System.Data.DataColumnChangeEventArgs)
       ' Only check for errors in the Product column
       If (e.Column.ColumnName.Equals("Product")) Then
          ' Do not allow "Automobile" as a product.
          If CType(e.ProposedValue, String) = "Automobile" Then
             Dim badValue As Object = e.ProposedValue
             e.ProposedValue = "Bad Data"
             e.Row.RowError = "The Product column contains an error"
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

2. <span data-ttu-id="d4947-115">Conecte o manipulador de eventos ao evento.</span><span class="sxs-lookup"><span data-stu-id="d4947-115">Connect the event handler to the event.</span></span>

    <span data-ttu-id="d4947-116">Coloque o seguinte código dentro de qualquer um do formulário <xref:System.Windows.Forms.Form.Load> evento ou do construtor.</span><span class="sxs-lookup"><span data-stu-id="d4947-116">Place the following code within either the form's <xref:System.Windows.Forms.Form.Load> event or its constructor.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d4947-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d4947-117">See also</span></span>

- <xref:System.Windows.Forms.DataGrid>
- <xref:System.Data.DataTable.ColumnChanging>
- <xref:System.Data.DataRow.SetColumnError%2A>
- [<span data-ttu-id="d4947-118">Controle DataGrid</span><span class="sxs-lookup"><span data-stu-id="d4947-118">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
