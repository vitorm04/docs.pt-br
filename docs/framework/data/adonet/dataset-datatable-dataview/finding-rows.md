---
title: Localizando linhas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: 57ed6045ca0ea9f9579640839e8198716cf79fe0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760876"
---
# <a name="finding-rows"></a><span data-ttu-id="2eae8-102">Localizando linhas</span><span class="sxs-lookup"><span data-stu-id="2eae8-102">Finding Rows</span></span>
<span data-ttu-id="2eae8-103">Você pode procurar linhas de acordo com seus valores de chave de classificação usando o <xref:System.Data.DataView.Find%2A> e <xref:System.Data.DataView.FindRows%2A> métodos do <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="2eae8-103">You can search for rows according to their sort key values by using the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="2eae8-104">A diferenciação de maiusculas e minúsculas da pesquisa de valores no **localizar** e **FindRows** métodos é determinado pelo **CaseSensitive** propriedade subjacente <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="2eae8-104">The case sensitivity of search values in the **Find** and **FindRows** methods is determined by the **CaseSensitive** property of the underlying <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="2eae8-105">Valores de pesquisa devem corresponder a valores de chave de classificação existentes em sua totalidade para retornar um resultado.</span><span class="sxs-lookup"><span data-stu-id="2eae8-105">Search values must match existing sort key values in their entirety in order to return a result.</span></span>  
  
 <span data-ttu-id="2eae8-106">O **localizar** método retorna um inteiro com o índice da <xref:System.Data.DataRowView> que corresponde aos critérios de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="2eae8-106">The **Find** method returns an integer with the index of the <xref:System.Data.DataRowView> that matches the search criteria.</span></span> <span data-ttu-id="2eae8-107">Se mais de uma linha corresponde aos critérios de pesquisa, apenas o índice da primeira correspondência **DataRowView** é retornado.</span><span class="sxs-lookup"><span data-stu-id="2eae8-107">If more than one row matches the search criteria, only the index of the first matching **DataRowView** is returned.</span></span> <span data-ttu-id="2eae8-108">Se nenhuma correspondência for encontrada, **localizar** retornará -1.</span><span class="sxs-lookup"><span data-stu-id="2eae8-108">If no matches are found, **Find** returns -1.</span></span>  
  
 <span data-ttu-id="2eae8-109">Para retornar os resultados de pesquisa que correspondam a várias linhas, use o **FindRows** método.</span><span class="sxs-lookup"><span data-stu-id="2eae8-109">To return search results that match multiple rows, use the **FindRows** method.</span></span> <span data-ttu-id="2eae8-110">**FindRows** funciona como o **localizar** método, exceto que ela retorna um **DataRowView** matriz que faz referência a todas as linhas correspondentes no **DataView**.</span><span class="sxs-lookup"><span data-stu-id="2eae8-110">**FindRows** works just like the **Find** method, except that it returns a **DataRowView** array that references all matching rows in the **DataView**.</span></span> <span data-ttu-id="2eae8-111">Se nenhuma correspondência for encontrada, o **DataRowView** matriz estará vazia.</span><span class="sxs-lookup"><span data-stu-id="2eae8-111">If no matches are found, the **DataRowView** array will be empty.</span></span>  
  
 <span data-ttu-id="2eae8-112">Para usar o **localizar** ou **FindRows** métodos que você deve especificar uma classificação ordem definindo **ApplyDefaultSort** para **true** ou usando o **Classificação** propriedade.</span><span class="sxs-lookup"><span data-stu-id="2eae8-112">To use the **Find** or **FindRows** methods you must specify a sort order either by setting **ApplyDefaultSort** to **true** or by using the **Sort** property.</span></span> <span data-ttu-id="2eae8-113">Se nenhuma ordem de classificação for especificado, uma exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="2eae8-113">If no sort order is specified, an exception is thrown.</span></span>  
  
 <span data-ttu-id="2eae8-114">O **localizar** e **FindRows** métodos aceitam uma matriz de valores como entrada cujo tamanho corresponde ao número de colunas na ordem de classificação.</span><span class="sxs-lookup"><span data-stu-id="2eae8-114">The **Find** and **FindRows** methods take an array of values as input whose length matches the number of columns in the sort order.</span></span> <span data-ttu-id="2eae8-115">No caso de uma classificação em uma única coluna, você pode passar um único valor.</span><span class="sxs-lookup"><span data-stu-id="2eae8-115">In the case of a sort on a single column, you can pass a single value.</span></span> <span data-ttu-id="2eae8-116">Para ordens de classificação que contém várias colunas, você passar uma matriz de objetos.</span><span class="sxs-lookup"><span data-stu-id="2eae8-116">For sort orders containing multiple columns, you pass an array of objects.</span></span> <span data-ttu-id="2eae8-117">Observe que, para uma classificação em várias colunas, os valores na matriz de objetos devem corresponder à ordem das colunas especificadas no **classificação** propriedade o **DataView**.</span><span class="sxs-lookup"><span data-stu-id="2eae8-117">Note that for a sort on multiple columns, the values in the object array must match the order of the columns specified in the **Sort** property of the **DataView**.</span></span>  
  
 <span data-ttu-id="2eae8-118">O seguinte exemplo de código mostra o **localizar** método ser chamado em um **DataView** com uma ordem de classificação de coluna única.</span><span class="sxs-lookup"><span data-stu-id="2eae8-118">The following code example shows the **Find** method being called against a **DataView** with a single column sort order.</span></span>  
  
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
  
 <span data-ttu-id="2eae8-119">Se seu **classificação** propriedade especifica várias colunas, você deve passar uma matriz de objetos com os valores de pesquisa para cada coluna na ordem especificada pelo **classificação** propriedade, como no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="2eae8-119">If your **Sort** property specifies multiple columns, you must pass an object array with the search values for each column in the order specified by the **Sort** property, as in the following code example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2eae8-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2eae8-120">See Also</span></span>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [<span data-ttu-id="2eae8-121">DataViews</span><span class="sxs-lookup"><span data-stu-id="2eae8-121">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 <span data-ttu-id="2eae8-122">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="2eae8-122">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
