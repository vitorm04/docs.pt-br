---
title: Desempenho de um DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 90820e49-9d46-41f6-9a3d-6c0741bbd8eb
ms.openlocfilehash: f0a85232b753eed891cded4b0fb1154269b30dc9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224037"
---
# <a name="dataview-performance"></a><span data-ttu-id="b3127-102">Desempenho de um DataView</span><span class="sxs-lookup"><span data-stu-id="b3127-102">DataView Performance</span></span>
<span data-ttu-id="b3127-103">Este tópico aborda os benefícios de desempenho de usar <xref:System.Data.DataView.Find%2A> e métodos de <xref:System.Data.DataView.FindRows%2A> de <xref:System.Data.DataView> classe, e para armazenar em cachê <xref:System.Data.DataView> em um aplicativo da Web.</span><span class="sxs-lookup"><span data-stu-id="b3127-103">This topic discusses the performance benefits of using the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView> class, and of caching a <xref:System.Data.DataView> in a Web application.</span></span>  
  
## <a name="find-and-findrows"></a><span data-ttu-id="b3127-104">Localize e FindRows</span><span class="sxs-lookup"><span data-stu-id="b3127-104">Find and FindRows</span></span>  
 <xref:System.Data.DataView> <span data-ttu-id="b3127-105">constrói um índice.</span><span class="sxs-lookup"><span data-stu-id="b3127-105">constructs an index.</span></span> <span data-ttu-id="b3127-106">Um índice contém as chaves criadas de uma ou mais colunas na tabela ou na exibição.</span><span class="sxs-lookup"><span data-stu-id="b3127-106">An index contains keys built from one or more columns in the table or view.</span></span> <span data-ttu-id="b3127-107">Essas chaves são armazenadas em uma estrutura que permite <xref:System.Data.DataView> para encontrar a linha ou linhas associada com os valores da chave rapidamente e com eficiência.</span><span class="sxs-lookup"><span data-stu-id="b3127-107">These keys are stored in a structure that enables the <xref:System.Data.DataView> to find the row or rows associated with the key values quickly and efficiently.</span></span> <span data-ttu-id="b3127-108">Operações que usam o índice, como filtragem e classificação, consulte aumentos significativos de desempenho.</span><span class="sxs-lookup"><span data-stu-id="b3127-108">Operations that use the index, such as filtering and sorting, see significant performance increases.</span></span> <span data-ttu-id="b3127-109">O índice de um <xref:System.Data.DataView> é compilado quando <xref:System.Data.DataView> é criado e quando qualquer informação de classificação ou de filtragem é modificada.</span><span class="sxs-lookup"><span data-stu-id="b3127-109">The index for a <xref:System.Data.DataView> is built both when the <xref:System.Data.DataView> is created and when any of the sorting or filtering information is modified.</span></span> <span data-ttu-id="b3127-110">Criar <xref:System.Data.DataView> e então defina a classificação ou informações de filtragem causam posteriormente o índice a ser compilado pelo menos duas vezes: uma vez que quando <xref:System.Data.DataView> é criado, e novamente quando algumas de tipo ou propriedades de filtragem são alteradas.</span><span class="sxs-lookup"><span data-stu-id="b3127-110">Creating a <xref:System.Data.DataView> and then setting the sorting or filtering information later causes the index to be built at least twice: once when the <xref:System.Data.DataView> is created, and again when any of the sort or filter properties are modified.</span></span> <span data-ttu-id="b3127-111">Para obter mais informações sobre filtragem e classificação com <xref:System.Data.DataView>, consulte [filtrando com DataView](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md) e [classificando com DataView](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="b3127-111">For more information about filtering and sorting with <xref:System.Data.DataView>, see [Filtering with DataView](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md) and [Sorting with DataView](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md).</span></span>  
  
 <span data-ttu-id="b3127-112">Se você quiser retornar os resultados de uma consulta específica nos dados, ao contrário de fornecer uma exibição dinâmica de um subconjunto dos dados, você poderá usar os métodos <xref:System.Data.DataView.Find%2A> ou <xref:System.Data.DataView.FindRows%2A> de <xref:System.Data.DataView>, em vez de definir a propriedade <xref:System.Data.DataView.RowFilter%2A>.</span><span class="sxs-lookup"><span data-stu-id="b3127-112">If you want to return the results of a particular query on the data, as opposed to providing a dynamic view of a subset of the data, you can use the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>, rather than setting the <xref:System.Data.DataView.RowFilter%2A> property.</span></span> <span data-ttu-id="b3127-113">A propriedade <xref:System.Data.DataView.RowFilter%2A> é melhor usada em um aplicativo associado a dados onde um controle de associação exibe resultados filtrados.</span><span class="sxs-lookup"><span data-stu-id="b3127-113">The <xref:System.Data.DataView.RowFilter%2A> property is best used in a data-bound application where a bound control displays filtered results.</span></span> <span data-ttu-id="b3127-114">Definir a propriedade <xref:System.Data.DataView.RowFilter%2A> reconstrói o índice para os dados, adicionando a sobrecarga ao seu aplicativo e diminuindo o desempenho.</span><span class="sxs-lookup"><span data-stu-id="b3127-114">Setting the <xref:System.Data.DataView.RowFilter%2A> property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="b3127-115">Os métodos <xref:System.Data.DataView.Find%2A> e <xref:System.Data.DataView.FindRows%2A> usam o índice atual sem exigir que o índice seja reconstruído.</span><span class="sxs-lookup"><span data-stu-id="b3127-115">The <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods use the current index without requiring the index to be rebuilt.</span></span> <span data-ttu-id="b3127-116">Se você chamar <xref:System.Data.DataView.Find%2A> ou <xref:System.Data.DataView.FindRows%2A> apenas uma vez, deverá usar o <xref:System.Data.DataView> existente.</span><span class="sxs-lookup"><span data-stu-id="b3127-116">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> only once, then you should use the existing <xref:System.Data.DataView>.</span></span> <span data-ttu-id="b3127-117">Se você chamar <xref:System.Data.DataView.Find%2A> ou <xref:System.Data.DataView.FindRows%2A> várias vezes, deverá criar um novo <xref:System.Data.DataView> para recriar o índice na coluna em que você deseja pesquisar e, em seguida, chamar os métodos <xref:System.Data.DataView.Find%2A> ou <xref:System.Data.DataView.FindRows%2A>.</span><span class="sxs-lookup"><span data-stu-id="b3127-117">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> multiple times, you should create a new <xref:System.Data.DataView> to rebuild the index on the column you want to search on, and then call the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods.</span></span> <span data-ttu-id="b3127-118">Para obter mais informações sobre o <xref:System.Data.DataView.Find%2A> e <xref:System.Data.DataView.FindRows%2A> métodos, consulte [localizando linhas](../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).</span><span class="sxs-lookup"><span data-stu-id="b3127-118">For more information about the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods, see [Finding Rows](../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).</span></span>  
  
 <span data-ttu-id="b3127-119">O exemplo a seguir usa o método de <xref:System.Data.DataView.Find%2A> para localizar um contato com o sobrenome “Zhu”.</span><span class="sxs-lookup"><span data-stu-id="b3127-119">The following example uses the <xref:System.Data.DataView.Find%2A> method to find a contact with the last name "Zhu".</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryorderbyfind)]
 [!code-vb[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryorderbyfind)]  
  
 <span data-ttu-id="b3127-120">O exemplo a seguir usa o método de <xref:System.Data.DataView.FindRows%2A> para localizar todos os produtos colorido vermelho.</span><span class="sxs-lookup"><span data-stu-id="b3127-120">The following example uses the <xref:System.Data.DataView.FindRows%2A> method to find all the red colored products.</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryfindrows)]
 [!code-vb[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryfindrows)]  
  
