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
# <a name="query-typed-datasets"></a>Conjuntos de valores de consulta digitados

Se o esquema do <xref:System.Data.DataSet> for conhecido em tempo de design do aplicativo, recomendamos que você use um tipo digitado <xref:System.Data.DataSet> ao usar LINQ to DataSet. Um tipo <xref:System.Data.DataSet> é uma classe que deriva de um <xref:System.Data.DataSet>. Como tal, herda todos os métodos, eventos e propriedades de um <xref:System.Data.DataSet>. Além disso, um <xref:System.Data.DataSet> tipo fornece métodos, eventos e propriedades fortemente tipados. Isso significa que você pode acessar tabelas e colunas pelo nome, em vez de usar métodos baseados em coleção. Isso torna as consultas mais simples e mais legíveis. Para obter mais informações, consulte [datasets tipados](./dataset-datatable-dataview/typed-datasets.md).

LINQ to DataSet também dá suporte à consulta em um <xref:System.Data.DataSet>tipo. Com um tipo <xref:System.Data.DataSet>, você não precisa usar o método ou <xref:System.Data.DataRowExtensions.SetField%2A> método <xref:System.Data.DataRowExtensions.Field%2A> genérico para acessar os dados da coluna. Os nomes de propriedade estão disponíveis em tempo de compilação porque as informações de tipo <xref:System.Data.DataSet>estão incluídas no. LINQ to DataSet fornece acesso a valores de coluna como o tipo correto, para que erros de tipo incompatíveis sejam capturados quando o código é compilado em vez de em tempo de execução.

Antes de começar a consultar um tipo <xref:System.Data.DataSet>, você deve gerar a classe usando o **DataSet Designer** no Visual Studio. Para obter mais informações, consulte [criar e configurar conjuntos de](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio)dados.

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

- [Consultando DataSets](querying-datasets-linq-to-dataset.md)
- [Consultas de tabela cruzada](cross-table-queries-linq-to-dataset.md)
- [Consultas de tabela única](single-table-queries-linq-to-dataset.md)
