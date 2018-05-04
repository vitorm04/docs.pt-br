---
title: Navegando DataTables
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 202026a1-ec79-435e-b507-12a77f5011b2
ms.openlocfilehash: 3bd10694512e828354254588361cc009aac6602f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="navigating-datatables"></a>Navegando DataTables
O <xref:System.Data.DataTableReader> obtém o conteúdo de um ou mais objetos <xref:System.Data.DataTable> na forma de um ou mais conjuntos de resultados somente leitura de somente avanço.  
  
 Um <xref:System.Data.DataTableReader> pode conter vários conjuntos de resultados se ela for criada usando o <xref:System.Data.DataSet.CreateDataReader%2A> método. Quando há mais de um conjunto de resultados, o <xref:System.Data.DataTableReader.NextResult%2A> método avança o cursor para o próximo conjunto de resultados. Esse é um processo de somente avanço. Não é possível retornar a um conjunto de resultados anterior.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, o `TestConstructor` método cria dois <xref:System.Data.DataTable> instâncias. Para demonstrar a este construtor para o <xref:System.Data.DataTableReader> classe, o exemplo cria um novo **DataTableReader** com base em uma matriz que contém os dois **DataTables**e executa uma operação simples, Imprimir o conteúdo de algumas colunas primeiro para a janela do console.  
  
 [!code-csharp[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/VB/source.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 [DataTableReaders](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
