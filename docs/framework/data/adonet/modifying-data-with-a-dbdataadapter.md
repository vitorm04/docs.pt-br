---
title: Modificar dados com um DbDataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e35c7f9e-648b-4fcc-9361-d365c3e42c9a
ms.openlocfilehash: cd1f5faa0efe141dc064f0150b94807b90e7e2b8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794824"
---
# <a name="modifying-data-with-a-dbdataadapter"></a>Modificar dados com um DbDataAdapter
O <xref:System.Data.Common.DbProviderFactory.CreateDataAdapter%2A> método de um <xref:System.Data.Common.DbProviderFactory> objeto fornece a você <xref:System.Data.Common.DbDataAdapter> um objeto fortemente tipado para o provedor de dados subjacente especificado no momento em que você cria a fábrica. Você pode usar um <xref:System.Data.Common.DbCommandBuilder> para criar comandos para inserir, atualizar e excluir dados de um <xref:System.Data.DataSet> para uma fonte de dados.  
  
## <a name="retrieving-data-with-a-dbdataadapter"></a>Recuperando dados com um DbDataAdapter  
 Este exemplo demonstra como criar um tipo fortemente tipado `DbDataAdapter` com base em um nome de provedor e cadeia de conexão. O código usa o <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> método <xref:System.Data.Common.DbProviderFactory> do para criar um <xref:System.Data.Common.DbConnection>. Em seguida, o código usa <xref:System.Data.Common.DbProviderFactory.CreateCommand%2A> o método para criar <xref:System.Data.Common.DbCommand> um para selecionar dados definindo suas `CommandText` propriedades `Connection` e. Por fim, o código cria <xref:System.Data.Common.DbDataAdapter> um objeto usando <xref:System.Data.Common.DbProviderFactory.CreateDataAdapter%2A> o método e define `SelectCommand` sua propriedade. O `Fill` método <xref:System.Data.DataTable>do carrega os dados em um. `DbDataAdapter`  
  
 [!code-csharp[DataWorks DbProviderFactories.DbDataAdapter#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapter/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbDataAdapter#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapter/VB/source.vb#1)]  
  
## <a name="modifying-data-with-a-dbdataadapter"></a>Modificar dados com um DbDataAdapter  
 Este exemplo demonstra como modificar dados em um `DataTable` <xref:System.Data.Common.DbDataAdapter> usando um usando um <xref:System.Data.Common.DbCommandBuilder> para gerar os comandos necessários para atualizar os dados na fonte de dados. <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> O`DbDataAdapter` de é definido para recuperar CustomerID e CompanyName da tabela Customers. O <xref:System.Data.Common.DbCommandBuilder.GetInsertCommand%2A> método é usado para definir a <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> Propriedade, o <xref:System.Data.Common.DbCommandBuilder.GetUpdateCommand%2A> método é usado para definir a <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> Propriedade e o <xref:System.Data.Common.DbCommandBuilder.GetDeleteCommand%2A> método é usado para definir a <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> propriedade. O código adiciona uma nova linha à tabela Customers e atualiza a fonte de dados. Em seguida, o código localiza a linha adicionada pesquisando no CustomerID, que é a chave primária definida para a tabela Customers. Ele altera o CompanyName e atualiza a fonte de dados. Por fim, o código exclui a linha.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbDataAdapterModify#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapterModify/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbDataAdapterModify#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapterModify/VB/source.vb#1)]  
  
## <a name="handling-parameters"></a>Manipulando parâmetros  
 O .NET Framework provedores de dados manipulam a nomenclatura e a especificação de parâmetros e espaços reservados de parâmetros de forma diferente. Essa sintaxe é personalizada para uma fonte de dados específica, conforme descrito na tabela a seguir.  
  
|Provedor de dados|Sintaxe de nomeação de parâmetro|  
|-------------------|-----------------------------|  
|`SqlClient`|Usa parâmetros nomeados no formato `@` *ParameterName*.|  
|`OracleClient`|Usa parâmetros nomeados no formato `:` *parmname* (ou *parmname*).|  
|`OleDb`|Usa os marcadores de parâmetros posicionais indicados por um ponto de interrogação (`?`).|  
|`Odbc`|Usa os marcadores de parâmetros posicionais indicados por um ponto de interrogação (`?`).|  
  
 O modelo de fábrica não é útil para criar objetos `DbCommand` e `DbDataAdapter` com parâmetros. Você precisará ramificar em seu código para criar parâmetros que são personalizados para seu provedor de dados.  
  
> [!IMPORTANT]
> Evitar os parâmetros específicos do provedor usando a concatenação de cadeia de caracteres para construir instruções SQL diretas não é recomendado por motivos de segurança. Usar a concatenação de cadeia de caracteres em vez de parâmetros deixa seu aplicativo vulnerável a ataques de injeção de SQL.  
  
## <a name="see-also"></a>Consulte também

- [DbProviderFactories](dbproviderfactories.md)
- [Obtendo um DbProviderFactory](obtaining-a-dbproviderfactory.md)
- [DbConnection, DbCommand e DbException](dbconnection-dbcommand-and-dbexception.md)
- [ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)
