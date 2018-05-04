---
title: Copiando conteúdo do DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: bee91a6406fd48894580ce6223a5682dbadab380
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="copying-dataset-contents"></a>Copiando conteúdo do DataSet
Você pode criar uma cópia de um <xref:System.Data.DataSet> para que você possa trabalhar com dados sem afetar os dados originais ou trabalhar com um subconjunto dos dados de um **conjunto de dados**. Ao copiar um **conjunto de dados**, você pode:  
  
-   Criar uma cópia exata do **conjunto de dados**, incluindo o esquema, dados, informações de estado de linha e versões de linha.  
  
-   Criar um **DataSet** que contém o esquema de um objeto existente **conjunto de dados**, mas somente as linhas que foram modificadas. Você pode retornar todas as linhas que foram modificadas, ou especificar um determinado **DataRowState**. Para obter mais informações sobre estados de linha, consulte [estados de linha e versões de linha](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
-   Copie o esquema, ou estrutura relacional, do **DataSet** somente, sem copiar linhas. As linhas podem ser importadas em um <xref:System.Data.DataTable> existente usando o <xref:System.Data.DataTable.ImportRow%2A>.  
  
 Para criar uma cópia exata do **DataSet** que inclui o esquema e os dados, use o <xref:System.Data.DataSet.Copy%2A> método o **conjunto de dados**. O exemplo de código a seguir mostra como criar uma cópia exata do **conjunto de dados**.  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 Para criar uma cópia de um **DataSet** que inclui o esquema e apenas os dados que representa **adicionado**, **modificadas**, ou **excluído** linhas, use o <xref:System.Data.DataSet.GetChanges%2A> método o **conjunto de dados**. Você também pode usar **GetChanges** para retornar apenas as linhas com um estado de linha especificada, passando um **DataRowState** valor ao chamar **GetChanges**. O exemplo de código a seguir mostra como passar um **DataRowState** ao chamar **GetChanges**.  
  
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
  
 Para criar uma cópia de um **conjunto de dados** que inclui somente esquema, use o <xref:System.Data.DataSet.Clone%2A> método o **conjunto de dados**. Você também pode adicionar linhas existentes para o clonado **DataSet** usando o **ImportRow** método o **DataTable**. **ImportRow** adiciona dados, o estado de linha e informações de versão de linha à tabela especificada. Os valores de coluna são adicionados somente onde o nome da coluna corresponde e o tipo de dados é compatível.  
  
 O exemplo de código a seguir cria um clone de um **DataSet** e, em seguida, adiciona as linhas do original **DataSet** para o **clientes** tabela o **conjunto de dados**  clone para clientes onde o **CountryRegion** coluna tem o valor "Germany".  
  
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
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 [DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
