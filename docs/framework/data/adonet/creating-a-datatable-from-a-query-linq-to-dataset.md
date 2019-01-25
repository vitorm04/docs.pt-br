---
title: Criando um DataTable de uma consulta (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b97afeb-03f8-41e2-8eb3-58aff65f7d18
ms.openlocfilehash: fd2b639f98dbb381cf4bea70cc790fd99ebf185f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54708344"
---
# <a name="creating-a-datatable-from-a-query-linq-to-dataset"></a>Criando um DataTable de uma consulta (LINQ to DataSet)
A vinculação de dados é um uso comum do objeto <xref:System.Data.DataTable>. O método <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> recebe os resultados de uma consulta e copia os dados em um <xref:System.Data.DataTable>, que podem ser usados para vinculação de dados. Quando as operações de dados tiverem sido executadas, o novo <xref:System.Data.DataTable> será mesclado de volta no <xref:System.Data.DataTable> de origem.  
  
 O método <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> usa o seguinte processo para criar um <xref:System.Data.DataTable> de uma consulta:  
  
1.  O método <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> clona um <xref:System.Data.DataTable> da tabela de origem (um objeto <xref:System.Data.DataTable> que implementa a interface <xref:System.Linq.IQueryable%601>). A fonte do <xref:System.Collections.IEnumerable> foi geralmente originada de uma expressão [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] ou consulta de método.  
  
2.  O esquema do <xref:System.Data.DataTable> clonado é criado de colunas do primeiro objeto <xref:System.Data.DataRow> enumerado na tabela de origem e o nome da tabela clonada é o nome da tabela de origem com a palavra “consulta” adicionada a ele.  
  
3.  Para cada linha na tabela de origem, o conteúdo da linha é copiado para um novo objeto <xref:System.Data.DataRow>, que é, em seguida, inserido na tabela clonada. As propriedades <xref:System.Data.DataRow.RowState%2A> e <xref:System.Data.DataRow.RowError%2A> são preservadas na operação de cópia. Um <xref:System.ArgumentException> é gerado se os objetos <xref:System.Data.DataRow> na fonte forem de tabelas diferentes.  
  
4.  O <xref:System.Data.DataTable> clonado é retornado após todos os objetos <xref:System.Data.DataRow> na tabela consultável de entrada terem sido copiados. Se a sequência de origem não contiver nenhum objeto <xref:System.Data.DataRow>, o método retornará um <xref:System.Data.DataTable> vazio.  
  
 Observe que a chamada ao método <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> fará com que a consulta associada à tabela de origem seja executada.  
  
 Quando o método <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> encontrar uma referência nula ou o tipo de valor anulável em uma linha na tabela de origem, ele substituirá o valor por <xref:System.DBNull.Value>. Dessa maneira, os valores nulos serão manipulados corretamente no <xref:System.Data.DataTable> retornado.  
  
 Observação: O <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> método aceita como entrada uma consulta que pode retornar linhas de vários <xref:System.Data.DataTable> ou <xref:System.Data.DataSet> objetos. O método <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> copiará os dados mas não as propriedades dos objetos <xref:System.Data.DataTable> ou <xref:System.Data.DataSet> de origem para o <xref:System.Data.DataTable> retornado. Você precisará definir explicitamente as propriedades no <xref:System.Data.DataTable> retornado, por exemplo <xref:System.Data.DataTable.Locale%2A> e <xref:System.Data.DataTable.TableName%2A>.  
  
 O exemplo a seguir consulta a tabela SalesOrderHeader para pedidos após 8 de agosto de 2001 e usa o método <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> para criar um <xref:System.Data.DataTable> a partir dessa consulta. O <xref:System.Data.DataTable> é então associado a um <xref:System.Windows.Forms.BindingSource>, que age como o proxy para um <xref:System.Windows.Forms.DataGridView>.  
  
 [!code-csharp[DP LINQ to DataSet Examples#CopyToDataTable1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#copytodatatable1)]
 [!code-vb[DP LINQ to DataSet Examples#CopyToDataTable1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#copytodatatable1)]  
  
## <a name="creating-a-custom-copytodatatablet-method"></a>Criar um personalizado CopyToDataTable\<T > método  
 Os métodos <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> existentes somente funcionam em uma fonte de <xref:System.Collections.Generic.IEnumerable%601> onde o parâmetro genérico `T` é do tipo <xref:System.Data.DataRow>. Embora isso seja útil, não permite que as tabelas sejam criadas de uma sequência de tipos escalares, de consultas que retornam tipos anônimos ou de consultas que executam uniões de tabela. Para obter um exemplo de como implementar dois personalizado `CopyToDataTable` métodos que carregam uma tabela de uma sequência de tipos anônimos ou escalares, consulte [como: Implementar CopyToDataTable\<T > em que o tipo genérico T não é um DataRow](../../../../docs/framework/data/adonet/implement-copytodatatable-where-type-not-a-datarow.md)s.  
  
 Os exemplos nesta seção usam os seguintes tipos personalizados:  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#ItemClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#itemclass)]
 [!code-vb[DP Custom CopyToDataTable Examples#ItemClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#itemclass)]  
  
### <a name="example"></a>Exemplo  
 Este exemplo realiza uma união das tabelas `SalesOrderHeader` e `SalesOrderDetail` para obter pedidos online do mês de agosto e cria uma tabela da consulta.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#join)]
 [!code-vb[DP Custom CopyToDataTable Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#join)]  
  
### <a name="example"></a>Exemplo  
 O exemplo a seguir consulta uma coleção em busca de itens de preço maior que US$9,99 e cria uma tabela dos resultados da consulta.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsIntoTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsintotable)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsIntoTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsintotable)]  
  
### <a name="example"></a>Exemplo  
 O exemplo a seguir consulta uma coleção em busca de itens de preço maior que US$9,99 e projeta os resultados. A sequência retornada de tipos anônimos é carregada em uma tabela existente.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsIntoExistingTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsintoexistingtable)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsIntoExistingTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsintoexistingtable)]  
  
### <a name="example"></a>Exemplo  
 O exemplo a seguir consulta uma coleção em busca de itens de preço maior que US$9,99 e projeta os resultados. A sequência retornada de tipos anônimos é carregada em uma tabela existente. O esquema da tabela é automaticamente expandido porque os tipos `Book` e `Movies` são derivados do tipo `Item`.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsExpandSchema](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsexpandschema)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsExpandSchema](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsexpandschema)]  
  
### <a name="example"></a>Exemplo  
 O exemplo a seguir consulta uma coleção em busca de itens de preço maior que US$9,99 e retorna uma sequência de <xref:System.Double>, que é carregada em uma nova tabela.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadScalarSequence](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loadscalarsequence)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadScalarSequence](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loadscalarsequence)]  
  
## <a name="see-also"></a>Consulte também
- [Guia de Programação](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
- [Campo genérico e métodos de SetField](../../../../docs/framework/data/adonet/generic-field-and-setfield-methods-linq-to-dataset.md)
- [Exemplos de LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
