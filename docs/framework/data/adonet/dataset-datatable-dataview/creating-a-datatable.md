---
title: Criando uma DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
ms.openlocfilehash: ad3f8bc6b42c5a54b42100a5d010e097ba80adc2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43386907"
---
# <a name="creating-a-datatable"></a>Criando uma DataTable
Uma <xref:System.Data.DataTable>, que representa uma tabela de dados relacionais de memória, pode ser criada e usada independentemente ou pode ser usada por outros objetos do .NET Framework, mais comumente como membro de um <xref:System.Data.DataSet>.  
  
 Você pode criar uma **DataTable** objeto com o uso apropriado **DataTable** construtor. Você pode adicioná-lo para o **conjunto de dados** usando o **Add** método para adicioná-lo para o **DataTable** do objeto **tabelas** coleção.  
  
 Você também pode criar **DataTable** objetos dentro de uma **conjunto de dados** usando o **preencher** ou **FillSchema** métodos do  **DataAdapter** objeto, ou em uma predefinido ou inferido XML esquema usando o **ReadXml**, **ReadXmlSchema**, ou **InferXmlSchema** métodos do **conjunto de dados**. Observe que, depois de ter adicionado uma **DataTable** como um membro do **tabelas** coleção de um **conjunto de dados**, você não pode adicioná-lo à coleção de tabelas de quaisquer outros **Conjunto de dados**.  
  
 Quando você cria primeiro um **DataTable**, ele não tem um esquema (ou seja, uma estrutura). Para definir o esquema da tabela, você deve criar e adicionar <xref:System.Data.DataColumn> objetos para o **colunas** coleção da tabela. Você também pode definir uma coluna de chave primária para a tabela e criar e adicionar **restrição** objetos para o **restrições** coleção da tabela. Depois de definir o esquema para um **DataTable**, você pode adicionar linhas de dados à tabela adicionando **DataRow** objetos para o **linhas** coleção da tabela.  
  
 Não é necessário fornecer um valor para o <xref:System.Data.DataTable.TableName%2A> propriedade quando você cria um **DataTable**; você pode especificar a propriedade em outro momento, ou você pode deixá-lo vazio. No entanto, quando você adiciona uma tabela sem um **TableName** valor para um **DataSet**, a tabela terá um nome padrão incremental da tabela*N*, começando com "Table" para Table0.  
  
> [!NOTE]
>  É recomendável que você evite a "tabela*N*" convenção de nomenclatura ao fornecer um **TableName** valor, porque o nome fornecido pode entrar em conflito com um nome de tabela padrão existente no **conjunto de dados** . Se o nome fornecido já existir, será gerada uma exceção.  
  
 O exemplo a seguir cria uma instância de um **DataTable** do objeto e atribui a ele o nome "Customers".  
  
```vb  
Dim workTable as DataTable = New DataTable("Customers")  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
```  
  
 O exemplo a seguir cria uma instância de um **DataTable** adicionando-o para o **tabelas** coleção de um **conjunto de dados**.  
  
```vb  
Dim customers As DataSet = New DataSet  
Dim customersTable As DataTable = _  
   customers.Tables.Add("CustomersTable")  
```  
  
```csharp  
DataSet customers = new DataSet();  
DataTable customersTable = customers.Tables.Add("CustomersTable");  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataTableCollection>  
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [Populating a DataSet from a DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md) (Preenchendo um DataSet por meio de um DataAdapter)  
 [Carregar um conjunto de dados do XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Carregando informações de esquema de conjunto de dados de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
