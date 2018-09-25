---
title: Criando um DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: b88df66ef2e065d1db8d4033eb1fb0e47ebdd189
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47108709"
---
# <a name="creating-a-dataview"></a>Criando um DataView
Há duas maneiras de criar um <xref:System.Data.DataView>. Você pode usar o **DataView** construtor, ou você pode criar uma referência para o <xref:System.Data.DataTable.DefaultView%2A> propriedade do <xref:System.Data.DataTable>. O **DataView** construtor pode estar vazia ou pode levar a um **DataTable** como um único argumento, ou uma **DataTable** juntamente com os critérios de filtro, critérios de classificação e uma linha filtro de estado. Para obter mais informações sobre os argumentos adicionais disponíveis para uso com o **DataView**, consulte [classificando e filtrando dados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).  
  
 Porque o índice para uma **DataView** é compilado quando o **DataView** é criado e quando qualquer um dos **classificação**, **RowFilter**, ou  **RowStateFilter** propriedades são modificadas, você obter o melhor desempenho, fornecendo uma ordem de classificação inicial ou critérios de filtragem como argumentos de construtor quando você cria o **DataView**. Criando um **DataView** sem especificar critérios de classificação ou filtragem e, em seguida, definindo o **classificação**, **RowFilter**, ou **RowStateFilter** propriedades posteriormente faz com que o índice a ser compilado pelo menos duas vezes: depois de quando o **DataView** é criado, e novamente quando qualquer uma das propriedades de classificação ou filtragem são alteradas.  
  
 Observe que, se você criar uma **DataView** usando o construtor que não leva argumentos, você não poderá usar o **DataView** até que você tenha definido o **tabela** propriedade .  
  
 O exemplo de código a seguir demonstra como criar uma **DataView** usando o **DataView** construtor. Um **RowFilter**, **classificação** coluna, e **DataViewRowState** são fornecidos juntamente com o **DataTable**.  
  
```vb  
Dim custDV As DataView = New DataView(custDS.Tables("Customers"), _  
    "Country = 'USA'", _  
    "ContactName", _  
    DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView custDV = new DataView(custDS.Tables["Customers"],   
    "Country = 'USA'",   
    "ContactName",   
    DataViewRowState.CurrentRows);  
```  
  
 O exemplo de código a seguir demonstra como obter uma referência para o padrão **DataView** de uma **DataTable** usando o **DefaultView** propriedade da tabela.  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [Classificando e filtrando dados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)  
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
