---
title: Exibindo dados em uma DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc
ms.openlocfilehash: de745633060dd4f7b1610492d0ff57ec7a4f545b
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44202135"
---
# <a name="viewing-data-in-a-datatable"></a>Exibindo dados em uma DataTable
Você pode acessar o conteúdo de um <xref:System.Data.DataTable> usando o **linhas** e **colunas** coleções do **DataTable**. Você também pode usar o <xref:System.Data.DataTable.Select%2A> método para retornar subconjuntos de dados em um **DataTable** acordo com critérios, incluindo os critérios de pesquisa, ordem de classificação e estado de linha. Além disso, você pode usar o <xref:System.Data.DataRowCollection.Find%2A> método da **DataRowCollection** ao pesquisar por uma linha específica usando um valor de chave primária.  
  
 O **selecionar** método o **DataTable** objeto retorna um conjunto de <xref:System.Data.DataRow> objetos que correspondem aos critérios especificados. **Selecione** utiliza argumentos opcionais de uma expressão de filtro, expressão de classificação, e **DataViewRowState**. A expressão de filtro que identifica quais linhas retornar com base nos **DataColumn** valores, como `LastName = 'Smith'`. A expressão de classificação segue as convenções padrão de SQL para ordenar colunas, por exemplo `LastName ASC, FirstName ASC`. Para obter regras sobre como escrever expressões, consulte o <xref:System.Data.DataColumn.Expression%2A> propriedade do **DataColumn** classe.  
  
> [!TIP]
>  Se você estiver executando um número de chamadas para o **selecionar** método de um **DataTable**, você pode aumentar o desempenho criando primeiro uma <xref:System.Data.DataView> para o **DataTable**. Criando o **DataView** indexa as linhas da tabela. O **selecionar** método e em seguida, usa esse índice, reduzindo significativamente o tempo para gerar o resultado da consulta. Para obter informações sobre como criar uma **DataView** para um **DataTable**, consulte [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).  
  
 O **selecionar** método determina qual versão das linhas para exibir ou manipular com base em um <xref:System.Data.DataViewRowState>. A tabela a seguir descreve os possíveis **DataViewRowState** valores de enumeração.  
  
|Valor de DataViewRowState|Descrição|  
|----------------------------|-----------------|  
|**CurrentRows**|Linhas atuais, incluindo inalteradas, adicionadas e modificadas.|  
|**Excluído**|Uma linha excluída.|  
|**ModifiedCurrent**|A versão atual, que é uma versão modificada dos dados originais. (Consulte **ModifiedOriginal**.)|  
|**ModifiedOriginal**|A versão original de todas as linhas alteradas. A versão atual está disponível com **ModifiedCurrent**.|  
|**Adicionado**|Uma nova linha.|  
|**Nenhum**|nenhuma.|  
|**OriginalRows**|Linhas originais, incluindo linhas inalteradas e excluídas.|  
|**inalterado**|Uma linha inalterada.|  
  
 No exemplo a seguir, o **DataSet** o objeto é filtrado para que você só trabalha com linhas cuja **DataViewRowState** está definido como **CurrentRows**.  
  
```vb  
Dim column As DataColumn  
Dim row As DataRow  
  
Dim currentRows() As DataRow = _  
    workTable.Select(Nothing, Nothing, DataViewRowState.CurrentRows)  
  
If (currentRows.Length < 1 ) Then  
  Console.WriteLine("No Current Rows Found")  
Else  
  For Each column in workTable.Columns  
    Console.Write(vbTab & column.ColumnName)  
  Next  
  
  Console.WriteLine(vbTab & "RowState")  
  
  For Each row In currentRows  
    For Each column In workTable.Columns  
      Console.Write(vbTab & row(column).ToString())  
    Next  
  
    Dim rowState As String = _  
        System.Enum.GetName(row.RowState.GetType(), row.RowState)  
    Console.WriteLine(vbTab & rowState)  
  Next  
End If  
```  
  
```csharp  
DataRow[] currentRows = workTable.Select(  
    null, null, DataViewRowState.CurrentRows);  
  
if (currentRows.Length < 1 )  
  Console.WriteLine("No Current Rows Found");  
else  
{  
  foreach (DataColumn column in workTable.Columns)  
    Console.Write("\t{0}", column.ColumnName);  
  
  Console.WriteLine("\tRowState");  
  
  foreach (DataRow row in currentRows)  
  {  
    foreach (DataColumn column in workTable.Columns)  
      Console.Write("\t{0}", row[column]);  
  
    Console.WriteLine("\t" + row.RowState);  
  }  
}  
```  
  
 O **selecionar** método pode ser usado para retornar linhas com diferentes **RowState** valores ou valores de campo. O exemplo a seguir retorna uma **DataRow** que faz referência a todas as linhas que foram excluídas e retorna outra matriz **DataRow** matriz que faz referência a todas as linhas, ordenadas por **CustLName**, em que o **CustID** coluna é maior que 5. Para obter informações sobre como exibir as informações de **Deleted** linha, consulte [estados de linha e versões de linha](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
```vb  
' Retrieve all deleted rows.  
Dim deletedRows() As DataRow = workTable.Select(Nothing, Nothing, DataViewRowState.Deleted)  
  
' Retrieve rows where CustID > 5, and order by CustLName.  
Dim custRows() As DataRow = workTable.Select( _  
    "CustID > 5", "CustLName ASC")  
```  
  
```csharp  
// Retrieve all deleted rows.  
DataRow[] deletedRows = workTable.Select(  
    null, null, DataViewRowState.Deleted);  
  
// Retrieve rows where CustID > 5, and order by CustLName.  
DataRow[] custRows = workTable.Select("CustID > 5", "CustLName ASC");  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataViewRowState>  
 [Manipulação de dados em uma DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [Estados e versões de linha](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
