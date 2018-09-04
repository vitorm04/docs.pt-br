---
title: DbProviderFactories
ms.date: 03/30/2017
ms.assetid: 2a8e2640-3a49-42a1-a3a9-b43026907ae1
ms.openlocfilehash: 403c7a50bcb802140bb008bd18db0a6f16663942
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43504724"
---
# <a name="dbproviderfactories"></a>DbProviderFactories
O namespace <xref:System.Data.Common> fornece classes para criar instâncias <xref:System.Data.Common.DbProviderFactory> para funcionar com as fontes de dados específicas. Quando você cria uma instância <xref:System.Data.Common.DbProviderFactory> e passa informações sobre o provedor de dados, o `DbProviderFactory` pode determinar o objeto de conexão correto e fortemente tipado para retornar com base nas informações que recebeu.  
  
 A partir do .NET Framework versão 4, os provedores de dados como <xref:System.Data.Odbc>, <xref:System.Data.OleDb>, <xref:System.Data.SqlClient> e <xref:System.Data.OracleClient> já não são listados no arquivo machine.config, mas os provedores personalizados continuarão a ser listados lá.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral do modelo de fábrica](../../../../docs/framework/data/adonet/factory-model-overview.md)  
 Fornece uma visão geral do padrão de design de fábrica e da interface de programação.  
  
 [Obtendo um DbProviderFactory](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 Demonstra como listar os provedores de dados instalados e criar um <xref:System.Data.Common.DbConnection> de um `DbProviderFactory`.  
  
 [DbConnection, DbCommand e DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 Demonstra como criar um <xref:System.Data.Common.DbCommand> e <xref:System.Data.Common.DbDataReader> e como manipular erros de dados usando <xref:System.Data.Common.DbException>.  
  
 [Modificando dados com um DbDataAdapter](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 Demonstra como usar um <xref:System.Data.Common.DbCommandBuilder> com um <xref:System.Data.Common.DbDataAdapter> para recuperar e modificar dados.  
  
## <a name="see-also"></a>Consulte também  
 [Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)  
 [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
