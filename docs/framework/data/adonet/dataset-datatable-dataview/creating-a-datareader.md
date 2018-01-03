---
title: Criando um DataReader
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 169f290ba41e7efe1ceb7c57f0821fdc0a886c5e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-datareader"></a>Criando um DataReader
O <xref:System.Data.DataTable> e <xref:System.Data.DataSet> classes têm uma <xref:System.Data.DataTable.CreateDataReader%2A> método que retorna o conteúdo do <xref:System.Data.DataTable> ou o conteúdo do <xref:System.Data.DataSet> do objeto <xref:System.Data.DataSet.Tables%2A> coleção como um ou mais conjuntos de resultados somente leitura, somente encaminhamento.  
  
## <a name="example"></a>Exemplo  
 O aplicativo de console a seguir cria um <xref:System.Data.DataTable> instância. O exemplo, em seguida, passa o preenchido <xref:System.Data.DataTable> para um procedimento que chama o <xref:System.Data.DataTable.CreateDataReader%2A> método, que itera através dos resultados contidos a <xref:System.Data.DataTableReader>.  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 O exemplo exibe a seguinte saída na janela do console:  
  
```  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Data.DataTable.CreateDataReader%2A>  
 <xref:System.Data.DataSet.CreateDataReader%2A>  
 [DataTableReaders](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
