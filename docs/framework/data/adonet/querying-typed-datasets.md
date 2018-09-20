---
title: Consultando DataSets tipados
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
ms.openlocfilehash: d956fd5f07c108146d20623bcf811266380c132c
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45963738"
---
# <a name="query-typed-datasets"></a>Consultar conjuntos de dados tipados

Se o esquema do <xref:System.Data.DataSet> é conhecido em tempo de design do aplicativo, é recomendável que você use um tipo <xref:System.Data.DataSet> ao usar LINQ to DataSet. Tipado <xref:System.Data.DataSet> é uma classe que deriva de um <xref:System.Data.DataSet>. Como tal, herda todos os métodos, eventos e propriedades de um <xref:System.Data.DataSet>. Além disso, um tipo <xref:System.Data.DataSet> fornece propriedades, eventos e métodos com rigidez de tipos. Isso significa que você pode acessar tabelas e colunas pelo nome, em vez de usar métodos baseados em coleção. Isso torna as consultas mais simples e mais legíveis. Para obter mais informações, consulte [DataSets tipados](../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).

LINQ to DataSet também dá suporte a consultas em um tipo <xref:System.Data.DataSet>. Com um tipado <xref:System.Data.DataSet>, você não precisa usar o genérico <xref:System.Data.DataRowExtensions.Field%2A> método ou <xref:System.Data.DataRowExtensions.SetField%2A> método para acessar os dados de coluna. Nomes de propriedade estão disponíveis em tempo de compilação porque as informações de tipo estão incluídas no <xref:System.Data.DataSet>. LINQ to DataSet fornece acesso aos valores de coluna como o tipo correto, para que os erros de incompatibilidade de tipo são capturados quando o código é compilado em vez de em tempo de execução.

Antes de começar a consultar um tipado <xref:System.Data.DataSet>, você deve gerar a classe usando o **DataSet Designer** no Visual Studio. Para obter mais informações, consulte [criar e configurar conjuntos de dados](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).

## <a name="example"></a>Exemplo

O exemplo a seguir mostra uma consulta sobre um <xref:System.Data.DataSet> tipado:

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

## <a name="see-also"></a>Consulte também

- [Consultando DataSets](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [Consultas de tabela cruzada](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)
- [Consultas de tabela única](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)
