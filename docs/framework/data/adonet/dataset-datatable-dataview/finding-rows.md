---
title: Localizar linhas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: ad10557a55b498fe004bff6ce89801e975e7138b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786323"
---
# <a name="finding-rows"></a><span data-ttu-id="29a04-102">Localizar linhas</span><span class="sxs-lookup"><span data-stu-id="29a04-102">Finding Rows</span></span>
<span data-ttu-id="29a04-103">Você pode pesquisar linhas de acordo com seus valores de chave de classificação usando <xref:System.Data.DataView.Find%2A> os <xref:System.Data.DataView.FindRows%2A> métodos e do <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="29a04-103">You can search for rows according to their sort key values by using the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="29a04-104">A diferenciação de maiúsculas e minúsculas dos valores de pesquisa nos métodos **Find** e **FindRows** é determinada pela <xref:System.Data.DataTable>propriedade **CaseSensitive** do subjacente.</span><span class="sxs-lookup"><span data-stu-id="29a04-104">The case sensitivity of search values in the **Find** and **FindRows** methods is determined by the **CaseSensitive** property of the underlying <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="29a04-105">Os valores de pesquisa devem corresponder valores de chave de classificação existentes em sua totalidade para retornar um resultado.</span><span class="sxs-lookup"><span data-stu-id="29a04-105">Search values must match existing sort key values in their entirety in order to return a result.</span></span>  
  
 <span data-ttu-id="29a04-106">O método **Find** retorna um inteiro com o índice do <xref:System.Data.DataRowView> que corresponde aos critérios de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="29a04-106">The **Find** method returns an integer with the index of the <xref:System.Data.DataRowView> that matches the search criteria.</span></span> <span data-ttu-id="29a04-107">Se mais de uma linha corresponder aos critérios de pesquisa, somente o índice do primeiro **DataRowView** correspondente será retornado.</span><span class="sxs-lookup"><span data-stu-id="29a04-107">If more than one row matches the search criteria, only the index of the first matching **DataRowView** is returned.</span></span> <span data-ttu-id="29a04-108">Se nenhuma correspondência for encontrada, **Find** retornará-1.</span><span class="sxs-lookup"><span data-stu-id="29a04-108">If no matches are found, **Find** returns -1.</span></span>  
  
 <span data-ttu-id="29a04-109">Para retornar os resultados da pesquisa que correspondem a várias linhas, use o método **FindRows** .</span><span class="sxs-lookup"><span data-stu-id="29a04-109">To return search results that match multiple rows, use the **FindRows** method.</span></span> <span data-ttu-id="29a04-110">**FindRows** funciona exatamente como o método **Find** , exceto pelo fato de que ele retorna uma matriz **DataRowView** que faz referência a todas as linhas correspondentes no **DataView**.</span><span class="sxs-lookup"><span data-stu-id="29a04-110">**FindRows** works just like the **Find** method, except that it returns a **DataRowView** array that references all matching rows in the **DataView**.</span></span> <span data-ttu-id="29a04-111">Se nenhuma correspondência for encontrada, a matriz **DataRowView** estará vazia.</span><span class="sxs-lookup"><span data-stu-id="29a04-111">If no matches are found, the **DataRowView** array will be empty.</span></span>  
  
 <span data-ttu-id="29a04-112">Para usar os métodos **Find** ou **FindRows** , você deve especificar uma ordem de classificação definindo **ApplyDefaultSort** como **true** ou usando a propriedade **Sort** .</span><span class="sxs-lookup"><span data-stu-id="29a04-112">To use the **Find** or **FindRows** methods you must specify a sort order either by setting **ApplyDefaultSort** to **true** or by using the **Sort** property.</span></span> <span data-ttu-id="29a04-113">Se nenhuma ordem de classificação for especificada, uma exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="29a04-113">If no sort order is specified, an exception is thrown.</span></span>  
  
 <span data-ttu-id="29a04-114">Os métodos **Find** e **FindRows** pegam uma matriz de valores como entrada cujo comprimento corresponde ao número de colunas na ordem de classificação.</span><span class="sxs-lookup"><span data-stu-id="29a04-114">The **Find** and **FindRows** methods take an array of values as input whose length matches the number of columns in the sort order.</span></span> <span data-ttu-id="29a04-115">No caso de uma classificação em uma única coluna, você pode passar um único valor.</span><span class="sxs-lookup"><span data-stu-id="29a04-115">In the case of a sort on a single column, you can pass a single value.</span></span> <span data-ttu-id="29a04-116">Para ordens de classificação que contêm várias colunas, você passa uma matriz de objetos.</span><span class="sxs-lookup"><span data-stu-id="29a04-116">For sort orders containing multiple columns, you pass an array of objects.</span></span> <span data-ttu-id="29a04-117">Observe que, para uma classificação em várias colunas, os valores na matriz de objetos devem corresponder à ordem das colunas especificadas na propriedade **Sort** do **DataView**.</span><span class="sxs-lookup"><span data-stu-id="29a04-117">Note that for a sort on multiple columns, the values in the object array must match the order of the columns specified in the **Sort** property of the **DataView**.</span></span>  
  
 <span data-ttu-id="29a04-118">O exemplo de código a seguir mostra o método **Find** sendo chamado em relação a um **DataView** com uma ordem de classificação de coluna única.</span><span class="sxs-lookup"><span data-stu-id="29a04-118">The following code example shows the **Find** method being called against a **DataView** with a single column sort order.</span></span>  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName", DataViewRowState.CurrentRows)  
  
