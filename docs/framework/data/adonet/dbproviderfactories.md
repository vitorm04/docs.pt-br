---
title: DbProviderFactories
ms.date: 03/30/2017
ms.assetid: 2a8e2640-3a49-42a1-a3a9-b43026907ae1
ms.openlocfilehash: b5f2dbb687348afac98247cb21bae831dea26bfe
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183306"
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
  
 [Modificar dados com um DbDataAdapter](modifying-data-with-a-dbdataadapter.md)  
 Demonstra como usar um <xref:System.Data.Common.DbCommandBuilder> com um <xref:System.Data.Common.DbDataAdapter> para recuperar e modificar dados.  
  
## <a name="see-also"></a>Veja também

- [Recuperando e modificando dados no ADO.NET](retrieving-and-modifying-data.md)
- [Visão geral do ADO.NET](ado-net-overview.md)
