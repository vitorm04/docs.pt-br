---
title: Modificando DataViews
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
ms.openlocfilehash: 3663b0317176495b13b1092652bd8bf4c79f30d2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760096"
---
# <a name="modifying-dataviews"></a>Modificando DataViews
Você pode usar o <xref:System.Data.DataView> para adicionar, excluir ou modificar linhas de dados na tabela subjacente. A capacidade de usar o **DataView** modificar os dados na tabela subjacente é controlado pela definição de uma das três propriedades Boolean o **DataView**. Essas propriedades são <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A>, e <xref:System.Data.DataView.AllowDelete%2A>. Eles são definidos como **true** por padrão.  
  
 Se **AllowNew** é **true**, você pode usar o <xref:System.Data.DataView.AddNew%2A> método o **DataView** para criar um novo <xref:System.Data.DataRowView>. Observe que uma nova linha não é realmente adicionado ao subjacente <xref:System.Data.DataTable> até que o <xref:System.Data.DataRowView.EndEdit%2A> método o **DataRowView** é chamado. Se o <xref:System.Data.DataRowView.CancelEdit%2A> método o **DataRowView** é chamado, a nova linha será descartada. Observe também que você pode editar somente uma **DataRowView** por vez. Se você chamar o **AddNew** ou **BeginEdit** método o **DataRowView** enquanto existe uma linha pendente, **EndEdit** é chamado implicitamente no linha pendente. Quando **EndEdit** é chamado, as alterações são aplicadas ao subjacente **DataTable** e posteriormente pode ser confirmada ou rejeitada usando o **AcceptChanges** ou  **RejectChanges** métodos do **DataTable**, **DataSet**, ou **DataRow** objeto. Se **AllowNew** é **false**, uma exceção é gerada se você chamar o **AddNew** método o **DataRowView**.  
  
 Se **AllowEdit** é **true**, você pode modificar o conteúdo de um **DataRow** por meio de **DataRowView**. Você pode confirmar as alterações para a linha de base usando **DataRowView.EndEdit** ou rejeitar as alterações usando **DataRowView.CancelEdit**. Observe que somente uma linha pode ser editada por vez. Se você chamar o **AddNew** ou **BeginEdit** métodos do **DataRowView** enquanto existe uma linha pendente, **EndEdit** é chamado implicitamente em a linha pendente. Quando **EndEdit** é chamado, as alterações propostas são colocadas no **atual** versão de linha de base **DataRow** e posteriormente pode ser confirmada ou rejeitada usando o  **AcceptChanges** ou **RejectChanges** métodos do **DataTable**, **DataSet**, ou **DataRow** objeto. Se **AllowEdit** é **false**, uma exceção é gerada se você tentar modificar um valor de **DataView**.  
  
 Quando um existente **DataRowView** está sendo editado, eventos de subjacente **DataTable** ainda será gerado com as alterações propostas. Observe que, se você chamar **EndEdit** ou **CancelEdit** em subjacente **DataRow**, pendente alterações serão aplicadas ou canceladas independentemente se  **EndEdit** ou **CancelEdit** é chamado de **DataRowView**.  
  
 Se **AllowDelete** é **true**, você pode excluir linhas do **DataView** usando o **excluir** método o **DataView**  ou **DataRowView** objeto e as linhas são excluídas de subjacente **DataTable**. Posteriormente, você pode confirmar ou rejeitar as exclusões usando **AcceptChanges** ou **RejectChanges** respectivamente. Se **AllowDelete** é **false**, uma exceção é gerada se você chamar o **excluir** método o **DataView** ou  **DataRowView**.  
  
 O exemplo de código a seguir desabilita o uso de **DataView** para excluir linhas e adiciona uma nova linha à tabela subjacente usando a **DataView**.  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custView As DataView = custTable.DefaultView  
custView.Sort = "CompanyName"  
  
custView.AllowDelete = False  
  
Dim newDRV As DataRowView = custView.AddNew()  
newDRV("CustomerID") = "ABCDE"  
newDRV("CompanyName") = "ABC Products"  
newDRV.EndEdit()  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
DataView custView = custTable.DefaultView;  
custView.Sort = "CompanyName";  
  
custView.AllowDelete = false;  
  
DataRowView newDRV = custView.AddNew();  
newDRV["CustomerID"] = "ABCDE";  
newDRV["CompanyName"] = "ABC Products";  
newDRV.EndEdit();  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 <xref:System.Data.DataRowView>  
 [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
