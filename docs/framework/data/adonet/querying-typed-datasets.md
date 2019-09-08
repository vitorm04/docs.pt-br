---
title: Consultando DataSets tipados
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
ms.openlocfilehash: 55714c4dae73cd17a849cc35681797dfa4266e3b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782971"
---
# <a name="query-typed-datasets"></a><span data-ttu-id="6e47c-102">Conjuntos de valores de consulta digitados</span><span class="sxs-lookup"><span data-stu-id="6e47c-102">Query typed DataSets</span></span>

<span data-ttu-id="6e47c-103">Se o esquema do <xref:System.Data.DataSet> for conhecido em tempo de design do aplicativo, recomendamos que você use um tipo digitado <xref:System.Data.DataSet> ao usar LINQ to DataSet.</span><span class="sxs-lookup"><span data-stu-id="6e47c-103">If the schema of the <xref:System.Data.DataSet> is known at application design time, we recommend that you use a typed <xref:System.Data.DataSet> when using LINQ to DataSet.</span></span> <span data-ttu-id="6e47c-104">Um tipo <xref:System.Data.DataSet> é uma classe que deriva de um <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="6e47c-104">A typed <xref:System.Data.DataSet> is a class that derives from a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="6e47c-105">Como tal, herda todos os métodos, eventos e propriedades de um <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="6e47c-105">As such, it inherits all the methods, events, and properties of a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="6e47c-106">Além disso, um <xref:System.Data.DataSet> tipo fornece métodos, eventos e propriedades fortemente tipados.</span><span class="sxs-lookup"><span data-stu-id="6e47c-106">Additionally, a typed <xref:System.Data.DataSet> provides strongly typed methods, events, and properties.</span></span> <span data-ttu-id="6e47c-107">Isso significa que você pode acessar tabelas e colunas pelo nome, em vez de usar métodos baseados em coleção.</span><span class="sxs-lookup"><span data-stu-id="6e47c-107">This means that you can access tables and columns by name, instead of using collection-based methods.</span></span> <span data-ttu-id="6e47c-108">Isso torna as consultas mais simples e mais legíveis.</span><span class="sxs-lookup"><span data-stu-id="6e47c-108">This makes queries simpler and more readable.</span></span> <span data-ttu-id="6e47c-109">Para obter mais informações, consulte [datasets tipados](./dataset-datatable-dataview/typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="6e47c-109">For more information, see [Typed DataSets](./dataset-datatable-dataview/typed-datasets.md).</span></span>

<span data-ttu-id="6e47c-110">LINQ to DataSet também dá suporte à consulta em um <xref:System.Data.DataSet>tipo.</span><span class="sxs-lookup"><span data-stu-id="6e47c-110">LINQ to DataSet also supports querying over a typed <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="6e47c-111">Com um tipo <xref:System.Data.DataSet>, você não precisa usar o método ou <xref:System.Data.DataRowExtensions.SetField%2A> método <xref:System.Data.DataRowExtensions.Field%2A> genérico para acessar os dados da coluna.</span><span class="sxs-lookup"><span data-stu-id="6e47c-111">With a typed <xref:System.Data.DataSet>, you do not have to use the generic <xref:System.Data.DataRowExtensions.Field%2A> method or <xref:System.Data.DataRowExtensions.SetField%2A> method to access column data.</span></span> <span data-ttu-id="6e47c-112">Os nomes de propriedade estão disponíveis em tempo de compilação porque as informações de tipo <xref:System.Data.DataSet>estão incluídas no.</span><span class="sxs-lookup"><span data-stu-id="6e47c-112">Property names are available at compile time because the type information is included in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="6e47c-113">LINQ to DataSet fornece acesso a valores de coluna como o tipo correto, para que erros de tipo incompatíveis sejam capturados quando o código é compilado em vez de em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6e47c-113">LINQ to DataSet provides access to column values as the correct type, so that type mismatch errors are caught when the code is compiled instead of at run time.</span></span>

<span data-ttu-id="6e47c-114">Antes de começar a consultar um tipo <xref:System.Data.DataSet>, você deve gerar a classe usando o **DataSet Designer** no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6e47c-114">Before you can begin querying a typed <xref:System.Data.DataSet>, you must generate the class by using the **DataSet Designer** in Visual Studio.</span></span> <span data-ttu-id="6e47c-115">Para obter mais informações, consulte [criar e configurar conjuntos de](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio)dados.</span><span class="sxs-lookup"><span data-stu-id="6e47c-115">For more information, see [Create and configure DataSets](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).</span></span>

## <a name="example"></a><span data-ttu-id="6e47c-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6e47c-116">Example</span></span>

<span data-ttu-id="6e47c-117">O exemplo a seguir mostra uma consulta sobre um <xref:System.Data.DataSet> tipado:</span><span class="sxs-lookup"><span data-stu-id="6e47c-117">The following example shows a query over a typed <xref:System.Data.DataSet>:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6e47c-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6e47c-118">See also</span></span>

- [<span data-ttu-id="6e47c-119">Consultando DataSets</span><span class="sxs-lookup"><span data-stu-id="6e47c-119">Querying DataSets</span></span>](querying-datasets-linq-to-dataset.md)
- [<span data-ttu-id="6e47c-120">Consultas de tabela cruzada</span><span class="sxs-lookup"><span data-stu-id="6e47c-120">Cross-Table Queries</span></span>](cross-table-queries-linq-to-dataset.md)
- [<span data-ttu-id="6e47c-121">Consultas de tabela única</span><span class="sxs-lookup"><span data-stu-id="6e47c-121">Single-Table Queries</span></span>](single-table-queries-linq-to-dataset.md)
