---
title: Adicionando dados a um DataTable
description: Consulte este código de exemplo para adicionar novas linhas de dados a uma tabela no ADO.NET, depois de criar uma DataTable e definir sua estrutura usando colunas e restrições.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d6aa8474-7bde-48f7-949d-20dc38a1625b
ms.openlocfilehash: aac2d90cc57a4af823c42f8c7eb2adcd43c63caf
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164812"
---
# <a name="adding-data-to-a-datatable"></a><span data-ttu-id="b30b1-103">Adicionando dados a um DataTable</span><span class="sxs-lookup"><span data-stu-id="b30b1-103">Adding Data to a DataTable</span></span>

<span data-ttu-id="b30b1-104">Depois de criar <xref:System.Data.DataTable> e definir sua estrutura usando colunas e restrições, você pode adicionar novas linhas de dados à tabela.</span><span class="sxs-lookup"><span data-stu-id="b30b1-104">After you create a <xref:System.Data.DataTable> and define its structure using columns and constraints, you can add new rows of data to the table.</span></span> <span data-ttu-id="b30b1-105">Para adicionar uma nova linha, declare uma nova variável como tipo <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="b30b1-105">To add a new row, declare a new variable as type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="b30b1-106">Um novo objeto **DataRow** é retornado quando você chama o <xref:System.Data.DataTable.NewRow%2A> método.</span><span class="sxs-lookup"><span data-stu-id="b30b1-106">A new **DataRow** object is returned when you call the <xref:System.Data.DataTable.NewRow%2A> method.</span></span> <span data-ttu-id="b30b1-107">Em seguida, a **DataTable** cria o objeto **DataRow** com base na estrutura da tabela, conforme definido pelo <xref:System.Data.DataColumnCollection> .</span><span class="sxs-lookup"><span data-stu-id="b30b1-107">The **DataTable** then creates the **DataRow** object based on the structure of the table, as defined by the <xref:System.Data.DataColumnCollection>.</span></span>  
  
 <span data-ttu-id="b30b1-108">O exemplo a seguir demonstra como criar uma nova linha chamando o método **NewRow** .</span><span class="sxs-lookup"><span data-stu-id="b30b1-108">The following example demonstrates how to create a new row by calling the **NewRow** method.</span></span>  
  
```vb  
Dim workRow As DataRow = workTable.NewRow()  
```  
  
```csharp  
DataRow workRow = workTable.NewRow();  
```  
  
 <span data-ttu-id="b30b1-109">Você pode manipular a linha recém-adicionada usando um índice ou o nome da coluna, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b30b1-109">You then can manipulate the newly added row using an index or the column name, as shown in the following example.</span></span>  
  
```vb  
workRow("CustLName") = "Smith"  
workRow(1) = "Smith"  
```  
  
```csharp  
workRow["CustLName"] = "Smith";  
workRow[1] = "Smith";  
```  
  
 <span data-ttu-id="b30b1-110">Depois que os dados são inseridos na nova linha, o método **Add** é usado para adicionar a linha ao <xref:System.Data.DataRowCollection> , mostrada no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b30b1-110">After data is inserted into the new row, the **Add** method is used to add the row to the <xref:System.Data.DataRowCollection>, shown in the following code.</span></span>  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 <span data-ttu-id="b30b1-111">Você também pode chamar o método **Add** para adicionar uma nova linha passando uma matriz de valores, digitada como <xref:System.Object> , conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b30b1-111">You can also call the **Add** method to add a new row by passing in an array of values, typed as <xref:System.Object>, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 <span data-ttu-id="b30b1-112">Passar uma matriz de valores, tipado como **objeto**, para o método **Add** cria uma nova linha dentro da tabela e define seus valores de coluna para os valores na matriz de objetos.</span><span class="sxs-lookup"><span data-stu-id="b30b1-112">Passing an array of values, typed as **Object**, to the **Add** method creates a new row inside the table and sets its column values to the values in the object array.</span></span> <span data-ttu-id="b30b1-113">Observe que os valores na matriz são correspondidos sequencialmente a colunas, com base na ordem na qual aparecem na tabela.</span><span class="sxs-lookup"><span data-stu-id="b30b1-113">Note that values in the array are matched sequentially to the columns, based on the order in which they appear in the table.</span></span>  
  
 <span data-ttu-id="b30b1-114">O exemplo a seguir adiciona 10 linhas à tabela **Customers** recém-criada.</span><span class="sxs-lookup"><span data-stu-id="b30b1-114">The following example adds 10 rows to the newly created **Customers** table.</span></span>  
  
```vb  
Dim workRow As DataRow  
Dim i As Integer  
  
For i = 0 To 9  
  workRow = workTable.NewRow()  
  workRow(0) = i  
  workRow(1) = "CustName" & I.ToString()  
  workTable.Rows.Add(workRow)  
Next  
```  
  
```csharp  
DataRow workRow;  
  
for (int i = 0; i <= 9; i++)
{  
  workRow = workTable.NewRow();  
  workRow[0] = i;  
  workRow[1] = "CustName" + i.ToString();  
  workTable.Rows.Add(workRow);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="b30b1-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="b30b1-115">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="b30b1-116">Manipulando dados em uma DataTable</span><span class="sxs-lookup"><span data-stu-id="b30b1-116">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="b30b1-117">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b30b1-117">ADO.NET Overview</span></span>](../ado-net-overview.md)
