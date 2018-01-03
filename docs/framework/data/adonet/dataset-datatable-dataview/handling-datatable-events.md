---
title: "Manipulação de eventos de DataTable"
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
ms.assetid: 62f404a5-13ea-4b93-a29f-55b74a16c9d3
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: f7ab9d1043fdd1d4d78ec09390f227f297e471c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="handling-datatable-events"></a>Manipulação de eventos de DataTable
O <xref:System.Data.DataTable> objeto fornece uma série de eventos que podem ser processadas por um aplicativo. A tabela a seguir descreve `DataTable` eventos.  
  
|evento|Descrição|  
|-----------|-----------------|  
|<xref:System.Data.DataTable.Initialized>|Ocorre após o <xref:System.Data.DataTable.EndInit%2A> método de um `DataTable` é chamado. Esse evento destina-se principalmente para oferecer suporte a cenários de tempo de design.|  
|<xref:System.Data.DataTable.ColumnChanged>|Ocorre depois que um valor foi alterado com êxito em um <xref:System.Data.DataColumn>.|  
|<xref:System.Data.DataTable.ColumnChanging>|Ocorre quando um valor é enviado para um `DataColumn`.|  
|<xref:System.Data.DataTable.RowChanged>|Ocorre após um `DataColumn` valor ou o <xref:System.Data.DataRow.RowState%2A> de um <xref:System.Data.DataRow> no `DataTable` foi alterada com êxito.|  
|<xref:System.Data.DataTable.RowChanging>|Ocorre quando uma alteração é enviada para um `DataColumn` valor ou o `RowState` de um `DataRow` no `DataTable`.|  
|<xref:System.Data.DataTable.RowDeleted>|Ocorre após um `DataRow` no `DataTable` tiver sido marcada como `Deleted`.|  
|<xref:System.Data.DataTable.RowDeleting>|Ocorre antes de um `DataRow` no `DataTable` está marcado como `Deleted`.|  
|<xref:System.Data.DataTable.TableCleared>|Ocorre após uma chamada para o <xref:System.Data.DataTable.Clear%2A> método o `DataTable` foi limpo com êxito todos os `DataRow`.|  
|<xref:System.Data.DataTable.TableClearing>|Ocorre após o `Clear` método é chamado, mas antes de `Clear` início da operação.|  
|<xref:System.Data.DataTable.TableNewRow>|Ocorre depois que um novo `DataRow` é criado por uma chamada para o `NewRow` método o `DataTable`.|  
|<xref:System.ComponentModel.MarshalByValueComponent.Disposed>|Ocorre quando o `DataTable` é `Disposed`. Herdada de <xref:System.ComponentModel.MarshalByValueComponent>.|  
  
> [!NOTE]
>  A maioria das operações que adicionar ou excluir linhas não aumente o `ColumnChanged` e `ColumnChanging` eventos. No entanto, o `ReadXml` método gerar `ColumnChanged` e `ColumnChanging` eventos, a menos que o `XmlReadMode` é definido como `DiffGram` ou é definido como `Auto` quando o documento XML que está sendo lido é um `DiffGram`.  
  
> [!WARNING]
>  Pode ocorrer corrupção de dados se os dados são modificados em um `DataSet` do qual o `RowChanged` é gerado. Nenhuma exceção será gerada se tais danos.  
  
