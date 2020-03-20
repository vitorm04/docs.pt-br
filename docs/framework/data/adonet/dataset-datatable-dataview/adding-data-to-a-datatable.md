---
title: Adicionando dados a um DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d6aa8474-7bde-48f7-949d-20dc38a1625b
ms.openlocfilehash: 02d7f94259cc56513be404c5539ca7015d5f3533
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151527"
---
# <a name="adding-data-to-a-datatable"></a><span data-ttu-id="8e1ae-102">Adicionando dados a um DataTable</span><span class="sxs-lookup"><span data-stu-id="8e1ae-102">Adding Data to a DataTable</span></span>
<span data-ttu-id="8e1ae-103">Depois de criar <xref:System.Data.DataTable> e definir sua estrutura usando colunas e restrições, você pode adicionar novas linhas de dados à tabela.</span><span class="sxs-lookup"><span data-stu-id="8e1ae-103">After you create a <xref:System.Data.DataTable> and define its structure using columns and constraints, you can add new rows of data to the table.</span></span> <span data-ttu-id="8e1ae-104">Para adicionar uma nova linha, declare uma nova variável como tipo <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="8e1ae-104">To add a new row, declare a new variable as type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="8e1ae-105">Um novo objeto **DataRow** é retornado quando você chama o <xref:System.Data.DataTable.NewRow%2A> método.</span><span class="sxs-lookup"><span data-stu-id="8e1ae-105">A new **DataRow** object is returned when you call the <xref:System.Data.DataTable.NewRow%2A> method.</span></span> <span data-ttu-id="8e1ae-106">A **Tabela de Dados** cria então o objeto **DataRow** com <xref:System.Data.DataColumnCollection>base na estrutura da tabela, conforme definido pelo .</span><span class="sxs-lookup"><span data-stu-id="8e1ae-106">The **DataTable** then creates the **DataRow** object based on the structure of the table, as defined by the <xref:System.Data.DataColumnCollection>.</span></span>  
  
 <span data-ttu-id="8e1ae-107">O exemplo a seguir demonstra como criar uma nova linha chamando o método **NewRow.**</span><span class="sxs-lookup"><span data-stu-id="8e1ae-107">The following example demonstrates how to create a new row by calling the **NewRow** method.</span></span>  
  
```vb  
Dim workRow As DataRow = workTable.NewRow()  
```  
  
```csharp  
DataRow workRow = workTable.NewRow();  
```  
  
 <span data-ttu-id="8e1ae-108">Você pode manipular a linha recém-adicionada usando um índice ou o nome da coluna, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="8e1ae-108">You then can manipulate the newly added row using an index or the column name, as shown in the following example.</span></span>  
  
```vb  
workRow("CustLName") = "Smith"  
workRow(1) = "Smith"  
```  
  
```csharp  
workRow["CustLName"] = "Smith";  
workRow[1] = "Smith";  
```  
  
 <span data-ttu-id="8e1ae-109">Depois que os dados são inseridos na nova linha, o <xref:System.Data.DataRowCollection>método **Adicionar** é usado para adicionar a linha ao , mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="8e1ae-109">After data is inserted into the new row, the **Add** method is used to add the row to the <xref:System.Data.DataRowCollection>, shown in the following code.</span></span>  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 <span data-ttu-id="8e1ae-110">Você também pode chamar o método **Adicionar** para adicionar uma nova linha, passando em uma matriz de valores, digitada como <xref:System.Object>, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="8e1ae-110">You can also call the **Add** method to add a new row by passing in an array of values, typed as <xref:System.Object>, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 <span data-ttu-id="8e1ae-111">Passar uma matriz de valores, digitada como **Objeto,** para o método **Adicionar** cria uma nova linha dentro da tabela e define seus valores de coluna para os valores na matriz de objetos.</span><span class="sxs-lookup"><span data-stu-id="8e1ae-111">Passing an array of values, typed as **Object**, to the **Add** method creates a new row inside the table and sets its column values to the values in the object array.</span></span> <span data-ttu-id="8e1ae-112">Observe que os valores na matriz são correspondidos sequencialmente a colunas, com base na ordem na qual aparecem na tabela.</span><span class="sxs-lookup"><span data-stu-id="8e1ae-112">Note that values in the array are matched sequentially to the columns, based on the order in which they appear in the table.</span></span>  
  
 <span data-ttu-id="8e1ae-113">O exemplo a seguir adiciona 10 linhas à tabela **Clientes** recém-criada.</span><span class="sxs-lookup"><span data-stu-id="8e1ae-113">The following example adds 10 rows to the newly created **Customers** table.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8e1ae-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="8e1ae-114">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="8e1ae-115">Manipulando dados em uma DataTable</span><span class="sxs-lookup"><span data-stu-id="8e1ae-115">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="8e1ae-116">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8e1ae-116">ADO.NET Overview</span></span>](../ado-net-overview.md)
