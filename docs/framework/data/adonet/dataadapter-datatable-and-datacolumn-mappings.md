---
title: Mapeamentos de DataTable e de DataColumn do DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.openlocfilehash: 6380dd0512bd7834f50b87f90f445cb01b7a8b95
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151553"
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a>Mapeamentos de DataTable e de DataColumn do DataAdapter
Um **DataAdapter** contém uma coleção <xref:System.Data.Common.DataTableMapping> de zero ou mais objetos em sua propriedade **TableMappings.** Um **DataTableMapping** fornece um mapeamento mestre entre os dados retornados de <xref:System.Data.DataTable>uma consulta contra uma fonte de dados e um . O nome **DataTableMapping** pode ser passado no lugar do nome **DataTable** para o método **Preenchimento** do **DataAdapter**. O exemplo a seguir cria um **DataTableMapping** chamado **AuthorsMapping** para a tabela **Autores.**  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 Um **DataTableMapping** permite que você use nomes de coluna **satisfazem** uma Tabela de Dados diferente sustais das do banco de dados. O **DataAdapter** usa o mapeamento para corresponder às colunas quando a tabela é atualizada.  
  
 Se você não especificar um **nome de tabela** ou um nome **DataTableMapping** ao chamar o método **Preenchimento** ou **Atualização** do **DataAdapter,** o **DataAdapter** procurará um **DataTableMapping** chamado "Table". Se esse **DataTableMapping** não existir, a **TabelaNome** da Tabela de **Dados** será "Tabela". Você pode especificar um **DataTableMapping** padrão criando um **DataTableMapping** com o nome de "Tabela".  
  
 O exemplo de código a seguir <xref:System.Data.Common> cria um **DataTableMapping** (a partir do namespace) e torna-o o mapeamento padrão para o **DataAdapter** especificado, nomeando-o "Tabela". O exemplo, então, mapeia as colunas da primeira tabela no resultado da consulta (a tabela **Clientes** do banco <xref:System.Data.DataSet>de dados **Northwind)** para um conjunto de nomes mais fáceis de usar na tabela **Clientes Northwind** na . Para colunas que não são mapeadas, o nome da coluna na fonte de dados é usado.  
  
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
  
 Em situações mais avançadas, você pode decidir que deseja que o mesmo **DataAdapter** suporte o carregamento de diferentes tabelas com diferentes mapeamentos. Para fazer isso, basta adicionar objetos adicionais **do DataTableMapping.**  
  
 Quando o método **Preenchimento** é aprovado uma instância de um **dataset** e um nome **DataTableMapping,** se um mapeamento com esse nome existir, ele será usado; caso contrário, uma **DataTable** com esse nome é usada.  
  
 Os exemplos a seguir criam um **DataTableMapping** com um nome de **Clientes** e um nome **de DataTable** de **BizTalkSchema**. O exemplo, então, mapeia as linhas retornadas pela declaração SELECT para a Tabela **de Dados** **BizTalkSchema** .  
  
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
> Se o nome de uma coluna de origem não for fornecido para um mapeamento de coluna ou se o nome de uma tabela de origem não for fornecido para um mapeamento de tabela, os nomes padrão serão gerados automaticamente. Se nenhuma coluna de origem for fornecida para um mapeamento de coluna, o mapeamento da coluna recebe um nome padrão incremental da **SourceColumn** *N,* começando com **SourceColumn1**. Se nenhum nome de tabela de origem for fornecido para um mapeamento de tabela, o mapeamento da tabela recebe um nome padrão incremental de **SourceTable** *N*, começando com **SourceTable1**.  
  
> [!NOTE]
> Recomendamos que você evite a convenção de nomeação da **SourceColumn** *N* para um mapeamento de coluna, ou **SourceTable** *N* para um mapeamento de tabela, porque o nome que você fornece pode entrar em conflito com um nome de mapeamento de coluna padrão existente no **ColumnMappingCollection** ou nome de mapeamento de tabela na **DataTableMappingCollection**. Se o nome fornecido já existir, será gerada uma exceção.  
  
## <a name="handling-multiple-result-sets"></a>Manipulando vários conjuntos de resultados  
 Se o **SelectCommand** retornar várias tabelas, **o Fill** gerará automaticamente nomes de tabela com valores incrementais para as tabelas no **Conjunto de Dados,** começando com o nome da tabela especificado e continuando no formulário **TableName** *N*, começando com **TableName1**. Você pode usar mapeamentos de tabela para mapear o nome da tabela gerado automaticamente para um nome que você deseja especificado para a tabela no **Conjunto de dados**. Por exemplo, para um **SelectCommand** que retorna duas **tabelas, Clientes** e **Pedidos,** emita a seguinte chamada para **preencher**.  
  
```vb  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.Fill(customersDataSet, "Customers");  
```  

 Duas tabelas são criadas no **DataSet**: **Clientes** e **Clientes1**. Você pode usar mapeamentos de tabela para garantir que a segunda tabela seja nomeada **Orders** em vez de **Clientes1**. Para isso, mapeie a tabela de origem dos **Clientes1** para as **ordens**da tabela **DataSet,** conforme mostrado no exemplo a seguir.  
  
```vb  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.TableMappings.Add("Customers1", "Orders");  
adapter.Fill(customersDataSet, "Customers");  
```
  
## <a name="see-also"></a>Confira também

- [DataAdapters e DataReaders](dataadapters-and-datareaders.md)
- [Retrieving and Modifying Data in ADO.NET](retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)
- [Visão geral do ADO.NET](ado-net-overview.md)
