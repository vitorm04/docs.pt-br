---
title: Criar um DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: 9d21b17068ff3ce5b0bd3990144383d7f9ded2f9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151332"
---
# <a name="creating-a-dataview"></a>Criar um DataView
Há duas maneiras de criar um <xref:System.Data.DataView>. Você pode usar o construtor **DataView** ou criar <xref:System.Data.DataTable.DefaultView%2A> uma referência <xref:System.Data.DataTable>à propriedade do . O construtor **DataView** pode estar vazio ou pode tomar uma **Tabela de Dados** como um único argumento ou uma Tabela de **Dados,** juntamente com critérios de filtro, critérios de classificação e um filtro de estado de linha. Para obter mais informações sobre os argumentos adicionais disponíveis para uso com o **DataView,** consulte [Dados de classificação e filtragem](sorting-and-filtering-data.md).  
  
 Como o índice de um **DataView** é construído tanto quando o **DataView** é criado, quanto quando qualquer uma das propriedades **Sort**, **RowFilter**ou **RowStateFilter** são modificadas, você obtém o melhor desempenho fornecendo qualquer ordem de classificação inicial ou critérios de filtragem como argumentos de construtor quando você cria o **DataView**. Criar um **DataView** sem especificar critérios de classificação ou filtro e, em seguida, definir as propriedades **Classificar,** **RowFilter**ou **RowStateFilter** mais tarde faz com que o índice seja construído pelo menos duas vezes: uma vez quando o **DataView** é criado e novamente quando qualquer um dos tipos ou propriedades do filtro for modificado.  
  
 Observe que se você criar um **DataView** usando o construtor que não tenha argumentos, você não poderá usar o **DataView** até definir a propriedade **Tabela.**  
  
 O exemplo de código a seguir demonstra como criar um **DataView** usando o construtor **DataView.** Uma **coluna RowFilter**, **Sort** e **DataViewRowState** são fornecidas juntamente com a **Tabela de Dados**.  
  
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
  
 O exemplo de código a seguir demonstra como obter uma referência ao **DataView** padrão de uma Tabela de **Dados** usando a propriedade **DefaultView** da tabela.  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a>Confira também

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [DataViews](dataviews.md)
- [Classificando e filtrando dados](sorting-and-filtering-data.md)
- [DataTables](datatables.md)
- [Visão geral do ADO.NET](../ado-net-overview.md)
