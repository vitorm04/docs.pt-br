---
title: Criando um DataView
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
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1a8529c317025dbabd9c7467557b244b2f452a77
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="creating-a-dataview"></a>Criando um DataView
Há duas maneiras de criar um <xref:System.Data.DataView>. Você pode usar o **DataView** construtor, ou você pode criar uma referência para o <xref:System.Data.DataTable.DefaultView%2A> propriedade o <xref:System.Data.DataTable>. O **DataView** construtor pode estar vazia ou pode levar a um **DataTable** como um único argumento, ou um **DataTable** juntamente com os critérios de filtro, os critérios de classificação e uma linha filtro de estado. Para obter mais informações sobre os argumentos adicionais disponíveis para uso com o **DataView**, consulte [classificando e filtrando dados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).  
  
 Porque o índice para uma **DataView** baseia-se ambos os quando o **DataView** é criado e quando qualquer uma da **classificação**, **RowFilter**, ou  **RowStateFilter** propriedades são modificadas, você obter melhor desempenho, fornecendo uma ordem de classificação inicial ou critérios de filtragem como argumentos de construtor quando você cria o **DataView**. Criando um **DataView** sem especificar critérios de classificação ou filtragem e, em seguida, definindo o **classificação**, **RowFilter**, ou **RowStateFilter** propriedades posteriormente faz com que o índice seja criado pelo menos duas vezes: depois de quando o **DataView** é criado, e novamente quando qualquer uma das propriedades de classificação ou filtro são modificados.  
  
 Observe que, se você criar um **DataView** usando o construtor que não tem nenhum argumento, você não poderá usar o **DataView** até que você definiu o **tabela** propriedade .  
  
 O exemplo de código a seguir demonstra como criar um **DataView** usando o **DataView** construtor. Um **RowFilter**, **classificação** coluna, e **DataViewRowState** são fornecidos junto com o **DataTable**.  
  
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
  
 O exemplo de código a seguir demonstra como obter uma referência para o padrão **DataView** de um **DataTable** usando o **DefaultView** propriedade da tabela.  
  
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
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
