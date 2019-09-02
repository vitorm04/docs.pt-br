---
title: Criar um DataReader
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
ms.openlocfilehash: cb39ead1fe15e3bfcf67370e4675dcae3bbf9801
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203903"
---
# <a name="creating-a-datareader"></a>Criar um DataReader
As <xref:System.Data.DataTable> classes <xref:System.Data.DataSet> e têm um <xref:System.Data.DataTable.CreateDataReader%2A> método que retorna o <xref:System.Data.DataSet> conteúdo do <xref:System.Data.DataTable> ou o conteúdo da coleção do <xref:System.Data.DataSet.Tables%2A> objeto como um ou mais conjuntos de resultados somente de encaminhamento e somente leitura.  
  
## <a name="example"></a>Exemplo  
 O aplicativo de console a seguir <xref:System.Data.DataTable> cria uma instância do. Em seguida, o exemplo passa <xref:System.Data.DataTable> o preenchido para um procedimento que <xref:System.Data.DataTable.CreateDataReader%2A> chama o método, que itera pelos resultados contidos <xref:System.Data.DataTableReader>no.  
  
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

- <xref:System.Data.DataTable.CreateDataReader%2A>
- <xref:System.Data.DataSet.CreateDataReader%2A>
- [DataTableReaders](datatablereaders.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
