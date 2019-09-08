---
title: Classificando e filtrando dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
ms.openlocfilehash: 09cee2f2b2c3288c835912c9f311bf2511c7b0d0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785921"
---
# <a name="sorting-and-filtering-data"></a>Classificando e filtrando dados
O <xref:System.Data.DataView> fornece várias maneiras de classificar e filtrar dados em uma <xref:System.Data.DataTable>:  
  
- Você pode usar a propriedade <xref:System.Data.DataView.Sort%2A> para especificar uma ou várias ordens de classificação de coluna, e para incluir parâmetros ASC (crescente) e DESC (decrescente).  
  
- Você pode usar a propriedade <xref:System.Data.DataView.ApplyDefaultSort%2A> para criar automaticamente uma ordem de classificação, em ordem crescente, com base na coluna de chave primária ou nas colunas da tabela. <xref:System.Data.DataView.ApplyDefaultSort%2A>aplica-se somente quando a propriedade **Sort** é uma referência nula ou uma cadeia de caracteres vazia e quando a tabela tem uma chave primária definida.  
  
- Você pode usar a propriedade <xref:System.Data.DataView.RowFilter%2A> para especificar subconjuntos de linhas com base nos valores de coluna. Para obter detalhes sobre as expressões válidas para a propriedade **userFilter** , consulte as informações <xref:System.Data.DataColumn.Expression%2A> de referência para <xref:System.Data.DataColumn> a propriedade da classe.  
  
     Se você quiser retornar os resultados de uma consulta específica nos dados, em vez de fornecer uma exibição dinâmica de um subconjunto dos dados, use os <xref:System.Data.DataView.Find%2A> métodos ou <xref:System.Data.DataView.FindRows%2A> do **DataView** para obter o melhor desempenho em vez de definir oPropriedade de filtro. A configuração da propriedade **userFilter** recria o índice para os dados, adicionando sobrecarga ao seu aplicativo e diminuindo o desempenho. A propriedade **doFilter** é melhor usada em um aplicativo associado a dados em que um controle ligado exibe resultados filtrados. Os métodos **Find** e **FindRows** aproveitam o índice atual sem exigir que o índice seja recriado. Para obter mais informações sobre os métodos **Find** e **FindRows** , consulte [Localizando linhas](finding-rows.md).  
  
- Você pode usar a propriedade <xref:System.Data.DataView.RowStateFilter%2A> para especificar quais versões de linha serão exibidas. O **DataView** gerencia implicitamente qual versão de linha é exposta, dependendo do **RowState** da linha subjacente. Por exemplo, se **RowStateFilter** for definido como **DataViewRowState. Deleted**, o **DataView** expõe a versão de linha **original** de todas as linhas **excluídas** porque não há nenhuma versão de linha **atual** . Você pode determinar qual versão de linha de uma linha está sendo exposta usando a **Propriedade rowgroup** do **DataRowView**.  
  
     A tabela a seguir mostra as opções para **DataViewRowState**.  
  
    |Opções de DataViewRowState|Descrição|  
    |------------------------------|-----------------|  
    |**CurrentRows**|A versão de linha **atual** de todas as linhas **inalteradas**, **adicionadas**e **modificadas** . Esse é o padrão.|  
    |**Mais**|A versão de linha **atual** de todas as linhas **adicionadas** .|  
    |**Excluí**|A versão de linha **original** de todas as linhas **excluídas** .|  
    |**ModifiedCurrent**|A versão da linha **atual** de todas as linhas **modificadas** .|  
    |**ModifiedOriginal**|A versão de linha **original** de todas as linhas **modificadas** .|  
    |**Nenhum**|Nenhuma linha.|  
    |**OriginalRows**|A versão de linha **original** de todas as linhas **inalteradas**, **modificadas**e **excluídas** .|  
    |**Inalterado**|A versão de linha **atual** de todas as linhas **inalteradas** .|  
  
 Para obter mais informações sobre Estados de linha e versões de linha, consulte [Estados de linha e versões de linha](row-states-and-row-versions.md).  
  
 O exemplo de código a seguir cria uma exibição que mostra todos os produtos em que o número de unidades em estoque é menor ou igual ao nível de reordenação, classificado primeiro por ID do fornecedor e, depois, por nome do produto.  
  
```vb  
Dim prodView As DataView = New DataView(prodDS.Tables("Products"), _  
   "UnitsInStock <= ReorderLevel", _  
   "SupplierID, ProductName", _  
   DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView prodView = new DataView(prodDS.Tables["Products"],  
   "UnitsInStock <= ReorderLevel",  
   "SupplierID, ProductName",  
   DataViewRowState.CurrentRows);  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [DataViews](dataviews.md)
- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)
