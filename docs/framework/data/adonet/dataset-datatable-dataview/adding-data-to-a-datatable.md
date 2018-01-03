---
title: Adicionando dados a um DataTable
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d6aa8474-7bde-48f7-949d-20dc38a1625b
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 91aa84b0a3d381512faf74f350dc4b43e9a3c598
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="adding-data-to-a-datatable"></a><span data-ttu-id="8ea3b-102">Adicionando dados a um DataTable</span><span class="sxs-lookup"><span data-stu-id="8ea3b-102">Adding Data to a DataTable</span></span>
<span data-ttu-id="8ea3b-103">Depois de criar <xref:System.Data.DataTable> e definir sua estrutura usando colunas e restrições, você pode adicionar novas linhas de dados à tabela.</span><span class="sxs-lookup"><span data-stu-id="8ea3b-103">After you create a <xref:System.Data.DataTable> and define its structure using columns and constraints, you can add new rows of data to the table.</span></span> <span data-ttu-id="8ea3b-104">Para adicionar uma nova linha, declare uma nova variável como tipo <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="8ea3b-104">To add a new row, declare a new variable as type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="8ea3b-105">Um novo **DataRow** objeto é retornado ao chamar o <xref:System.Data.DataTable.NewRow%2A> método.</span><span class="sxs-lookup"><span data-stu-id="8ea3b-105">A new **DataRow** object is returned when you call the <xref:System.Data.DataTable.NewRow%2A> method.</span></span> <span data-ttu-id="8ea3b-106">O **DataTable** , em seguida, cria o **DataRow** objeto com base na estrutura da tabela, conforme definido pelo <xref:System.Data.DataColumnCollection>.</span><span class="sxs-lookup"><span data-stu-id="8ea3b-106">The **DataTable** then creates the **DataRow** object based on the structure of the table, as defined by the <xref:System.Data.DataColumnCollection>.</span></span>  
  
 <span data-ttu-id="8ea3b-107">O exemplo a seguir demonstra como criar uma nova linha chamando o **NewRow** método.</span><span class="sxs-lookup"><span data-stu-id="8ea3b-107">The following example demonstrates how to create a new row by calling the **NewRow** method.</span></span>  
  
```vb  
Dim workRow As DataRow = workTable.NewRow()  
```  
  
```csharp  
DataRow workRow = workTable.NewRow();  
```  
  
 <span data-ttu-id="8ea3b-108">Você pode manipular a linha recém-adicionada usando um índice ou o nome da coluna, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="8ea3b-108">You then can manipulate the newly added row using an index or the column name, as shown in the following example.</span></span>  
  
```vb  
workRow("CustLName") = "Smith"  
workRow(1) = "Smith"  
```  
  
```csharp  
workRow["CustLName"] = "Smith";  
workRow[1] = "Smith";  
```  
  
 <span data-ttu-id="8ea3b-109">Depois que dados são inseridos em nova linha, o **adicionar** método é usado para adicionar a linha para o <xref:System.Data.DataRowCollection>, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="8ea3b-109">After data is inserted into the new row, the **Add** method is used to add the row to the <xref:System.Data.DataRowCollection>, shown in the following code.</span></span>  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 <span data-ttu-id="8ea3b-110">Você também pode chamar o **adicionar** tipado para adicionar uma nova linha, passando uma matriz de valores, como <xref:System.Object>, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="8ea3b-110">You can also call the **Add** method to add a new row by passing in an array of values, typed as <xref:System.Object>, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 <span data-ttu-id="8ea3b-111">Passando uma matriz de valores, digitado como **objeto**, para o **adicionar** método cria uma nova linha dentro da tabela e define seus valores de coluna com os valores na matriz de objetos.</span><span class="sxs-lookup"><span data-stu-id="8ea3b-111">Passing an array of values, typed as **Object**, to the **Add** method creates a new row inside the table and sets its column values to the values in the object array.</span></span> <span data-ttu-id="8ea3b-112">Observe que os valores na matriz são correspondidos sequencialmente a colunas, com base na ordem na qual aparecem na tabela.</span><span class="sxs-lookup"><span data-stu-id="8ea3b-112">Note that values in the array are matched sequentially to the columns, based on the order in which they appear in the table.</span></span>  
  
 <span data-ttu-id="8ea3b-113">O exemplo a seguir adiciona 10 linhas para recém-criado **clientes** tabela.</span><span class="sxs-lookup"><span data-stu-id="8ea3b-113">The following example adds 10 rows to the newly created **Customers** table.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8ea3b-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ea3b-114">See Also</span></span>  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataRowCollection>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="8ea3b-115">Manipulação de dados em uma DataTable</span><span class="sxs-lookup"><span data-stu-id="8ea3b-115">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 <span data-ttu-id="8ea3b-116">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="8ea3b-116">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