## <a name="additional-related-events"></a>Eventos relacionados adicionais  
 O <xref:System.Data.DataTable.Constraints%2A> propriedade mantém um <xref:System.Data.ConstraintCollection> instância. O <xref:System.Data.ConstraintCollection> classe expõe um <xref:System.Data.ConstraintCollection.CollectionChanged> eventos. Esse evento é acionado quando uma restrição é adicionada, modificada ou removida da `ConstraintCollection`.  
  
 O <xref:System.Data.DataTable.Columns%2A> propriedade mantém um <xref:System.Data.DataColumnCollection> instância. O `DataColumnCollection` classe expõe um <xref:System.Data.DataColumnCollection.CollectionChanged> eventos. Esse evento é acionado quando um `DataColumn` é adicionado, modificado ou removido o `DataColumnCollection`. Modificações que fazer com que o evento seja acionado incluem alterações para o nome, o tipo, a expressão ou a posição ordinal de uma coluna.  
  
 O <xref:System.Data.DataSet.Tables%2A> propriedade de um <xref:System.Data.DataSet> mantém um <xref:System.Data.DataTableCollection> instância. O `DataTableCollection` classe expõe ambos um `CollectionChanged` e um `CollectionChanging` eventos. Esses eventos acionam quando um `DataTable` é adicionado ou removido o `DataSet`.  
  
 Alterações em `DataRows` também pode disparar eventos de um tipo de <xref:System.Data.DataView>. O `DataView` classe expõe um <xref:System.Data.DataView.ListChanged> evento acionado quando um `DataColumn` alterações de valor ou quando a ordem de classificação ou de composição do modo de exibição é alterado. O <xref:System.Data.DataRowView> classe expõe um <xref:System.Data.DataRowView.PropertyChanged> evento é acionado quando um tipo de `DataColumn` o valor é alterado.  
  
## <a name="sequence-of-operations"></a>Sequência de operações  
 Aqui está a sequência de operações que ocorrem quando um `DataRow` é adicionada, modificada ou excluída:  
  
1.  Criar o registro de proposta e aplicar as alterações.  
  
2.  Verificar restrições para colunas de expressão não.  
  
3.  Gerar o `RowChanging` ou `RowDeleting` eventos conforme aplicável.  
  
4.  Defina o registro proposto para ser o registro atual.  
  
5.  Atualize qualquer índice associado.  
  
6.  Gerar `ListChanged` associadas de eventos para `DataView` objetos e `PropertyChanged` associadas de eventos para `DataRowView` objetos.  
  
7.  Avalie todas as colunas de expressão, mas o atraso de verificação de quaisquer restrições nessas colunas.  
  
8.  Gerar `ListChanged` associadas de eventos para `DataView` objetos e `PropertyChanged` associadas de eventos para `DataRowView` objetos afetados pela avaliações de coluna de expressão.  
  
9. Gerar `RowChanged` ou `RowDeleted` eventos conforme aplicável.  
  
10. Verificar restrições em colunas de expressão.  
  
> [!NOTE]
>  Alterações em colunas de expressão nunca geram `DataTable` eventos. Alterações em colunas de expressão só geram `DataView` e `DataRowView` eventos. Colunas de expressão pode ter dependências em várias outras colunas e podem ser avaliadas várias vezes durante uma única `DataRow` operação. Cada avaliação de expressão gera eventos e uma única `DataRow` operação pode gerar vários `ListChanged` e `PropertyChanged` eventos quando as colunas de expressão são afetadas, possivelmente incluindo vários eventos para a mesma coluna de expressão.  
  
> [!WARNING]
>  Não gerar um <xref:System.NullReferenceException> dentro de `RowChanged` manipulador de eventos. Se um <xref:System.NullReferenceException> é gerada dentro de `RowChanged` eventos de um `DataTable`, o `DataTable` serão corrompidos.  
  
### <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como criar manipuladores de eventos para o `RowChanged`, `RowChanging`, `RowDeleted`, `RowDeleting`, `ColumnChanged`, `ColumnChanging`, `TableNewRow`, `TableCleared`, e `TableClearing` eventos. Cada manipulador de eventos exibe a saída na janela do console quando ele é acionado.  
  
 [!code-csharp[DataWorks DataTable.Events#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.Events/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.Events#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.Events/VB/source.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Manipulação de dados em uma DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [Manipulação de eventos DataAdapter](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md)  
 [Handling DataSet Events](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md) (Manipulando eventos do DataSet)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
