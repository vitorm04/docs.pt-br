---
title: Adicionar restrições existentes a um DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
ms.openlocfilehash: 267d6489d39f86fc06b35de8cf30dad74f501b0b
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523242"
---
# <a name="adding-existing-constraints-to-a-dataset"></a>Adicionar restrições existentes a um DataSet

O método **Fill** do **DataAdapter** preenche uma <xref:System.Data.DataSet> somente com colunas e linhas de tabela de uma fonte de dados; Embora as restrições sejam normalmente definidas pela fonte de dados, o método **Fill** não adiciona essas informações de esquema ao **DataSet** por padrão. Para popular um **conjunto** de dados com informações de restrição de chave primária existentes de uma fonte, você pode chamar o método **FillSchema** do **DataAdapter**ou definir a propriedade **MissingSchemaAction** do **DataAdapter** para **AddWithKey** antes de chamar **Fill**. Isso garantirá que as restrições de chave primária no **DataSet** reflitam aquelas na fonte de dados. As informações de restrição de chave estrangeira não estão incluídas e devem ser criadas explicitamente, conforme mostrado em [restrições de DataTable](./dataset-datatable-dataview/datatable-constraints.md).  
  
A adição de informações de esquema a um **conjunto** de dados antes de preenchê-lo com o data garante que as restrições de chave primária sejam incluídas com os objetos de <xref:System.Data.DataTable> no **DataSet**. Como resultado, quando são feitas chamadas adicionais para preencher o **conjunto** de dados, as informações da coluna de chave primária são usadas para fazer a correspondência de novas linhas a partir da fonte com as linhas atuais em cada **DataTable**, e os dados atuais nas tabelas são substituídos pelos dados do fonte de dados. Sem as informações de esquema, as novas linhas da fonte de dados são acrescentadas ao **DataSet**, resultando em linhas duplicadas.  
  
> [!NOTE]
> Se uma coluna em uma fonte de dados for identificada como incrementação automática, o método **FillSchema** ou o método **Fill** com um **MissingSchemaAction** de **AddWithKey**, criará uma **DataColumn** com uma propriedade **AutoIncrement** Defina como `true`. No entanto, você precisará definir os valores **AutoIncrementStep** e **AutoIncrementSeed** por conta própria. Para obter mais informações sobre colunas de incrementação automática, consulte [criando colunas de incremento](./dataset-datatable-dataview/creating-autoincrement-columns.md)automático.  
  
O uso de **FillSchema** ou a definição de **MissingSchemaAction** como **AddWithKey** requer processamento extra na fonte de dados para determinar as informações da coluna de chave primária. Esse processamento adicional pode impedir o desempenho. Se você souber as informações de chave primária em tempo de design, recomendamos especificar explicitamente a coluna de chave primária ou as colunas para obter o desempenho ideal. Para obter informações sobre como definir explicitamente informações de chave primária para uma tabela, consulte [definindo chaves primárias](./dataset-datatable-dataview/defining-primary-keys.md).
  
O exemplo de código a seguir mostra como adicionar informações de esquema a um **conjunto** de dados usando **FillSchema**:
  
```vb  
Dim custDataSet As New DataSet()  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers")  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
var custDataSet = new DataSet();  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers");  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
O exemplo de código a seguir mostra como adicionar informações de esquema a um **conjunto** de dados usando a propriedade **MissingSchemaAction. AddWithKey** do método **Fill** :
  
```vb  
Dim custDataSet As New DataSet()  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
var custDataSet = new DataSet();  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
## <a name="handling-multiple-result-sets"></a>Manipulando vários conjuntos de resultados  

Se o **DataAdapter** encontrar vários conjuntos de resultados retornados do **SelectCommand**, ele criará várias tabelas no **conjunto**de linhas. As tabelas receberão um nome padrão incremental de base zero da **tabela** *N*, começando com a **tabela** em vez de "Table0". Se um nome de tabela for passado como um argumento para o método **FillSchema** , as tabelas receberão um nome incremental com base em zero de **TableName** *N*, começando com **TableName** em vez de "TableName0".  
  
> [!NOTE]
> Se o método **FillSchema** do objeto **OleDbDataAdapter** for chamado para um comando que retorna vários conjuntos de resultados, somente as informações de esquema do primeiro conjunto de resultados serão retornadas. Ao retornar informações de esquema para vários conjuntos de resultados usando o **OleDbDataAdapter**, é recomendável que você especifique um **MissingSchemaAction** de **AddWithKey** e obtenha as informações de esquema ao chamar o **preenchimento** forma.  
  
## <a name="see-also"></a>Consulte também

- [DataAdapters e DataReaders](dataadapters-and-datareaders.md)
- [DataSets, DataTables, and DataViews](./dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)
- [Retrieving and Modifying Data in ADO.NET](retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)
- [ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)
