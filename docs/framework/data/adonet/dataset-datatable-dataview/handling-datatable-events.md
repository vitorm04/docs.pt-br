---
title: Manipulação de eventos de DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62f404a5-13ea-4b93-a29f-55b74a16c9d3
ms.openlocfilehash: ef9fcd31253283248dfe773ac4dde4fcbb358a2c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660977"
---
# <a name="handling-datatable-events"></a>Manipulação de eventos de DataTable
O <xref:System.Data.DataTable> objeto fornece uma série de eventos que podem ser processadas por um aplicativo. A tabela a seguir descreve `DataTable` eventos.  
  
|evento|Descrição|  
|-----------|-----------------|  
|<xref:System.Data.DataTable.Initialized>|Ocorre após o <xref:System.Data.DataTable.EndInit%2A> método de um `DataTable` é chamado. Esse evento destina-se principalmente para dar suporte a cenários de tempo de design.|  
|<xref:System.Data.DataTable.ColumnChanged>|Ocorre depois que um valor foi alterado com êxito em um <xref:System.Data.DataColumn>.|  
|<xref:System.Data.DataTable.ColumnChanging>|Ocorre quando um valor tiver sido enviado para um `DataColumn`.|  
|<xref:System.Data.DataTable.RowChanged>|Ocorre após um `DataColumn` valor ou o <xref:System.Data.DataRow.RowState%2A> de uma <xref:System.Data.DataRow> no `DataTable` foi alterada com êxito.|  
|<xref:System.Data.DataTable.RowChanging>|Ocorre quando uma alteração é enviada para um `DataColumn` valor ou o `RowState` de uma `DataRow` no `DataTable`.|  
|<xref:System.Data.DataTable.RowDeleted>|Ocorre após um `DataRow` no `DataTable` tiver sido marcada como `Deleted`.|  
|<xref:System.Data.DataTable.RowDeleting>|Ocorre antes de uma `DataRow` no `DataTable` está marcado como `Deleted`.|  
|<xref:System.Data.DataTable.TableCleared>|Ocorre após uma chamada para o <xref:System.Data.DataTable.Clear%2A> método da `DataTable` foi limpo com êxito cada `DataRow`.|  
|<xref:System.Data.DataTable.TableClearing>|Ocorre após o `Clear` método é chamado, mas antes de `Clear` início da operação.|  
|<xref:System.Data.DataTable.TableNewRow>|Ocorre depois que um novo `DataRow` é criado por uma chamada para o `NewRow` método o `DataTable`.|  
|<xref:System.ComponentModel.MarshalByValueComponent.Disposed>|Ocorre quando o `DataTable` é `Disposed`. Herdada de <xref:System.ComponentModel.MarshalByValueComponent>.|  
  
> [!NOTE]
>  A maioria das operações que adicionam ou excluem linhas não acionar o `ColumnChanged` e `ColumnChanging` eventos. No entanto, o `ReadXml` método disparar `ColumnChanged` e `ColumnChanging` eventos, a menos que o `XmlReadMode` é definido como `DiffGram` ou estiver definido como `Auto` quando o documento XML que está sendo lido estiver um `DiffGram`.  
  
> [!WARNING]
>  Corrupção de dados pode ocorrer se os dados são modificados em um `DataSet` do qual o `RowChanged` é gerado. Nenhuma exceção será gerada se ocorrer essa corrupção de dados.  
  
