---
title: Criando um DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
ms.openlocfilehash: 19badb009ebe95c52ab1dbbaef96f280c769553b
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205160"
---
# <a name="creating-a-dataset"></a>Criando um DataSet
Você cria uma instância de um <xref:System.Data.DataSet> chamando o construtor <xref:System.Data.DataSet>. Opcionalmente especifique um argumento de nome. Se você não especificar um nome para o <xref:System.Data.DataSet>, o nome será definido como "NewDataSet".  
  
 Você também pode criar um novo <xref:System.Data.DataSet> baseado em um <xref:System.Data.DataSet> existente. O novo <xref:System.Data.DataSet> pode ser uma cópia exata do <xref:System.Data.DataSet> existente; um clone do <xref:System.Data.DataSet> que copia a estrutura relacional ou o esquema, mas que não contém nenhum dos dados do <xref:System.Data.DataSet> existente; ou um subconjunto de <xref:System.Data.DataSet>, que contém somente as linhas modificadas do <xref:System.Data.DataSet> existente usando o método <xref:System.Data.DataSet.GetChanges%2A>. Para obter mais informações, consulte [copiando conteúdo do conjunto](copying-dataset-contents.md)de dados.  
  
 O exemplo de código a seguir demonstra como criar uma instância de um <xref:System.Data.DataSet>.  
  
```vb  
Dim customerOrders As DataSet = New DataSet("CustomerOrders")  
```  
  
```csharp  
DataSet customerOrders = new DataSet("CustomerOrders");  
```  
  
## <a name="see-also"></a>Consulte também

- [Populating a DataSet from a DataAdapter](../populating-a-dataset-from-a-dataadapter.md) (Preenchendo um DataSet por meio de um DataAdapter)
- [DataSets, DataTables, and DataViews](index.md) (DataSets, DataTables e DataViews)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
