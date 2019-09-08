---
title: DbProviderFactories
ms.date: 03/30/2017
ms.assetid: 2a8e2640-3a49-42a1-a3a9-b43026907ae1
ms.openlocfilehash: e3ea9e3d083314f8df25f9edadbd1a18f1227293
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784094"
---
# <a name="dbproviderfactories"></a>DbProviderFactories
O namespace <xref:System.Data.Common> fornece classes para criar instâncias <xref:System.Data.Common.DbProviderFactory> para funcionar com as fontes de dados específicas. Quando você cria uma instância <xref:System.Data.Common.DbProviderFactory> e passa informações sobre o provedor de dados, o `DbProviderFactory` pode determinar o objeto de conexão correto e fortemente tipado para retornar com base nas informações que recebeu.  
  
 A partir do .NET Framework versão 4, os provedores de dados como <xref:System.Data.Odbc>, <xref:System.Data.OleDb>, <xref:System.Data.SqlClient> e <xref:System.Data.OracleClient> já não são listados no arquivo machine.config, mas os provedores personalizados continuarão a ser listados lá.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral do modelo de fábrica](factory-model-overview.md)  
 Fornece uma visão geral do padrão de design de fábrica e da interface de programação.  
  
 [Obtendo um DbProviderFactory](obtaining-a-dbproviderfactory.md)  
 Demonstra como listar os provedores de dados instalados e criar um <xref:System.Data.Common.DbConnection> de um `DbProviderFactory`.  
  
 [DbConnection, DbCommand e DbException](dbconnection-dbcommand-and-dbexception.md)  
 Demonstra como criar um <xref:System.Data.Common.DbCommand> e <xref:System.Data.Common.DbDataReader> e como manipular erros de dados usando <xref:System.Data.Common.DbException>.  
  
 [Modificando dados com um DbDataAdapter](modifying-data-with-a-dbdataadapter.md)  
 Demonstra como usar um <xref:System.Data.Common.DbCommandBuilder> com um <xref:System.Data.Common.DbDataAdapter> para recuperar e modificar dados.  
  
## <a name="see-also"></a>Consulte também

- [Retrieving and Modifying Data in ADO.NET](retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)
- [ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)
