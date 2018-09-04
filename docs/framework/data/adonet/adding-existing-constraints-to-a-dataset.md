---
title: Adicionando restrições existentes a um conjunto de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
ms.openlocfilehash: 90aa1e5dceb3cac87d330837496b9dc467dc1876
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43555466"
---
# <a name="adding-existing-constraints-to-a-dataset"></a>Adicionando restrições existentes a um conjunto de dados
O **preencher** método o **DataAdapter** preenche um <xref:System.Data.DataSet> somente com colunas de tabelas e linhas de uma fonte de dados; no entanto as restrições são geralmente definidas pela fonte de dados, o **preencher** método não adiciona essas informações de esquema para o **conjunto de dados** por padrão. Para preencher uma **DataSet** com informações de restrição de chave primária existente de uma fonte de dados, você pode chamar o **FillSchema** método da **DataAdapter**, ou defina o **MissingSchemaAction** propriedade da **DataAdapter** para **AddWithKey** antes de chamar **preencher**. Isso garantirá que a chave primária restrições na **conjunto de dados** refletem as na fonte de dados. Informações de restrição de chave estrangeira não está incluídas e devem ser criadas explicitamente, conforme mostrado na [restrições de DataTable](../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).  
  
 Adicionando informações de esquema para um **DataSet** antes de preenchê-lo com dados garante que as restrições de chave primária são incluídas com o <xref:System.Data.DataTable> objetos no **conjunto de dados**. Como resultado, quando adicionais chamadas para preencher a **conjunto de dados** forem feitas, o primário informações de coluna de chave são usadas para corresponder as novas linhas da fonte de dados com linhas atuais em cada **DataTable**e os dados atuais as tabelas serão substituídas pelos dados da fonte de dados. Sem as informações de esquema, as novas linhas da fonte de dados são acrescentadas à **conjunto de dados**, resultando em linhas duplicadas.  
  
> [!NOTE]
>  Se uma coluna em uma fonte de dados for identificada como incremento automático, o **FillSchema** método, ou o **preencher** método com um **MissingSchemaAction** de  **AddWithKey**, cria um **DataColumn** com um **AutoIncrement** propriedade definida como `true`. No entanto, você precisará definir a **AutoIncrementStep** e **AutoIncrementSeed** valores por conta própria. Para obter mais informações sobre colunas de incremento automático, consulte [criando colunas de incremento automático](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md).  
  
 Usando o **FillSchema** configuração ou o **MissingSchemaAction** para **AddWithKey** exige processamento extra na fonte de dados para determinar as informações de coluna de chave primária. Esse processamento adicional pode prejudicar o desempenho. Se você souber que as informações de chave primárias em tempo de design, é recomendável que você especifique explicitamente a coluna de chave primária ou colunas para alcançar um desempenho ideal. Para obter informações sobre como definir explicitamente as informações de chave primária para uma tabela, consulte [definindo chaves primárias](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
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
  
 O exemplo de código a seguir mostra como adicionar informações de esquema para um **DataSet** usando o **MissingSchemaAction.AddWithKey** propriedade do **preencher** método.  
  
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
 Se o **DataAdapter** encontra vários conjuntos de resultados retornados da **SelectCommand**, ele criará várias tabelas no **conjunto de dados**. As tabelas terá um nome padrão incremental com base em zero da **tabela** *N*, começando com **tabela** em vez de "Table0". Se um nome de tabela é passado como um argumento para o **FillSchema** método, as tabelas terá um nome incremental com base em zero da **TableName** *N*, começando com **TableName** em vez de "TableName0".  
  
> [!NOTE]
>  Se o **FillSchema** método o **OleDbDataAdapter** objeto é chamado para um comando que retorna vários conjuntos de resultados, somente as informações de esquema do primeiro conjunto de resultados serão retornadas. Quando, retornando informações de esquema de resultados múltiplos conjuntos usando o **OleDbDataAdapter**, é recomendável que você especifique uma **MissingSchemaAction** dos **AddWithKey** e obter as informações de esquema ao chamar o **preencher** método.  
  
## <a name="see-also"></a>Consulte também  
 [DataAdapters e DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [DataSets, DataTables, and DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 [Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)  
 [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
