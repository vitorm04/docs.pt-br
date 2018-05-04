---
title: Adicionando restrições existentes para um conjunto de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
ms.openlocfilehash: c3c28392a9e4bee0e2f9e0dcf553e13b67c378dd
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="adding-existing-constraints-to-a-dataset"></a>Adicionando restrições existentes para um conjunto de dados
O **preencher** método o **DataAdapter** preenche uma <xref:System.Data.DataSet> apenas com colunas de tabelas e linhas de uma fonte de dados; no entanto restrições mais frequentemente definidas pela fonte de dados, o **preencher** método não adicionar essas informações de esquema para o **DataSet** por padrão. Para popular um **DataSet** com informações de restrição de chave primária existente de uma fonte de dados, você pode chamar o **FillSchema** método do **DataAdapter**, ou defina o **MissingSchemaAction** propriedade o **DataAdapter** para **AddWithKey** antes de chamar **preencher**. Isso garantirá que a chave primária restrições no **DataSet** refletem aqueles na fonte de dados. Informações de restrição de chave estrangeira não está incluídas e devem ser criadas explicitamente, conforme mostrado no [restrições de DataTable](../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).  
  
 Adicionando informações de esquema para um **DataSet** para preenchê-lo com dados garante que as restrições de chave primária são incluídas com o <xref:System.Data.DataTable> objetos no **conjunto de dados**. Como resultado, quando adicionais chamadas para preencher o **DataSet** são feitas, o principal informações de coluna de chave são usadas para corresponder a novas linhas da fonte de dados com linhas atuais em cada **DataTable**e os dados atuais as tabelas é substituído por dados da fonte de dados. Sem as informações de esquema, as novas linhas da fonte de dados são anexadas ao **conjunto de dados**, resultando em linhas duplicadas.  
  
> [!NOTE]
>  Se uma coluna em uma fonte de dados for identificada como incremento automático, o **FillSchema** método, ou o **preencher** método com um **MissingSchemaAction** de  **AddWithKey**, cria um **DataColumn** com um **AutoIncrement** propriedade definida como `true`. No entanto, você precisará definir o **AutoIncrementStep** e **AutoIncrementSeed** valores por conta própria. Para obter mais informações sobre colunas de incremento automático, consulte [criar colunas de incremento automático](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md).  
  
 Usando **FillSchema** ou configuração de **MissingSchemaAction** para **AddWithKey** requer processamento extra na fonte de dados para determinar as informações de coluna de chave primária. Esse processamento adicional pode prejudicar o desempenho. Se você souber que as informações de chave primárias em tempo de design, é recomendável que você especificar explicitamente a coluna de chave primária ou colunas para alcançar um desempenho ideal. Para obter informações sobre como definir explicitamente as informações de chave primária para uma tabela, consulte [definindo chaves primárias](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
 O exemplo de código a seguir mostra como adicionar informações de esquema para um **DataSet** usando **FillSchema**.  
  
```vb  
Dim custDataSet As DataSet = New DataSet()  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers")  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
DataSet custDataSet = new DataSet();  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers");  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
 O exemplo de código a seguir mostra como adicionar informações de esquema para um **DataSet** usando o **MissingSchemaAction.AddWithKey** propriedade o **preencher** método.  
  
```vb  
Dim custDataSet As DataSet = New DataSet()  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
DataSet custDataSet = new DataSet();  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
## <a name="handling-multiple-result-sets"></a>Manipulando vários conjuntos de resultados  
 Se o **DataAdapter** encontra vários conjuntos de resultados retornados do **SelectCommand**, ele criará várias tabelas no **conjunto de dados**. As tabelas terá um nome de base zero padrão incremental **tabela** *N*, começando com **tabela** em vez de "Table0". Se um nome de tabela é passado como um argumento para o **FillSchema** método, as tabelas terá um nome incremental com base em zero do **TableName** *N*, começando com **TableName** em vez de "TableName0".  
  
> [!NOTE]
>  Se o **FillSchema** método o **OleDbDataAdapter** objeto é chamado para um comando que retorna vários conjuntos de resultados, somente as informações de esquema do primeiro conjunto de resultados serão retornadas. Quando retornando informações de esquema de resultados múltiplos conjuntos usando o **OleDbDataAdapter**, é recomendável que você especifique um **MissingSchemaAction** de **AddWithKey** e obter as informações de esquema ao chamar o **preencher** método.  
  
## <a name="see-also"></a>Consulte também  
 [DataAdapters e DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [DataSets, DataTables, and DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 [Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
