---
title: Mapeamentos de DataTable e de DataColumn do DataAdapter
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e104ba75026c2ff387eb7c74b11c505e34085f41
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a>Mapeamentos de DataTable e de DataColumn do DataAdapter
Um **DataAdapter** contém uma coleção de zero ou mais <xref:System.Data.Common.DataTableMapping> objetos no seu **TableMappings** propriedade. Um **DataTableMapping** fornece um mapeamento mestre entre os dados retornados de uma consulta em relação a uma fonte de dados e um <xref:System.Data.DataTable>. O **DataTableMapping** nome pode ser passado em vez do **DataTable** nome para o **preencher** método o **DataAdapter**. O exemplo a seguir cria um **DataTableMapping** chamado **AuthorsMapping** para o **autores** tabela.  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 Um **DataTableMapping** permite que você use nomes de colunas em um **DataTable** que são diferentes no banco de dados. O **DataAdapter** usa o mapeamento para corresponder às colunas quando a tabela é atualizada.  
  
 Se você não especificar um **TableName** ou um **DataTableMapping** nome ao chamar o **preencher** ou **atualização** método o  **DataAdapter**, o **DataAdapter** procura um **DataTableMapping** chamado "Table". Se esse **DataTableMapping** não existir, o **TableName** do **DataTable** é "Table". Você pode especificar um padrão **DataTableMapping** criando um **DataTableMapping** com o nome de "Tabela".  
  
 O exemplo de código a seguir cria um **DataTableMapping** (da <xref:System.Data.Common> namespace) e torna o mapeamento padrão especificado **DataAdapter** nomeando-"Table". O exemplo, em seguida, mapeia as colunas da primeira tabela no resultado da consulta (o **clientes** tabela do **Northwind** banco de dados) para um conjunto de nomes mais amigáveis no **clientes do Northwind**  tabela o <xref:System.Data.DataSet>. Para colunas que não são mapeadas, o nome da coluna na fonte de dados é usado.  
  
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
  
 Em situações mais avançadas, você pode decidir que deseja que o mesmo **DataAdapter** para dar suporte ao carregamento de tabelas diferentes com diferentes mapeamentos. Para fazer isso, basta adicionar adicionais **DataTableMapping** objetos.  
  
 Quando o **preencher** é passado para uma instância de método um **DataSet** e um **DataTableMapping** nome, se existir um mapeamento com esse nome, ele é usado; caso contrário, um  **DataTable** com esse nome é usado.  
  
 Os exemplos a seguir criam um **DataTableMapping** com um nome de **clientes** e um **DataTable** nome de **BizTalkSchema**. O exemplo, em seguida, mapeia as linhas retornadas pela instrução SELECT para o **BizTalkSchema** **DataTable**.  
  
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
>  Se o nome de uma coluna de origem não for fornecido para um mapeamento de coluna ou se o nome de uma tabela de origem não for fornecido para um mapeamento de tabela, os nomes padrão serão gerados automaticamente. Se nenhuma coluna de origem é fornecida para um mapeamento de coluna, o mapeamento de coluna recebe um nome padrão incremental de **SourceColumn** *N,* começando com **SourceColumn1**. Se nenhum nome de tabela de origem é fornecido para um mapeamento de tabela, o mapeamento de tabela recebe um nome padrão incremental de **SourceTable** *N*, começando com **SourceTable1**.  
  
> [!NOTE]
>  É recomendável que você evite a convenção de nomenclatura de **SourceColumn** *N* para um mapeamento de coluna, ou **SourceTable** *N* para uma tabela mapeamento, porque o nome que você fornecer pode entrar em conflito com um nome de mapeamento de coluna padrão existente no **ColumnMappingCollection** ou nome de mapeamento de tabela no **DataTableMappingCollection** . Se o nome fornecido já existir, será gerada uma exceção.  
  
## <a name="handling-multiple-result-sets"></a>Manipulando vários conjuntos de resultados  
 Se seu **SelectCommand** retorna várias tabelas, **preencher** gera automaticamente os nomes de tabela com valores incrementais para as tabelas de **conjunto de dados**, começando com o especificado nome de tabela e continuar no formulário **TableName** *N*, começando com **TableName1**. Você pode usar os mapeamentos de tabela para mapear o nome da tabela gerada automaticamente para um nome especificado da tabela de **conjunto de dados**. Por exemplo, para um **SelectCommand** que retorna duas tabelas, **clientes** e **pedidos**, emita a seguinte chamada a **preencher**.  
  
```  
adapter.Fill(customersDataSet, "Customers")  
```  
  
 Duas tabelas são criadas no **DataSet**: **clientes** e **chamar Clientes1**. Você pode usar os mapeamentos de tabela para garantir que a segunda tabela é chamada **pedidos** em vez de **chamar Clientes1**. Para fazer isso, mapear a tabela de origem de **chamar Clientes1** para o **DataSet** tabela **pedidos**, conforme mostrado no exemplo a seguir.  
  
```  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  
  
## <a name="see-also"></a>Consulte também  
 [DataAdapters e DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
