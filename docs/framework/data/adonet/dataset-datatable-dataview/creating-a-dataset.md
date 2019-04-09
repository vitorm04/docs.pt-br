---
title: Criando um DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
ms.openlocfilehash: d2d17056e6dcd29ef9b5c5e8c3024a32fce32bd5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59118177"
---
# <a name="creating-a-dataset"></a>Criando um DataSet
Você cria uma instância de um <xref:System.Data.DataSet> chamando o construtor <xref:System.Data.DataSet>. Opcionalmente especifique um argumento de nome. Se você não especificar um nome para o <xref:System.Data.DataSet>, o nome será definido como "NewDataSet".  
  
 Você também pode criar um novo <xref:System.Data.DataSet> baseado em um <xref:System.Data.DataSet> existente. O novo <xref:System.Data.DataSet> pode ser uma cópia exata do <xref:System.Data.DataSet> existente; um clone do <xref:System.Data.DataSet> que copia a estrutura relacional ou o esquema, mas que não contém nenhum dos dados do <xref:System.Data.DataSet> existente; ou um subconjunto de <xref:System.Data.DataSet>, que contém somente as linhas modificadas do <xref:System.Data.DataSet> existente usando o método <xref:System.Data.DataSet.GetChanges%2A>. Para obter mais informações, consulte [copiando o conteúdo do DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md).  
  
 O exemplo de código a seguir demonstra como criar uma instância de um <xref:System.Data.DataSet>.  
  
```vb  
Dim customerOrders As DataSet = New DataSet("CustomerOrders")  
```  
  
```csharp  
DataSet customerOrders = new DataSet("CustomerOrders");  
```  
  
## <a name="see-also"></a>Consulte também

- [Populando um DataSet a partir de um DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)
- [DataSets, DataTables e DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
