---
title: Criar um DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: 3e1c31dac458594eee70ddd99469aca7cf63b848
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785480"
---
# <a name="creating-a-dataview"></a>Criar um DataView
Há duas maneiras de criar um <xref:System.Data.DataView>. Você pode usar o construtor **DataView** ou pode criar uma referência à <xref:System.Data.DataTable.DefaultView%2A> Propriedade do. <xref:System.Data.DataTable> O construtor **DataView** pode estar vazio ou pode ter uma **DataTable** como um único argumento, ou uma **DataTable** junto com critérios de filtro, critérios de classificação e um filtro de estado de linha. Para obter mais informações sobre os argumentos adicionais disponíveis para uso com o **DataView**, consulte [classificando e Filtrando dados](sorting-and-filtering-data.md).  
  
 Como o índice de um **DataView** é criado tanto quando o **DataView** é criado, quanto quando qualquer uma das propriedades **Sort**, **RowStateFilter** **ou de propriedade**é modificada, você obtém o melhor desempenho fornecendo qualquer ordem de classificação ou critérios de filtragem como argumentos de Construtor quando você cria o **DataView**. A criação de um **DataView** sem especificar critérios de classificação ou de filtro e, em seguida, definir as propriedades **Sort**, **userFilter**ou **RowStateFilter** posteriormente faz com que o índice seja criado pelo menos duas vezes: uma vez quando o **DataView** é criado e novamente quando qualquer uma das propriedades de classificação ou de filtro é modificada.  
  
 Observe que se você criar um **DataView** usando o construtor que não usa argumentos, não será possível usar o **DataView** até que você defina a propriedade **Table** .  
  
 O exemplo de código a seguir demonstra como criar um **DataView** usando o construtor **DataView** . Um **filtro**de lista, coluna de **classificação** e **DataViewRowState** são fornecidos junto com a **DataTable**.  
  
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
  
 O exemplo de código a seguir demonstra como obter uma referência ao **DataView** padrão de uma **DataTable** usando a propriedade **ModoPadrão** da tabela.  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [DataViews](dataviews.md)
- [Classificando e filtrando dados](sorting-and-filtering-data.md)
- [DataTables](datatables.md)
- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)
