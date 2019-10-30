---
title: Criar um DataReader
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
ms.openlocfilehash: 696eb4dfc334390e1968dd317d441f3c987a1f77
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040116"
---
# <a name="creating-a-datareader"></a>Criar um DataReader
As classes <xref:System.Data.DataTable> e <xref:System.Data.DataSet> têm um método <xref:System.Data.DataTable.CreateDataReader%2A> que retorna o conteúdo do <xref:System.Data.DataTable> ou o conteúdo da coleção <xref:System.Data.DataSet> do objeto <xref:System.Data.DataSet.Tables%2A> como um ou mais conjuntos de resultados somente de encaminhamento e somente leitura.  
  
## <a name="example"></a>Exemplo  
 O aplicativo de console a seguir cria uma instância de <xref:System.Data.DataTable>. Em seguida, o exemplo passa o <xref:System.Data.DataTable> preenchido para um procedimento que chama o método <xref:System.Data.DataTable.CreateDataReader%2A>, que itera pelos resultados contidos no <xref:System.Data.DataTableReader>.  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 O exemplo exibe a seguinte saída na janela do console:  
  
```output  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Data.DataTable.CreateDataReader%2A>
- <xref:System.Data.DataSet.CreateDataReader%2A>
- [DataTableReaders](datatablereaders.md)
- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)