## <a name="aspnet"></a><span data-ttu-id="b3127-121">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b3127-121">ASP.NET</span></span>  
 <span data-ttu-id="b3127-122">O ASP.NET tem um mecanismo de cachê que permite que você armazene os objetos que exigem recursos abrangentes de servidor criar na memória.</span><span class="sxs-lookup"><span data-stu-id="b3127-122">ASP.NET has a caching mechanism that allows you to store objects that require extensive server resources to create in memory.</span></span> <span data-ttu-id="b3127-123">Armazenar em cachê esses tipos de recursos pode melhorar significativamente o desempenho do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b3127-123">Caching these types of resources can significantly improve the performance of your application.</span></span> <span data-ttu-id="b3127-124">Caching é implementado pela classe de <xref:System.Web.Caching.Cache> , com instâncias de cache que são particulares para cada aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b3127-124">Caching is implemented by the <xref:System.Web.Caching.Cache> class, with cache instances that are private to each application.</span></span> <span data-ttu-id="b3127-125">Como criar um novo objeto de <xref:System.Data.DataView> pode ser recurso intensivo, você pode querer usar essa funcionalidade de cachê em aplicativos da Web para que <xref:System.Data.DataView> não tem que ser reconstruído todas as vezes na página da Web é atualizado.</span><span class="sxs-lookup"><span data-stu-id="b3127-125">Because creating a new <xref:System.Data.DataView> object can be resource intensive, you might want to use this caching functionality in Web applications so that the <xref:System.Data.DataView> does not have to be rebuilt every time the Web page is refreshed.</span></span>  
  
 <span data-ttu-id="b3127-126">No exemplo a seguir, <xref:System.Data.DataView> é armazenado em cachê de modo que os dados não precisem ser recorridos quando a página é atualizada.</span><span class="sxs-lookup"><span data-stu-id="b3127-126">In the following example, the <xref:System.Data.DataView> is cached so that the data does not have to be re-sorted when the page is refreshed.</span></span>  
  
