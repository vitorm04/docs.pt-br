---
title: Copiando conteúdo do DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: de13e07eb5c19b8beffa724fec4a128c418a4fed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151358"
---
# <a name="copying-dataset-contents"></a>Copiando conteúdo do DataSet
Você pode criar uma <xref:System.Data.DataSet> cópia de um para que você possa trabalhar com dados sem afetar os dados originais ou trabalhar com um subconjunto dos dados de um **DataSet**. Ao copiar um **Conjunto de Dados,** você pode:  
  
- Crie uma cópia exata do Conjunto de **Dados**, incluindo o esquema, dados, informações do estado de linha e versões de linha.  
  
- Crie um **Conjunto de Dados** que contenha o esquema de um Conjunto de **Dados**existente, mas apenas linhas que foram modificadas. Você pode retornar todas as linhas que foram modificadas ou especificar um **DataRowState**específico . Para obter mais informações sobre estados de linha, consulte [Estados de linha e versões de linha](row-states-and-row-versions.md).  
  
- Copie apenas o esquema, ou estrutura relacional, do **DataSet,** sem copiar nenhuma linha. As linhas podem ser importadas em um <xref:System.Data.DataTable> existente usando o <xref:System.Data.DataTable.ImportRow%2A>.  
  
 Para criar uma cópia exata do Conjunto de **Dados** que inclui <xref:System.Data.DataSet.Copy%2A> esquema e dados, use o método do **DataSet**. O exemplo de código a seguir mostra como criar uma cópia exata do Conjunto de **Dados**.  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 Para criar uma cópia de um Conjunto de **Dados** que inclua esquema e apenas os dados <xref:System.Data.DataSet.GetChanges%2A> que representam linhas **adicionadas,** **modificadas**ou **excluídas,** use o método do Conjunto de **Dados**. Você também pode usar **GetChanges** para retornar apenas linhas com um estado de linha especificado, passando um valor **DataRowState** ao chamar **GetChanges**. O exemplo de código a seguir mostra como passar um **DataRowState** ao chamar **GetChanges**.  
  
```vb  
' Copy all changes.  
Dim changeDataSet As DataSet = customerDataSet.GetChanges()  
' Copy only new rows.  
Dim addedDataSetAs DataSet = _  
    customerDataSet.GetChanges(DataRowState.Added)  
```  
  
```csharp  
// Copy all changes.  
DataSet changeDataSet = customerDataSet.GetChanges();  
// Copy only new rows.  
DataSet addedDataSet= customerDataSet.GetChanges(DataRowState.Added);  
```  
  
 Para criar uma cópia de um Conjunto de **Dados** <xref:System.Data.DataSet.Clone%2A> que inclua apenas esquema, use o método do **DataSet**. Você também pode adicionar linhas existentes ao **Conjunto de Dados** clonado usando o método **ImportRow** da Tabela de **Dados**. **ImportRow** adiciona dados, informações de estado de linha e versão de linha à tabela especificada. Os valores de coluna são adicionados somente onde o nome da coluna corresponde e o tipo de dados é compatível.  
  
 O exemplo de código a seguir cria um clone de um **DataSet** e, em seguida, adiciona as linhas do **Conjunto** de Dados original à tabela **Clientes** no clone **DataSet** para clientes onde a coluna **CountryRegion** tem o valor "Alemanha".  
  
```vb  
Dim customerDataSet As New DataSet  
        customerDataSet.Tables.Add(New DataTable("Customers"))  
        customerDataSet.Tables("Customers").Columns.Add("Name", GetType(String))  
        customerDataSet.Tables("Customers").Columns.Add("CountryRegion", GetType(String))  
        customerDataSet.Tables("Customers").Rows.Add("Juan", "Spain")  
        customerDataSet.Tables("Customers").Rows.Add("Johann", "Germany")  
        customerDataSet.Tables("Customers").Rows.Add("John", "UK")  
  
Dim germanyCustomers As DataSet = customerDataSet.Clone()  
  
Dim copyRows() As DataRow = _  
  customerDataSet.Tables("Customers").Select("CountryRegion = 'Germany'")  
  
Dim customerTable As DataTable = germanyCustomers.Tables("Customers")  
Dim copyRow As DataRow  
  
For Each copyRow In copyRows  
  customerTable.ImportRow(copyRow)  
Next  
```  
  
```csharp  
DataSet customerDataSet = new DataSet();  
customerDataSet.Tables.Add(new DataTable("Customers"));  
customerDataSet.Tables["Customers"].Columns.Add("Name", typeof(string));  
customerDataSet.Tables["Customers"].Columns.Add("CountryRegion", typeof(string));  
customerDataSet.Tables["Customers"].Rows.Add("Juan", "Spain");  
customerDataSet.Tables["Customers"].Rows.Add("Johann", "Germany");  
customerDataSet.Tables["Customers"].Rows.Add("John", "UK");  
  
DataSet germanyCustomers = customerDataSet.Clone();  
  
DataRow[] copyRows =
  customerDataSet.Tables["Customers"].Select("CountryRegion = 'Germany'");  
  
DataTable customerTable = germanyCustomers.Tables["Customers"];  
  
foreach (DataRow copyRow in copyRows)  
  customerTable.ImportRow(copyRow);  
```  
  
## <a name="see-also"></a>Confira também

- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [DataSets, DataTables e DataViews](index.md)
- [Visão geral do ADO.NET](../ado-net-overview.md)