Dim rowIndex As Integer = custView.Find("The Cracker Box")  
  
If rowIndex = -1 Then  
  Console.WriteLine("No match found.")  
Else  
  Console.WriteLine("{0}, {1}", _  
    custView(rowIndex)("CustomerID").ToString(), _  
    custView(rowIndex)("CompanyName").ToString())  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",   
  "CompanyName", DataViewRowState.CurrentRows);  
  
int rowIndex = custView.Find("The Cracker Box");  
  
if (rowIndex == -1)  
  Console.WriteLine("No match found.");  
else  
  Console.WriteLine("{0}, {1}",  
    custView[rowIndex]["CustomerID"].ToString(),  
    custView[rowIndex]["CompanyName"].ToString());  
```  
  
 <span data-ttu-id="29a04-119">Se sua propriedade de **classificação** especificar várias colunas, você deverá passar uma matriz de objetos com os valores de pesquisa para cada coluna na ordem especificada pela propriedade **Sort** , como no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="29a04-119">If your **Sort** property specifies multiple columns, you must pass an object array with the search values for each column in the order specified by the **Sort** property, as in the following code example.</span></span>  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName, ContactName", _  
  DataViewRowState.CurrentRows)  
  
Dim foundRows() As DataRowView = _  
  custView.FindRows(New object() {"The Cracker Box", "Liu Wong"})  
  
If foundRows.Length = 0 Then  
  Console.WriteLine("No match found.")  
Else  
  Dim myDRV As DataRowView  
  For Each myDRV In foundRows  
    Console.WriteLine("{0}, {1}", _  
      myDRV("CompanyName").ToString(), myDRV("ContactName").ToString())  
  Next  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",  
  "CompanyName, ContactName",  
  DataViewRowState.CurrentRows);  
  
DataRowView[] foundRows =   
  custView.FindRows(new object[] {"The Cracker Box", "Liu Wong"});  
  
if (foundRows.Length == 0)  
  Console.WriteLine("No match found.");  
else  
  foreach (DataRowView myDRV in foundRows)  
    Console.WriteLine("{0}, {1}", myDRV["CompanyName"].ToString(),   
      myDRV["ContactName"].ToString());  
```  
  
## <a name="see-also"></a><span data-ttu-id="29a04-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29a04-120">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="29a04-121">DataViews</span><span class="sxs-lookup"><span data-stu-id="29a04-121">DataViews</span></span>](dataviews.md)
- <span data-ttu-id="29a04-122">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="29a04-122">[ADO.NET Overview](../ado-net-overview.md)</span></span>
