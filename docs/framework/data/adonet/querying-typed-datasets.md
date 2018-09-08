---
title: Consultando DataSets tipados
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
ms.openlocfilehash: d956fd5f07c108146d20623bcf811266380c132c
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44200939"
---
# <a name="query-typed-datasets"></a><span data-ttu-id="14a24-102">Consultar conjuntos de dados tipados</span><span class="sxs-lookup"><span data-stu-id="14a24-102">Query typed DataSets</span></span>

<span data-ttu-id="14a24-103">Se o esquema do <xref:System.Data.DataSet> é conhecido em tempo de design do aplicativo, é recomendável que você use um tipo <xref:System.Data.DataSet> ao usar LINQ to DataSet.</span><span class="sxs-lookup"><span data-stu-id="14a24-103">If the schema of the <xref:System.Data.DataSet> is known at application design time, we recommend that you use a typed <xref:System.Data.DataSet> when using LINQ to DataSet.</span></span> <span data-ttu-id="14a24-104">Tipado <xref:System.Data.DataSet> é uma classe que deriva de um <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="14a24-104">A typed <xref:System.Data.DataSet> is a class that derives from a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="14a24-105">Como tal, herda todos os métodos, eventos e propriedades de um <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="14a24-105">As such, it inherits all the methods, events, and properties of a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="14a24-106">Além disso, um tipo <xref:System.Data.DataSet> fornece propriedades, eventos e métodos com rigidez de tipos.</span><span class="sxs-lookup"><span data-stu-id="14a24-106">Additionally, a typed <xref:System.Data.DataSet> provides strongly typed methods, events, and properties.</span></span> <span data-ttu-id="14a24-107">Isso significa que você pode acessar tabelas e colunas pelo nome, em vez de usar métodos baseados em coleção.</span><span class="sxs-lookup"><span data-stu-id="14a24-107">This means that you can access tables and columns by name, instead of using collection-based methods.</span></span> <span data-ttu-id="14a24-108">Isso torna as consultas mais simples e mais legíveis.</span><span class="sxs-lookup"><span data-stu-id="14a24-108">This makes queries simpler and more readable.</span></span> <span data-ttu-id="14a24-109">Para obter mais informações, consulte [DataSets tipados](../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="14a24-109">For more information, see [Typed DataSets](../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span></span>

<span data-ttu-id="14a24-110">LINQ to DataSet também dá suporte a consultas em um tipo <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="14a24-110">LINQ to DataSet also supports querying over a typed <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="14a24-111">Com um tipado <xref:System.Data.DataSet>, você não precisa usar o genérico <xref:System.Data.DataRowExtensions.Field%2A> método ou <xref:System.Data.DataRowExtensions.SetField%2A> método para acessar os dados de coluna.</span><span class="sxs-lookup"><span data-stu-id="14a24-111">With a typed <xref:System.Data.DataSet>, you do not have to use the generic <xref:System.Data.DataRowExtensions.Field%2A> method or <xref:System.Data.DataRowExtensions.SetField%2A> method to access column data.</span></span> <span data-ttu-id="14a24-112">Nomes de propriedade estão disponíveis em tempo de compilação porque as informações de tipo estão incluídas no <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="14a24-112">Property names are available at compile time because the type information is included in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="14a24-113">LINQ to DataSet fornece acesso aos valores de coluna como o tipo correto, para que os erros de incompatibilidade de tipo são capturados quando o código é compilado em vez de em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="14a24-113">LINQ to DataSet provides access to column values as the correct type, so that type mismatch errors are caught when the code is compiled instead of at run time.</span></span>

<span data-ttu-id="14a24-114">Antes de começar a consultar um tipado <xref:System.Data.DataSet>, você deve gerar a classe usando o **DataSet Designer** no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="14a24-114">Before you can begin querying a typed <xref:System.Data.DataSet>, you must generate the class by using the **DataSet Designer** in Visual Studio.</span></span> <span data-ttu-id="14a24-115">Para obter mais informações, consulte [criar e configurar conjuntos de dados](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="14a24-115">For more information, see [Create and configure DataSets](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).</span></span>

## <a name="example"></a><span data-ttu-id="14a24-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="14a24-116">Example</span></span>

<span data-ttu-id="14a24-117">O exemplo a seguir mostra uma consulta sobre um <xref:System.Data.DataSet> tipado:</span><span class="sxs-lookup"><span data-stu-id="14a24-117">The following example shows a query over a typed <xref:System.Data.DataSet>:</span></span>

```csharp
var query = from o in orders
            where o.OnlineOrderFlag == true
            select new { o.SalesOrderID,
                         o.OrderDate,
                         o.SalesOrderNumber };

foreach(var order in query)
{
    Console.WriteLine("{0}\t{1:d}\t{2}",
      order.SalesOrderID,
      order.OrderDate,
      order.SalesOrderNumber);
}
```

```vb
Dim orders = ds.Tables("SalesOrderHeader")

Dim query = _
       From o In orders _
       Where o.OnlineOrderFlag = True _
       Select New {SalesOrderID := o.SalesOrderID, _
                   OrderDate := o.OrderDate, _
                   SalesOrderNumber := o.SalesOrderNumber}

For Each Dim onlineOrder In query
 Console.WriteLine("{0}\t{1:d}\t{2}", _
 onlineOrder.SalesOrderID, _
 onlineOrder.OrderDate, _
 onlineOrder.SalesOrderNumber)
Next
```

## <a name="see-also"></a><span data-ttu-id="14a24-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="14a24-118">See also</span></span>

- [<span data-ttu-id="14a24-119">Consultando DataSets</span><span class="sxs-lookup"><span data-stu-id="14a24-119">Querying DataSets</span></span>](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [<span data-ttu-id="14a24-120">Consultas de tabela cruzada</span><span class="sxs-lookup"><span data-stu-id="14a24-120">Cross-Table Queries</span></span>](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)
- [<span data-ttu-id="14a24-121">Consultas de tabela única</span><span class="sxs-lookup"><span data-stu-id="14a24-121">Single-Table Queries</span></span>](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)
