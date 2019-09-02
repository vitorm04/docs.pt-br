---
title: Copiando conteúdo do DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: f60ef817773b6234b19856bfc0727eedb67e113e
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205167"
---
# <a name="copying-dataset-contents"></a>Copiando conteúdo do DataSet
Você pode criar uma cópia de um <xref:System.Data.DataSet> para que você possa trabalhar com dados sem afetar os dados originais ou trabalhar com um subconjunto dos dados de um **DataSet**. Ao copiar um **conjunto**de um, você pode:  
  
- Crie uma cópia exata do **conjunto**de dados, incluindo o esquema, as informações de estado de linha e as versões de linha.  
  
- Crie um **conjunto** de registros que contenha o esquema de um **conjunto**de um existente, mas somente as linhas que foram modificadas. Você pode retornar todas as linhas que foram modificadas ou especificar um **DataRowState**específico. Para obter mais informações sobre Estados de linha, consulte [Estados de linha e versões de linha](row-states-and-row-versions.md).  
  
- Copie o esquema ou a estrutura relacional somente do **conjunto** de dados, sem copiar nenhuma linha. As linhas podem ser importadas em um <xref:System.Data.DataTable> existente usando o <xref:System.Data.DataTable.ImportRow%2A>.  
  
 Para criar uma cópia exata do **conjunto** de dados que inclui tanto o esquema quanto o dado <xref:System.Data.DataSet.Copy%2A> , use o método do **conjunto**. O exemplo de código a seguir mostra como criar uma cópia exata do **conjunto**de uma.  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 Para criar uma cópia de um **conjunto** de dados que inclui o esquema e apenaso dado que representa as linhas adicionadas, **modificadas**ou **excluídas** , use o <xref:System.Data.DataSet.GetChanges%2A> método do **DataSet**. Você também pode usar GetChanges para retornar apenas linhas com um estado de linha especificado, passando um valor de **DataRowState** ao chamar GetChanges. O exemplo de código a seguir mostra como passar um **DataRowState** aochamar GetChanges.  
  
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
  
 Para criar uma cópia de um **conjunto** de um DataSet que inclui apenas o <xref:System.Data.DataSet.Clone%2A> esquema, use o método do **conjunto**de um. Você também pode adicionar linhas existentes ao **conjunto** de registros clonado usando o método **ImportRow** da **DataTable**. **ImportRow** adiciona informações de dados, estado de linha e versão de linha à tabela especificada. Os valores de coluna são adicionados somente onde o nome da coluna corresponde e o tipo de dados é compatível.  
  
 O exemplo de código a seguir cria um clone de um conjunto de um **DataSet** e adiciona as linhas do **conjunto** de registros original à tabela **Customers** no clone do **conjunto** de um para clientes em que a coluna **CountryRegion** tem o valor "Alemanha ".  
  
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

- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [DataSets, DataTables, and DataViews](index.md) (DataSets, DataTables e DataViews)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
