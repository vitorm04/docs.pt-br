---
title: Edições de DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
ms.openlocfilehash: 689a297eb5368d35c2e7dd034426edbe665e7ed2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785392"
---
# <a name="datatable-edits"></a><span data-ttu-id="135ea-102">Edições de DataTable</span><span class="sxs-lookup"><span data-stu-id="135ea-102">DataTable Edits</span></span>
<span data-ttu-id="135ea-103">Quando você altera os valores de coluna em uma <xref:System.Data.DataRow>, as alterações são colocadas imediatamente no estado atual da linha.</span><span class="sxs-lookup"><span data-stu-id="135ea-103">When you make changes to column values in a <xref:System.Data.DataRow>, the changes are immediately placed in the current state of the row.</span></span> <span data-ttu-id="135ea-104">O <xref:System.Data.DataRowState> é então definido como **Modified**, e as alterações são aceitas ou rejeitadas <xref:System.Data.DataRow.AcceptChanges%2A> usando <xref:System.Data.DataRow.RejectChanges%2A> os métodos ou da **DataRow**.</span><span class="sxs-lookup"><span data-stu-id="135ea-104">The <xref:System.Data.DataRowState> is then set to **Modified**, and the changes are accepted or rejected using the <xref:System.Data.DataRow.AcceptChanges%2A> or <xref:System.Data.DataRow.RejectChanges%2A> methods of the **DataRow**.</span></span> <span data-ttu-id="135ea-105">A **DataRow** também fornece três métodos que você pode usar para suspender o estado da linha enquanto estiver editando.</span><span class="sxs-lookup"><span data-stu-id="135ea-105">The **DataRow** also provides three methods that you can use to suspend the state of the row while you are editing it.</span></span> <span data-ttu-id="135ea-106">Esses métodos são <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A> e <xref:System.Data.DataRow.CancelEdit%2A>.</span><span class="sxs-lookup"><span data-stu-id="135ea-106">These methods are <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, and <xref:System.Data.DataRow.CancelEdit%2A>.</span></span>  
  
 <span data-ttu-id="135ea-107">Quando você modifica valores de coluna em uma **DataRow** diretamente, o **DataRow** gerencia os valores de coluna usando as versões de linha **atual**, **padrão**e **original** .</span><span class="sxs-lookup"><span data-stu-id="135ea-107">When you modify column values in a **DataRow** directly, the **DataRow** manages the column values using the **Current**, **Default**, and **Original** row versions.</span></span> <span data-ttu-id="135ea-108">Além dessas versões de linha, os métodos **BeginEdit**, **EndEdit**e **CancelEdit** usam uma quarta versão de linha: **Proposta**.</span><span class="sxs-lookup"><span data-stu-id="135ea-108">In addition to these row versions, the **BeginEdit**, **EndEdit**, and **CancelEdit** methods use a fourth row version: **Proposed**.</span></span> <span data-ttu-id="135ea-109">Para obter mais informações sobre versões de linha, consulte [Estados de linha e versões de linha](row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="135ea-109">For more information about row versions, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="135ea-110">A versão de linha **proposta** existe durante uma operação de edição que começa chamando **BeginEdit** e que termina usando **EndEdit** ou **CancelEdit,** ou chamando **AcceptChanges** ou **RejectChanges**.</span><span class="sxs-lookup"><span data-stu-id="135ea-110">The **Proposed** row version exists during an edit operation that begins by calling **BeginEdit** and that ends either by using **EndEdit** or **CancelEdit,** or by calling **AcceptChanges** or **RejectChanges**.</span></span>  
  
 <span data-ttu-id="135ea-111">Durante a operação de edição, você pode aplicar a lógica de validação a colunas individuais avaliando o **ProposedValue** no evento **ColumnChanged** da **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="135ea-111">During the edit operation, you can apply validation logic to individual columns by evaluating the **ProposedValue** in the **ColumnChanged** event of the **DataTable**.</span></span> <span data-ttu-id="135ea-112">O evento **ColumnChanged** contém **DataColumnChangeEventArgs** que mantêm uma referência à coluna que está sendo alterada e ao **ProposedValue**.</span><span class="sxs-lookup"><span data-stu-id="135ea-112">The **ColumnChanged** event holds **DataColumnChangeEventArgs** that keep a reference to the column that is changing and to the **ProposedValue**.</span></span> <span data-ttu-id="135ea-113">Depois que você avaliar o valor proposto, poderá modificá-lo ou cancelar a edição.</span><span class="sxs-lookup"><span data-stu-id="135ea-113">After you evaluate the proposed value, you can either modify it or cancel the edit.</span></span> <span data-ttu-id="135ea-114">Quando a edição é finalizada, a linha sai do estado **proposto** .</span><span class="sxs-lookup"><span data-stu-id="135ea-114">When the edit is ended, the row moves out of the **Proposed** state.</span></span>  
  
 <span data-ttu-id="135ea-115">Você pode confirmar as edições chamando **EndEdit**ou pode cancelá-las chamando **CancelEdit**.</span><span class="sxs-lookup"><span data-stu-id="135ea-115">You can confirm edits by calling **EndEdit**, or you can cancel them by calling **CancelEdit**.</span></span> <span data-ttu-id="135ea-116">Observe que, embora **EndEdit** confirme suas edições, o **conjunto de DataSet** não aceita realmente as alterações até que **AcceptChanges** seja chamado.</span><span class="sxs-lookup"><span data-stu-id="135ea-116">Note that while **EndEdit** does confirm your edits, the **DataSet** does not actually accept the changes until **AcceptChanges** is called.</span></span> <span data-ttu-id="135ea-117">Observe também que, se você chamar **AcceptChanges** antes de terminar a edição com **EndEdit** ou **CancelEdit**, a edição será finalizada e os valores de linha **proposto** serão aceitos para as versões de linha **atuais** e **originais** .</span><span class="sxs-lookup"><span data-stu-id="135ea-117">Note also that if you call **AcceptChanges** before you have ended the edit with **EndEdit** or **CancelEdit**, the edit is ended and the **Proposed** row values are accepted for both the **Current** and **Original** row versions.</span></span> <span data-ttu-id="135ea-118">Da mesma maneira, chamar **RejectChanges** encerra a edição e descarta as versões de linha **atuais** e **propostas** .</span><span class="sxs-lookup"><span data-stu-id="135ea-118">In the same manner, calling **RejectChanges** ends the edit and discards the **Current** and **Proposed** row versions.</span></span> <span data-ttu-id="135ea-119">Chamar **EndEdit** ou **CancelEdit** depois de chamar **AcceptChanges** ou **RejectChanges** não tem efeito porque a edição já terminou.</span><span class="sxs-lookup"><span data-stu-id="135ea-119">Calling **EndEdit** or **CancelEdit** after calling **AcceptChanges** or **RejectChanges** has no effect because the edit has already ended.</span></span>  
  
 <span data-ttu-id="135ea-120">O exemplo a seguir demonstra como usar **BeginEdit** com **EndEdit** e **CancelEdit**.</span><span class="sxs-lookup"><span data-stu-id="135ea-120">The following example demonstrates how to use **BeginEdit** with **EndEdit** and **CancelEdit**.</span></span> <span data-ttu-id="135ea-121">O exemplo também verifica o **ProposedValue** no evento **ColumnChanged** e decide se a edição deve ser cancelada.</span><span class="sxs-lookup"><span data-stu-id="135ea-121">The example also checks the **ProposedValue** in the **ColumnChanged** event and decides whether to cancel the edit.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="135ea-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="135ea-122">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataRowVersion>
- [<span data-ttu-id="135ea-123">Manipulação de dados em uma DataTable</span><span class="sxs-lookup"><span data-stu-id="135ea-123">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="135ea-124">Manipulação de eventos de DataTable</span><span class="sxs-lookup"><span data-stu-id="135ea-124">Handling DataTable Events</span></span>](handling-datatable-events.md)
- <span data-ttu-id="135ea-125">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="135ea-125">[ADO.NET Overview](../ado-net-overview.md)</span></span>
