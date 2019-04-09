---
title: Mapeamentos de DataTable e de DataColumn do DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.openlocfilehash: 54af7c2f449f8eb289841fb3eca357c6916404aa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201202"
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a>Mapeamentos de DataTable e de DataColumn do DataAdapter
Um **DataAdapter** contém uma coleção de zero ou mais <xref:System.Data.Common.DataTableMapping> objetos no seu **TableMappings** propriedade. Um **DataTableMapping** fornece um mapeamento mestre entre os dados retornados de uma consulta em relação a uma fonte de dados e um <xref:System.Data.DataTable>. O **DataTableMapping** nome pode ser passado em vez da **DataTable** nome para o **preencher** o método da **DataAdapter**. O exemplo a seguir cria uma **DataTableMapping** denominado **AuthorsMapping** para o **autores** tabela.  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 Um **DataTableMapping** permite que você use nomes de coluna em uma **DataTable** que são diferentes no banco de dados. O **DataAdapter** usa o mapeamento para corresponder às colunas quando a tabela é atualizada.  
  
 Se você não especificar uma **TableName** ou um **DataTableMapping** nome ao chamar o **preencher** ou **atualização** método o  **DataAdapter**, o **DataAdapter** procura uma **DataTableMapping** chamado "Table". Se esse **DataTableMapping** não existir, o **TableName** dos **DataTable** será "Table". Você pode especificar um padrão **DataTableMapping** criando um **DataTableMapping** com o nome de "Table".  
  
 O exemplo de código a seguir cria uma **DataTableMapping** (da <xref:System.Data.Common> namespace) e torna o mapeamento padrão para especificado **DataAdapter** ao nomeá-lo "Table". O exemplo, em seguida, mapeia as colunas da primeira tabela no resultado da consulta (o **clientes** tabela da **Northwind** banco de dados) para um conjunto de nomes mais amigáveis no **clientes Northwind**  na tabela a <xref:System.Data.DataSet>. Para colunas que não são mapeadas, o nome da coluna na fonte de dados é usado.  
  
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
  
 Em situações mais avançadas, você pode decidir que deseja que o mesmo **DataAdapter** para dar suporte ao carregamento de diferentes tabelas com diferentes mapeamentos. Para fazer isso, basta adicionar mais **DataTableMapping** objetos.  
  
 Quando o **preencher** método recebe uma instância de um **DataSet** e um **DataTableMapping** nome, se existir um mapeamento com esse nome, ele é usado; caso contrário, um  **DataTable** com esse nome é usado.  
  
 Os exemplos a seguir criam uma **DataTableMapping** com um nome de **clientes** e um **DataTable** nome do **BizTalkSchema**. O exemplo, em seguida, mapeia as linhas retornadas pela instrução SELECT para o **BizTalkSchema** **DataTable**.  
  
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
>  Se o nome de uma coluna de origem não for fornecido para um mapeamento de coluna ou se o nome de uma tabela de origem não for fornecido para um mapeamento de tabela, os nomes padrão serão gerados automaticamente. Se nenhuma coluna de origem é fornecida para um mapeamento de coluna, o mapeamento de coluna recebe um nome padrão incremental **SourceColumn** *N,* começando com **SourceColumn1**. Se nenhum nome de tabela de origem é fornecido para um mapeamento de tabela, o mapeamento de tabela é fornecido um nome padrão incremental **SourceTable** *N*, começando com **SourceTable1**.  
  
> [!NOTE]
>  É recomendável que você evite a convenção de nomeação **SourceColumn** *N* para um mapeamento de coluna, ou **SourceTable** *N* para uma tabela mapeamento, porque o nome fornecido pode entrar em conflito com um nome de mapeamento de coluna padrão existente na **ColumnMappingCollection** ou o nome do mapeamento de tabela na **DataTableMappingCollection** . Se o nome fornecido já existir, será gerada uma exceção.  
  
## <a name="handling-multiple-result-sets"></a>Manipulando vários conjuntos de resultados  
 Se sua **SelectCommand** retorna várias tabelas, **preencher** gera automaticamente os nomes de tabela com valores incrementais para as tabelas a **conjunto de dados**, começando com o especificado o nome de tabela e continuando no formulário **TableName** *N*, começando com **TableName1**. Você pode usar mapeamentos de tabela para mapear o nome de tabela gerado automaticamente para um nome que você deseja especificado para a tabela na **conjunto de dados**. Por exemplo, para um **SelectCommand** , duas tabelas, que retorna **clientes** e **pedidos**, emita a seguinte chamada para **preencher**.  
  
```  
adapter.Fill(customersDataSet, "Customers")  
```  
  
 Duas tabelas são criadas na **conjunto de dados**: **Os clientes** e **Customers1**. Você pode usar mapeamentos de tabela para garantir que a segunda tabela é denominada **pedidos** em vez de **Customers1**. Para fazer isso, mapeie a tabela de origem do **Customers1** para o **DataSet** tabela **pedidos**, conforme mostrado no exemplo a seguir.  
  
```  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  
  
## <a name="see-also"></a>Consulte também

- [DataAdapters e DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [Recuperando e modificando dados no ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
