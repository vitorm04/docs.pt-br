---
title: Edições de DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
ms.openlocfilehash: 9e8c4204b51121b147fc7614066d9b849a687574
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151254"
---
# <a name="datatable-edits"></a><span data-ttu-id="5bc54-102">Edições de DataTable</span><span class="sxs-lookup"><span data-stu-id="5bc54-102">DataTable Edits</span></span>
<span data-ttu-id="5bc54-103">Quando você altera os valores de coluna em uma <xref:System.Data.DataRow>, as alterações são colocadas imediatamente no estado atual da linha.</span><span class="sxs-lookup"><span data-stu-id="5bc54-103">When you make changes to column values in a <xref:System.Data.DataRow>, the changes are immediately placed in the current state of the row.</span></span> <span data-ttu-id="5bc54-104">Em <xref:System.Data.DataRowState> seguida, é definido como **Modificado,** e as <xref:System.Data.DataRow.AcceptChanges%2A> <xref:System.Data.DataRow.RejectChanges%2A> alterações são aceitas ou rejeitadas usando os ou métodos do **DataRow**.</span><span class="sxs-lookup"><span data-stu-id="5bc54-104">The <xref:System.Data.DataRowState> is then set to **Modified**, and the changes are accepted or rejected using the <xref:System.Data.DataRow.AcceptChanges%2A> or <xref:System.Data.DataRow.RejectChanges%2A> methods of the **DataRow**.</span></span> <span data-ttu-id="5bc54-105">O **DataRow** também fornece três métodos que você pode usar para suspender o estado da linha enquanto você está editando-a.</span><span class="sxs-lookup"><span data-stu-id="5bc54-105">The **DataRow** also provides three methods that you can use to suspend the state of the row while you are editing it.</span></span> <span data-ttu-id="5bc54-106">Esses métodos são <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A> e <xref:System.Data.DataRow.CancelEdit%2A>.</span><span class="sxs-lookup"><span data-stu-id="5bc54-106">These methods are <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, and <xref:System.Data.DataRow.CancelEdit%2A>.</span></span>  
  
 <span data-ttu-id="5bc54-107">Quando você modifica os valores da coluna diretamente em um **DataRow,** o **DataRow** gerencia os valores da coluna usando as versões de linha **Atual,** **Padrão**e **Original.**</span><span class="sxs-lookup"><span data-stu-id="5bc54-107">When you modify column values in a **DataRow** directly, the **DataRow** manages the column values using the **Current**, **Default**, and **Original** row versions.</span></span> <span data-ttu-id="5bc54-108">Além dessas versões de linha, os métodos **BeginEdit,** **EndEdit**e **CancelEdit** usam uma versão da quarta linha: **Proposta**.</span><span class="sxs-lookup"><span data-stu-id="5bc54-108">In addition to these row versions, the **BeginEdit**, **EndEdit**, and **CancelEdit** methods use a fourth row version: **Proposed**.</span></span> <span data-ttu-id="5bc54-109">Para obter mais informações sobre versões de linha, consulte [Row States e Row Versions](row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="5bc54-109">For more information about row versions, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="5bc54-110">A versão **de** linha proposta existe durante uma operação de edição que começa chamando **BeginEdit** e que termina usando **EndEdit** ou **CancelEdit,** ou chamando **AcceptChanges** ou **RejectChanges**.</span><span class="sxs-lookup"><span data-stu-id="5bc54-110">The **Proposed** row version exists during an edit operation that begins by calling **BeginEdit** and that ends either by using **EndEdit** or **CancelEdit,** or by calling **AcceptChanges** or **RejectChanges**.</span></span>  
  
 <span data-ttu-id="5bc54-111">Durante a operação de edição, você pode aplicar a lógica de validação a colunas individuais avaliando o **Evento PropostoValor** no evento **ColunaAlterar** da Tabela de **Dados**.</span><span class="sxs-lookup"><span data-stu-id="5bc54-111">During the edit operation, you can apply validation logic to individual columns by evaluating the **ProposedValue** in the **ColumnChanged** event of the **DataTable**.</span></span> <span data-ttu-id="5bc54-112">O evento **ColunaAlterar** mantém **DataColumnChangeEventArgs** que mantém uma referência à coluna que está mudando e ao **Valor proposto**.</span><span class="sxs-lookup"><span data-stu-id="5bc54-112">The **ColumnChanged** event holds **DataColumnChangeEventArgs** that keep a reference to the column that is changing and to the **ProposedValue**.</span></span> <span data-ttu-id="5bc54-113">Depois que você avaliar o valor proposto, poderá modificá-lo ou cancelar a edição.</span><span class="sxs-lookup"><span data-stu-id="5bc54-113">After you evaluate the proposed value, you can either modify it or cancel the edit.</span></span> <span data-ttu-id="5bc54-114">Quando a edição é terminada, a linha sai do estado **proposto.**</span><span class="sxs-lookup"><span data-stu-id="5bc54-114">When the edit is ended, the row moves out of the **Proposed** state.</span></span>  
  
 <span data-ttu-id="5bc54-115">Você pode confirmar edições chamando **EndEdit**ou cancelá-las ligando para **CancelEdit**.</span><span class="sxs-lookup"><span data-stu-id="5bc54-115">You can confirm edits by calling **EndEdit**, or you can cancel them by calling **CancelEdit**.</span></span> <span data-ttu-id="5bc54-116">Observe que, embora **o EndEdit** confirme suas edições, o **DataSet** não aceita as alterações até **que as Alterações sejam** chamadas.</span><span class="sxs-lookup"><span data-stu-id="5bc54-116">Note that while **EndEdit** does confirm your edits, the **DataSet** does not actually accept the changes until **AcceptChanges** is called.</span></span> <span data-ttu-id="5bc54-117">Observe também que se você chamar **AcceptChanges** antes de terminar a edição com **EndEdit** ou **CancelEdit,** a edição será encerrada e os valores de linha **propostos** serão aceitos para as versões de linha **Atual** e **Original.**</span><span class="sxs-lookup"><span data-stu-id="5bc54-117">Note also that if you call **AcceptChanges** before you have ended the edit with **EndEdit** or **CancelEdit**, the edit is ended and the **Proposed** row values are accepted for both the **Current** and **Original** row versions.</span></span> <span data-ttu-id="5bc54-118">Da mesma forma, chamar **RejectChanges** termina a edição e descarta as versões de linha **Atual** e **Proposta.**</span><span class="sxs-lookup"><span data-stu-id="5bc54-118">In the same manner, calling **RejectChanges** ends the edit and discards the **Current** and **Proposed** row versions.</span></span> <span data-ttu-id="5bc54-119">Chamar **EndEdit** ou **CancelEdit** depois de chamar **AcceptChanges** ou **RejectChanges** não tem efeito porque a edição já terminou.</span><span class="sxs-lookup"><span data-stu-id="5bc54-119">Calling **EndEdit** or **CancelEdit** after calling **AcceptChanges** or **RejectChanges** has no effect because the edit has already ended.</span></span>  
  
 <span data-ttu-id="5bc54-120">O exemplo a seguir demonstra como usar **BeginEdit** com **EndEdit** e **CancelEdit**.</span><span class="sxs-lookup"><span data-stu-id="5bc54-120">The following example demonstrates how to use **BeginEdit** with **EndEdit** and **CancelEdit**.</span></span> <span data-ttu-id="5bc54-121">O exemplo também verifica o **Valor proposto** no evento **ColunaAlterou** e decide se cancela a edição.</span><span class="sxs-lookup"><span data-stu-id="5bc54-121">The example also checks the **ProposedValue** in the **ColumnChanged** event and decides whether to cancel the edit.</span></span>  
  
```vb  
Dim workTable As DataTable = New DataTable  
workTable.Columns.Add("LastName", Type.GetType("System.String"))  
  
AddHandler workTable.ColumnChanged, _  
  New DataColumnChangeEventHandler(AddressOf OnColumnChanged)  
  
Dim workRow As DataRow = workTable.NewRow()  
workRow(0) = "Smith"  
workTable.Rows.Add(workRow)  
  
workRow.BeginEdit()  
' Causes the ColumnChanged event to write a message and cancel the edit.  
workRow(0) = ""
workRow.EndEdit()  
  
' Displays "Smith, New".  
Console.WriteLine("{0}, {1}", workRow(0), workRow.RowState)  
  
Private Shared Sub OnColumnChanged( _  
  sender As Object, args As DataColumnChangeEventArgs)  
  If args.Column.ColumnName = "LastName" Then  
    If args.ProposedValue.ToString() = "" Then  
      Console.WriteLine("Last Name cannot be blank.  Edit canceled.")  
      args.Row.CancelEdit()  
    End If  
  End If  
End Sub  
```  
  
```csharp  
DataTable workTable  = new DataTable();  
workTable.Columns.Add("LastName", typeof(String));  
  
workTable.ColumnChanged +=
  new DataColumnChangeEventHandler(OnColumnChanged);  
  
DataRow workRow = workTable.NewRow();  
workRow[0] = "Smith";  
workTable.Rows.Add(workRow);  
  
workRow.BeginEdit();  
// Causes the ColumnChanged event to write a message and cancel the edit.  
workRow[0] = "";
workRow.EndEdit();  
  
// Displays "Smith, New".  
Console.WriteLine("{0}, {1}", workRow[0], workRow.RowState);
  
protected static void OnColumnChanged(  
  Object sender, DataColumnChangeEventArgs args)  
{  
  if (args.Column.ColumnName == "LastName")  
    if (args.ProposedValue.ToString() == "")  
    {  
      Console.WriteLine("Last Name cannot be blank. Edit canceled.");  
      args.Row.CancelEdit();  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="5bc54-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="5bc54-122">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataRowVersion>
- [<span data-ttu-id="5bc54-123">Manipulando dados em uma DataTable</span><span class="sxs-lookup"><span data-stu-id="5bc54-123">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="5bc54-124">Manipulação de eventos de DataTable</span><span class="sxs-lookup"><span data-stu-id="5bc54-124">Handling DataTable Events</span></span>](handling-datatable-events.md)
- [<span data-ttu-id="5bc54-125">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5bc54-125">ADO.NET Overview</span></span>](../ado-net-overview.md)
