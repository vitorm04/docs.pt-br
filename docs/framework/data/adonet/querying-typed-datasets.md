---
title: Consultando DataSets tipados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
ms.openlocfilehash: 30a6512202615590a4b399b8ce7173b213a8873c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="querying-typed-datasets"></a>Consultando DataSets tipados
Se o esquema do <xref:System.Data.DataSet> for conhecido no tempo de design do aplicativo, recomendamos usar um <xref:System.Data.DataSet> tipado ao usar o [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. Um tipo <xref:System.Data.DataSet> é uma classe que deriva de um <xref:System.Data.DataSet>. Como tal, herda todos os métodos, eventos e propriedades de um <xref:System.Data.DataSet>. Além disso, um tipo <xref:System.Data.DataSet> fornece métodos com rigidez de tipos, propriedades e eventos. Isso significa que você pode acessar tabelas e colunas pelo nome, em vez de usar métodos baseados em coleção. Isso torna as consultas mais simples e mais legíveis. Para obter mais informações, consulte [DataSets tipados](../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] também oferece suporte a consultas em um tipo <xref:System.Data.DataSet>. Com um tipo <xref:System.Data.DataSet>, você não precisa usar o genérico <xref:System.Data.DataRowExtensions.Field%2A> método ou <xref:System.Data.DataRowExtensions.SetField%2A> método para acessar dados de coluna.  Nomes de propriedade estão disponíveis em tempo de compilação porque o tipo de informação está incluído no <xref:System.Data.DataSet>. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] fornece acesso aos valores de coluna como o tipo correto, para que os erros de incompatibilidade de tipo são detectados quando o código é compilado em vez de em tempo de execução.  
  
 Para que você possa começar a consultar um <xref:System.Data.DataSet> tipado, você deve gerar a classe usando o Designer de Conjunto de Dados no [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].  Para obter mais informações, consulte [Create and configure datasets (Criar e configurar conjuntos de dados)](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).  
  
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
 [Consultando DataSets](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [Consultas de tabela cruzada](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 [Consultas de tabela única](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)
