---
title: Mapeamentos de DataTable e de DataColumn do DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.openlocfilehash: 357812aa95ea731fe86fbe49b2cb1b2806e3915a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784869"
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a>Mapeamentos de DataTable e de DataColumn do DataAdapter
Um **DataAdapter** contém uma coleção de zero ou mais <xref:System.Data.Common.DataTableMapping> objetos em sua propriedade **TableMappings** . Um **DataTableMapping** fornece um mapeamento mestre entre os dados retornados de uma consulta em relação a uma fonte de dados <xref:System.Data.DataTable>e um. O nome de **DataTableMapping** pode ser passado no lugar do nome **DataTable** para o método **Fill** do **DataAdapter**. O exemplo a seguir cria um **DataTableMapping** chamado **AuthorsMapping** para a tabela **Authors** .  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 Um **DataTableMapping** permite que você use nomes de coluna em uma **DataTable** que são diferentes daquelas no banco de dados. O **DataAdapter** usa o mapeamento para corresponder as colunas quando a tabela é atualizada.  
  
 Se você não especificar um nome de **tabela** ou de **DataTableMapping** ao chamar o método **Fill** ou **Update** do **DataAdapter**, o **DataAdapter** procurará um **DataTableMapping** chamado "Table". Se esse **DataTableMapping** não existir, o **TableName** da **DataTable** será "Table". Você pode especificar um **DataTableMapping** padrão criando um **DataTableMapping** com o nome "Table".  
  
 O exemplo de código a seguir cria um **DataTableMapping** ( <xref:System.Data.Common> do namespace) e o torna o mapeamento padrão para o **DataAdapter** especificado, nomeando-o como "Table". Em seguida, o exemplo mapeia as colunas da primeira tabela no resultado da consulta (a tabela **Customers** do banco de dados **Northwind** ) para um conjunto de nomes mais amigáveis na tabela <xref:System.Data.DataSet> **Customers da Northwind** no. Para colunas que não são mapeadas, o nome da coluna na fonte de dados é usado.  
  
```vb  
Dim mapping As DataTableMapping = _  
  adapter.TableMappings.Add("Table", "NorthwindCustomers")  
mapping.ColumnMappings.Add("CompanyName", "Company")  
mapping.ColumnMappings.Add("ContactName", "Contact")  
mapping.ColumnMappings.Add("PostalCode", "ZIPCode")  
  
adapter.Fill(custDS)  
```  
  
```csharp  
DataTableMapping mapping =   
  adapter.TableMappings.Add("Table", "NorthwindCustomers");  
mapping.ColumnMappings.Add("CompanyName", "Company");  
mapping.ColumnMappings.Add("ContactName", "Contact");  
mapping.ColumnMappings.Add("PostalCode", "ZIPCode");  
  
adapter.Fill(custDS);  
```  
  
 Em situações mais avançadas, você pode decidir que deseja que o mesmo **DataAdapter** dê suporte ao carregamento de tabelas diferentes com mapeamentos diferentes. Para fazer isso, basta adicionar outros objetos **DataTableMapping** .  
  
 Quando o método **Fill** passa uma instância de um conjunto de um **DataSet** e um nome **DataTableMapping** , se um mapeamento com esse nome já existir, ele será usado; caso contrário, será usada uma **DataTable** com esse nome.  
  
 Os exemplos a seguir criam um **DataTableMapping** com um nome de **Customers** e um nome **DataTable** de **BizTalkSchema**. Em seguida, o exemplo mapeia as linhas retornadas pela instrução SELECT para a **DataTable** **BizTalkSchema** .  
  
```vb  
Dim mapping As ITableMapping = _  
  adapter.TableMappings.Add("Customers", "BizTalkSchema")  
mapping.ColumnMappings.Add("CustomerID", "ClientID")  
mapping.ColumnMappings.Add("CompanyName", "ClientName")  
mapping.ColumnMappings.Add("ContactName", "Contact")  
mapping.ColumnMappings.Add("PostalCode", "ZIP")  
  
adapter.Fill(custDS, "Customers")  
```  
  
```csharp  
ITableMapping mapping =   
  adapter.TableMappings.Add("Customers", "BizTalkSchema");  
mapping.ColumnMappings.Add("CustomerID", "ClientID");  
mapping.ColumnMappings.Add("CompanyName", "ClientName");  
mapping.ColumnMappings.Add("ContactName", "Contact");  
mapping.ColumnMappings.Add("PostalCode", "ZIP");  
  
adapter.Fill(custDS, "Customers");  
```  
  
> [!NOTE]
> Se o nome de uma coluna de origem não for fornecido para um mapeamento de coluna ou se o nome de uma tabela de origem não for fornecido para um mapeamento de tabela, os nomes padrão serão gerados automaticamente. Se nenhuma coluna de origem for fornecida para um mapeamento de coluna, o mapeamento de coluna receberá um nome padrão incremental de **SourceColumn** *N,* começando com **SourceColumn1**. Se nenhum nome de tabela de origem for fornecido para um mapeamento de tabela, o mapeamento de tabela receberá um nome padrão incremental de **SourceTable** *N*, começando com **SourceTable1**.  
  
> [!NOTE]
> Recomendamos que você evite a Convenção de nomenclatura de **SourceColumn** *N* para um mapeamento de coluna ou **SourceTable** *n* para um mapeamento de tabela, pois o nome que você fornece pode entrar em conflito com um nome de mapeamento de coluna padrão existente no  **ColumnMappingcollection** ou nome de mapeamento de tabela no **DataTableMappingCollection**. Se o nome fornecido já existir, será gerada uma exceção.  
  
## <a name="handling-multiple-result-sets"></a>Manipulando vários conjuntos de resultados  
 Se o **SelectCommand** retornar várias tabelas, **Fill** gerará automaticamente nomes de tabela com valores incrementais para as tabelas no **conjunto**de valores, começando com o nome da tabela especificada e continuando no formato **TableName** *N*, começando com **TableName1**. Você pode usar mapeamentos de tabela para mapear o nome de tabela gerado automaticamente para um nome que você deseja especificar para a tabela no **DataSet**. Por exemplo, para um **SelectCommand** que retorna duas tabelas, **Customers** e **Orders**, emita a seguinte chamada para **Fill**.  
  
```  
adapter.Fill(customersDataSet, "Customers")  
```  
  
 Duas tabelas são criadas no **conjunto de conjuntos**: **Clientes** e **Customers1**. Você pode usar mapeamentos de tabela para garantir que a segunda tabela seja denominada **Orders** em vez de **Customers1**. Para fazer isso, mapeie a tabela de origem de **Customers1** para os **pedidos**de tabela de **conjunto** de tabelas, conforme mostrado no exemplo a seguir.  
  
```  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  
  
## <a name="see-also"></a>Consulte também

- [DataAdapters e DataReaders](dataadapters-and-datareaders.md)
- [Retrieving and Modifying Data in ADO.NET](retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)
- [ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)