## <a name="additional-related-events"></a>Outros eventos relacionados  
 O <xref:System.Data.DataTable.Constraints%2A> propriedade mantém um <xref:System.Data.ConstraintCollection> instância. O <xref:System.Data.ConstraintCollection> classe expõe um <xref:System.Data.ConstraintCollection.CollectionChanged> eventos. Esse evento é acionado quando uma restrição é adicionada, modificada ou removida do `ConstraintCollection`.  
  
 O <xref:System.Data.DataTable.Columns%2A> propriedade mantém um <xref:System.Data.DataColumnCollection> instância. O `DataColumnCollection` classe expõe um <xref:System.Data.DataColumnCollection.CollectionChanged> eventos. Esse evento é acionado quando um `DataColumn` é adicionado, modificado ou removido do `DataColumnCollection`. As modificações que fazem com que o evento seja acionado incluem alterações para o nome, o tipo, a expressão ou a posição ordinal de uma coluna.  
  
 O <xref:System.Data.DataSet.Tables%2A> propriedade de um <xref:System.Data.DataSet> mantém um <xref:System.Data.DataTableCollection> instância. O `DataTableCollection` classe exponha uma `CollectionChanged` e um `CollectionChanging` eventos. Esses eventos são acionados quando um `DataTable` é adicionado ou removido do `DataSet`.  
  
 Muda para `DataRows` também pode disparar eventos para um tipo de <xref:System.Data.DataView>. O `DataView` classe expõe um <xref:System.Data.DataView.ListChanged> evento acionado quando um `DataColumn` alterações de valor ou quando a ordem de composição ou classificação da exibição é alterada. O <xref:System.Data.DataRowView> classe expõe um <xref:System.Data.DataRowView.PropertyChanged> que é acionado quando um tipo de evento `DataColumn` o valor é alterado.  
  
## <a name="sequence-of-operations"></a>Sequência de operações  
 Aqui está a sequência de operações que ocorrem quando um `DataRow` é adicionado, modificado ou excluído:  
  
1.  Criar o registro de proposta e aplicar as alterações.  
  
2.  Verificar restrições para colunas não-expression.  
  
3.  Gerar a `RowChanging` ou `RowDeleting` eventos conforme aplicável.  
  
4.  Defina o registro proposto para ser o registro atual.  
  
5.  Atualize qualquer índice associado.  
  
6.  Gerar `ListChanged` eventos para associados `DataView` objetos e `PropertyChanged` associadas de eventos para `DataRowView` objetos.  
  
7.  Avalie todas as colunas de expressão, mas o atraso, verificando a quaisquer restrições nessas colunas.  
  
8.  Elevar `ListChanged` eventos associados `DataView` objetos e `PropertyChanged` associadas de eventos para `DataRowView` objetos afetados pelas avaliações de coluna de expressão.  
  
9. Elevar `RowChanged` ou `RowDeleted` eventos conforme aplicável.  
  
10. Verificar restrições em colunas de expressão.  
  
> [!NOTE]
>  Alterações em colunas de expressão nunca geram `DataTable` eventos. Alterações em colunas de expressão apenas geram `DataView` e `DataRowView` eventos. Colunas de expressão pode ter dependências em várias outras colunas e pode ser avaliadas várias vezes durante uma única `DataRow` operação. Cada avaliação de expressão gera eventos e um único `DataRow` operação pode gerar vários `ListChanged` e `PropertyChanged` eventos quando colunas de expressão são afetadas, possivelmente incluindo vários eventos para a mesma coluna de expressão.  
  
> [!WARNING]
>  Não lance uma <xref:System.NullReferenceException> dentro de `RowChanged` manipulador de eventos. Se um <xref:System.NullReferenceException> é gerada dentro a `RowChanged` eventos de um `DataTable`, em seguida, a `DataTable` serão corrompidos.  
  
### <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como criar manipuladores de eventos para o `RowChanged`, `RowChanging`, `RowDeleted`, `RowDeleting`, `ColumnChanged`, `ColumnChanging`, `TableNewRow`, `TableCleared`, e `TableClearing` eventos. Cada manipulador de eventos exibe a saída na janela do console quando ele é acionado.  
  
 [!code-csharp[DataWorks DataTable.Events#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.Events/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.Events#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.Events/VB/source.vb#1)]  
  
## <a name="see-also"></a>Consulte também
- [Manipulação de dados em uma DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [Manipulação de eventos DataAdapter](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md)
- [Handling DataSet Events](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md) (Manipulando eventos do DataSet)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
