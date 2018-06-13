---
title: Exibindo dados em uma DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc
ms.openlocfilehash: 5d39d2a856a40b5ea20832a544ede360313309d3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761240"
---
# <a name="viewing-data-in-a-datatable"></a>Exibindo dados em uma DataTable
Você pode acessar o conteúdo de um <xref:System.Data.DataTable> usando o **linhas** e **colunas** coleções do **DataTable**. Você também pode usar o <xref:System.Data.DataTable.Select%2A> método para retornar subconjuntos de dados em um **DataTable** acordo com critérios inclusive critérios de pesquisa, ordem de classificação e o estado de linha. Além disso, você pode usar o <xref:System.Data.DataRowCollection.Find%2A> método o **DataRowCollection** durante a pesquisa de uma linha específica usando um valor de chave primária.  
  
 O **selecione** método o **DataTable** objeto retorna um conjunto de <xref:System.Data.DataRow> objetos que correspondem aos critérios especificados. **Selecione** leva argumentos opcionais de uma expressão de filtro, a expressão de classificação, e **DataViewRowState**. A expressão de filtro identifica quais linhas a serem retornadas com base em **DataColumn** valores, como `LastName = 'Smith'`. A expressão de classificação segue as convenções padrão de SQL para ordenar colunas, por exemplo `LastName ASC, FirstName ASC`. Para obter regras sobre como escrever expressões, consulte o <xref:System.Data.DataColumn.Expression%2A> propriedade o **DataColumn** classe.  
  
> [!TIP]
>  Se você estiver executando um número de chamadas para o **selecione** método de um **DataTable**, você pode aumentar o desempenho criando primeiro uma <xref:System.Data.DataView> para o **DataTable**. Criando o **DataView** indexa as linhas da tabela. O **selecione** método e usará o índice, reduzindo significativamente o tempo para gerar o resultado da consulta. Para obter informações sobre como criar um **DataView** para um **DataTable**, consulte [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).  
  
 O **selecione** método determina qual versão das linhas para exibir ou manipular com base em um <xref:System.Data.DataViewRowState>. A tabela a seguir descreve os possíveis **DataViewRowState** valores de enumeração.  
  
|Valor de DataViewRowState|Descrição|  
|----------------------------|-----------------|  
|**CurrentRows**|Linhas atuais, incluindo inalteradas, adicionadas e modificadas.|  
|**excluído**|Uma linha excluída.|  
|**ModifiedCurrent**|A versão atual, que é uma versão modificada dos dados originais. (Consulte **ModifiedOriginal**.)|  
|**ModifiedOriginal**|A versão original de todas as linhas alteradas. A versão atual está disponível com **ModifiedCurrent**.|  
|**Adicionado**|Uma nova linha.|  
|**Nenhum**|nenhuma.|  
|**OriginalRows**|Linhas originais, incluindo linhas inalteradas e excluídas.|  
|**Inalterado**|Uma linha inalterada.|  
  
 No exemplo a seguir, o **DataSet** objeto for filtrado para que você está apenas trabalhando com linhas cuja **DataViewRowState** é definido como **CurrentRows**.  
  
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
  
 O **selecione** método pode ser usado para retornar linhas com diferentes **RowState** valores ou valores de campo. O exemplo a seguir retorna um **DataRow** matriz que faz referência a todas as linhas que foram excluídas e retorna outro **DataRow** matriz que faz referência a todas as linhas, ordenados por **CustLName**, onde o **CustID** coluna é maior que 5. Para obter informações sobre como exibir as informações de **excluído** de linha, consulte [estados de linha e versões de linha](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
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
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
