---
title: Manipulação de eventos de DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62f404a5-13ea-4b93-a29f-55b74a16c9d3
ms.openlocfilehash: 210d15187cd539cdae6e38fdcb708b4b9f81c073
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988307"
---
# <a name="handling-datatable-events"></a>Manipulação de eventos de DataTable
O <xref:System.Data.DataTable> objeto fornece uma série de eventos que podem ser processados por um aplicativo. A tabela a seguir `DataTable` descreve os eventos.  
  
|evento|Descrição|  
|-----------|-----------------|  
|<xref:System.Data.DataTable.Initialized>|Ocorre depois que <xref:System.Data.DataTable.EndInit%2A> o método de `DataTable` um é chamado. Esse evento destina-se principalmente ao suporte a cenários de tempo de design.|  
|<xref:System.Data.DataTable.ColumnChanged>|Ocorre depois que um valor é alterado com êxito em um <xref:System.Data.DataColumn>.|  
|<xref:System.Data.DataTable.ColumnChanging>|Ocorre quando um valor é enviado para um `DataColumn`.|  
|<xref:System.Data.DataTable.RowChanged>|Ocorre depois que `DataColumn` um valor ou <xref:System.Data.DataRow.RowState%2A> o de <xref:System.Data.DataRow> um no `DataTable` foi alterado com êxito.|  
|<xref:System.Data.DataTable.RowChanging>|Ocorre quando uma alteração `DataColumn` é enviada para um valor ou o `RowState` de um `DataRow` no `DataTable`.|  
|<xref:System.Data.DataTable.RowDeleted>|Ocorre depois que `DataRow` um `DataTable` no é marcado como `Deleted`.|  
|<xref:System.Data.DataTable.RowDeleting>|Ocorre antes que `DataRow` um `DataTable` no seja marcado como `Deleted`.|  
|<xref:System.Data.DataTable.TableCleared>|Ocorre depois que uma chamada para <xref:System.Data.DataTable.Clear%2A> o método `DataTable` de foi limpa com êxito a `DataRow`cada.|  
|<xref:System.Data.DataTable.TableClearing>|Ocorre depois que `Clear` o método é chamado, mas `Clear` antes do início da operação.|  
|<xref:System.Data.DataTable.TableNewRow>|Ocorre depois que um `DataRow` novo é criado por uma chamada para `NewRow` o método do `DataTable`.|  
|<xref:System.ComponentModel.MarshalByValueComponent.Disposed>|Ocorre quando o `DataTable` é `Disposed`. Herdada de <xref:System.ComponentModel.MarshalByValueComponent>.|  
  
> [!NOTE]
> A maioria das operações que adicionam ou excluem linhas `ColumnChanged` não `ColumnChanging` geram os eventos e. No entanto `ReadXml` , o método `ColumnChanged` gera `ColumnChanging` `XmlReadMode` e eventos, a menos que seja `DiffGram` definido como ou seja `Auto` definido como quando o documento XML que está `DiffGram`sendo lido for um.  
  
> [!WARNING]
> Os dados corrompidos podem ocorrer se os dados são `DataSet` modificados em `RowChanged` um do qual o evento é gerado. Nenhuma exceção será gerada se ocorrer corrupção de dados.  
  
## <a name="additional-related-events"></a>Eventos relacionados adicionais  
 A <xref:System.Data.DataTable.Constraints%2A> propriedade contém uma <xref:System.Data.ConstraintCollection> instância. A <xref:System.Data.ConstraintCollection> classe expõe um <xref:System.Data.ConstraintCollection.CollectionChanged> evento. Esse evento é acionado quando uma restrição é adicionada, modificada ou removida do `ConstraintCollection`.  
  
 A <xref:System.Data.DataTable.Columns%2A> propriedade contém uma <xref:System.Data.DataColumnCollection> instância. A `DataColumnCollection` classe expõe um <xref:System.Data.DataColumnCollection.CollectionChanged> evento. Esse evento é acionado `DataColumn` quando um é adicionado, modificado ou removido `DataColumnCollection`do. As modificações que fazem com que o evento seja acionado incluem alterações no nome, tipo, expressão ou posição ordinal de uma coluna.  
  
 A <xref:System.Data.DataSet.Tables%2A> propriedade de um <xref:System.Data.DataSet> mantém uma <xref:System.Data.DataTableCollection> instância. A `DataTableCollection` classe expõe tanto um `CollectionChanged` quanto um `CollectionChanging` evento. Esses eventos são acionados `DataTable` quando um é adicionado ou removido `DataSet`do.  
  
 As alterações `DataRows` em também podem disparar eventos para um <xref:System.Data.DataView>associado. A `DataView` classe expõe um <xref:System.Data.DataView.ListChanged> evento que é acionado `DataColumn` quando um valor é alterado ou quando a ordem de composição ou de classificação da exibição é alterada. A <xref:System.Data.DataRowView> classe expõe um <xref:System.Data.DataRowView.PropertyChanged> evento que é acionado quando `DataColumn` um valor associado é alterado.  
  
## <a name="sequence-of-operations"></a>Sequência de operações  
 Aqui está a sequência de operações que ocorrem quando uma `DataRow` é adicionada, modificada ou excluída:  
  
1. Crie o registro proposto e aplique as alterações.  
  
2. Verifique as restrições de colunas que não são de expressão.  
  
3. Gere os `RowChanging` eventos `RowDeleting` ou conforme aplicável.  
  
4. Defina o registro proposto como o registro atual.  
  
5. Atualize todos os índices associados.  
  
6. Gerar `ListChanged` eventos para objetos `DataView` associados e `PropertyChanged` eventos para objetos `DataRowView` associados.  
  
7. Avalie todas as colunas de expressão, mas adie a verificação de qualquer restrição nessas colunas.  
  
8. Gerar `ListChanged` eventos para objetos `DataView` associados e `PropertyChanged` eventos para objetos `DataRowView` associados afetados pelas avaliações de coluna de expressão.  
  
9. Gerar `RowChanged` ou`RowDeleted` eventos conforme aplicável.  
  
10. Verifique as restrições nas colunas de expressão.  
  
> [!NOTE]
> As alterações nas colunas de expressão `DataTable` nunca geram eventos. As alterações nas colunas de expressão `DataView` geram e `DataRowView` apenas eventos. As colunas de expressão podem ter dependências em várias outras colunas e podem ser avaliadas várias vezes `DataRow` durante uma única operação. Cada avaliação de expressão gera eventos e uma única `DataRow` operação pode gerar vários `ListChanged` eventos `PropertyChanged` e quando as colunas de expressão são afetadas, possivelmente incluindo vários eventos para a mesma coluna de expressão.  
  
> [!WARNING]
> Não lance um <xref:System.NullReferenceException> dentro do manipulador `RowChanged` de eventos. Se um <xref:System.NullReferenceException> for lançado `RowChanged` no evento de a `DataTable`, o `DataTable` será corrompido.  
  
### <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como criar manipuladores de eventos para `RowChanged`os `RowChanging`eventos `RowDeleted`, `RowDeleting`, `ColumnChanged`, `ColumnChanging` `TableNewRow`,, `TableCleared`,, `TableClearing` e. Cada manipulador de eventos exibe a saída na janela do console quando ela é acionada.  
  
 [!code-csharp[DataWorks DataTable.Events#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.Events/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.Events#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.Events/VB/source.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- [Manipulação de dados em uma DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [Manipulação de eventos DataAdapter](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md)
- [Handling DataSet Events](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md) (Manipulando eventos do DataSet)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