```vb  
If (Cache("ordersView") = Nothing) Then  
  
Dim dataSet As New DataSet()  
  
   FillDataSet(dataSet)  
  
   Dim orders As DataTable = dataSet.Tables("SalesOrderHeader")  
  
   Dim query = _  
                    From order In orders.AsEnumerable() _  
                    Where order.Field(Of Boolean)("OnlineOrderFlag") = True _  
                    Order By order.Field(Of Decimal)("TotalDue") _  
                    Select order  
  
   Dim view As DataView = query.AsDataView()  
  
   Cache.Insert("ordersView", view)  
  
End If  
  
Dim ordersView = CType(Cache("ordersView"), DataView)  
  
GridView1.DataSource = ordersView  
GridView1.DataBind()  
```  
  
```csharp  
if (Cache["ordersView"] == null)  
{  
   // Fill the DataSet.                  
   DataSet dataSet = FillDataSet();  
  
   DataTable orders = dataSet.Tables["SalesOrderHeader"];  
  
   EnumerableRowCollection<DataRow> query =  
                        from order in orders.AsEnumerable()  
                        where order.Field<bool>("OnlineOrderFlag") == true  
                        orderby order.Field<decimal>("TotalDue")  
                        select order;  
  
   DataView view = query.AsDataView();  
   Cache.Insert("ordersView", view);  
}  
  
DataView ordersView = (DataView)Cache["ordersView"];  
  
GridView1.DataSource = ordersView;  
GridView1.DataBind();  
```  
  
## <a name="see-also"></a><span data-ttu-id="b3127-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b3127-127">See also</span></span>

- [<span data-ttu-id="b3127-128">Associação e LINQ to DataSet de dados</span><span class="sxs-lookup"><span data-stu-id="b3127-128">Data Binding and LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
