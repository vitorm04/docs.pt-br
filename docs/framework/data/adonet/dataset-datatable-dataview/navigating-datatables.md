---
title: Navegar DataTables
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 202026a1-ec79-435e-b507-12a77f5011b2
ms.openlocfilehash: 5008f8397b7d396b14fdfe8e24f1e59785c4319d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785258"
---
# <a name="navigating-datatables"></a>Navegar DataTables
O <xref:System.Data.DataTableReader> obtém o conteúdo de um ou mais objetos <xref:System.Data.DataTable> na forma de um ou mais conjuntos de resultados somente leitura de somente avanço.  
  
 Um <xref:System.Data.DataTableReader> pode conter vários conjuntos de resultados se ele for criado usando o <xref:System.Data.DataSet.CreateDataReader%2A> método. Quando há mais de um conjunto de resultados, o <xref:System.Data.DataTableReader.NextResult%2A> método avança o cursor para o próximo conjunto de resultados. Esse é um processo somente de encaminhamento. Não é possível retornar a um conjunto de resultados anterior.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, o `TestConstructor` método cria duas <xref:System.Data.DataTable> instâncias. Para demonstrar esse construtor para a <xref:System.Data.DataTableReader> classe, o exemplo cria um novo **DataTableReader** com base em uma matriz que contém as duas **tabelas**e executa uma operação simples, imprimindo o conteúdo dos primeiros colunas na janela do console.  
  
 [!code-csharp[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/VB/source.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- [DataTableReaders](datatablereaders.md)
- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)
