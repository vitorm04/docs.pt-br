---
title: Classificando e filtrando dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
ms.openlocfilehash: 02a67a490eb8339663aac08c97c665ffee09f0df
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="sorting-and-filtering-data"></a>Classificando e filtrando dados
O <xref:System.Data.DataView> fornece várias maneiras de classificar e filtrar dados em uma <xref:System.Data.DataTable>:  
  
-   Você pode usar a propriedade <xref:System.Data.DataView.Sort%2A> para especificar uma ou várias ordens de classificação de coluna, e para incluir parâmetros ASC (crescente) e DESC (decrescente).  
  
-   Você pode usar a propriedade <xref:System.Data.DataView.ApplyDefaultSort%2A> para criar automaticamente uma ordem de classificação, em ordem crescente, com base na coluna de chave primária ou nas colunas da tabela. <xref:System.Data.DataView.ApplyDefaultSort%2A> só se aplica quando o **classificação** propriedade é uma referência nula ou uma cadeia de caracteres vazia, e quando a tabela tem uma chave primária definida.  
  
-   Você pode usar a propriedade <xref:System.Data.DataView.RowFilter%2A> para especificar subconjuntos de linhas com base nos valores de coluna. Para obter detalhes sobre expressões válidas para o **RowFilter** propriedade, consulte as informações de referência para o <xref:System.Data.DataColumn.Expression%2A> propriedade o <xref:System.Data.DataColumn> classe.  
  
     Se você quiser retornar os resultados de uma determinada consulta nos dados, em vez de fornecer uma exibição dinâmica de um subconjunto dos dados, usam o <xref:System.Data.DataView.Find%2A> ou <xref:System.Data.DataView.FindRows%2A> métodos do **DataView** para obter melhor desempenho em vez de Definindo o **RowFilter** propriedade. Definindo o **RowFilter** propriedade recria o índice para os dados, adicionando sobrecarga para o seu aplicativo e diminuindo o desempenho. O **RowFilter** propriedade melhor é usada em um aplicativo de associação de dados em que um controle associado exibe resultados filtrados. O **localizar** e **FindRows** métodos aproveitam o índice atual sem a necessidade do índice seja reconstruído. Para obter mais informações sobre o **localizar** e **FindRows** métodos, consulte [localizando linhas](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).  
  
-   Você pode usar a propriedade <xref:System.Data.DataView.RowStateFilter%2A> para especificar quais versões de linha serão exibidas. O **DataView** implicitamente gerencia qual versão de linha para expor dependendo do **RowState** da linha de base. Por exemplo, se o **RowStateFilter** é definido como **DataViewRowState.Deleted**, o **DataView** expõe o **Original** versão de linha de todos os **excluído** linhas porque não há nenhum **atual** versão de linha. Você pode determinar qual versão de linha de uma linha está sendo exposto por meio de **RowVersion** propriedade o **DataRowView**.  
  
     A tabela a seguir mostra as opções para **DataViewRowState**.  
  
    |Opções de DataViewRowState|Descrição|  
    |------------------------------|-----------------|  
    |**CurrentRows**|O **atual** versão de linha de todos os **inalterado**, **adicionado**, e **modificadas** linhas. Esse é o padrão.|  
    |**Adicionado**|O **atual** versão de linha de todos os **adicionado** linhas.|  
    |**excluído**|O **Original** versão de linha de todos os **excluído** linhas.|  
    |**ModifiedCurrent**|O **atual** versão de linha de todos os **modificadas** linhas.|  
    |**ModifiedOriginal**|O **Original** versão de linha de todos os **modificadas** linhas.|  
    |**Nenhum**|Nenhuma linha.|  
    |**OriginalRows**|O **Original** versão de linha de todos os **inalterado**, **modificadas**, e **excluído** linhas.|  
    |**Inalterado**|O **atual** versão de linha de todos os **inalterado** linhas.|  
  
 Para obter mais informações sobre estados de linha e versões de linha, consulte [estados de linha e versões de linha](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
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
 <xref:System.Data.DataViewRowState>  
 <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
