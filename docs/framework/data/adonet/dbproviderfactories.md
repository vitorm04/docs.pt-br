---
title: DbProviderFactories
ms.date: 03/30/2017
ms.assetid: 2a8e2640-3a49-42a1-a3a9-b43026907ae1
ms.openlocfilehash: 255ef115e6851b5f1d93744b54ec88990746d9cb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543533"
---
# <a name="dbproviderfactories"></a><span data-ttu-id="3e55a-102">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="3e55a-102">DbProviderFactories</span></span>
<span data-ttu-id="3e55a-103">O namespace <xref:System.Data.Common> fornece classes para criar instâncias <xref:System.Data.Common.DbProviderFactory> para funcionar com as fontes de dados específicas.</span><span class="sxs-lookup"><span data-stu-id="3e55a-103">The <xref:System.Data.Common> namespace provides classes for creating <xref:System.Data.Common.DbProviderFactory> instances to work with specific data sources.</span></span> <span data-ttu-id="3e55a-104">Quando você cria uma instância <xref:System.Data.Common.DbProviderFactory> e passa informações sobre o provedor de dados, o `DbProviderFactory` pode determinar o objeto de conexão correto e fortemente tipado para retornar com base nas informações que recebeu.</span><span class="sxs-lookup"><span data-stu-id="3e55a-104">When you create a <xref:System.Data.Common.DbProviderFactory> instance and pass it information about the data provider, the `DbProviderFactory` can determine the correct, strongly typed connection object to return based on the information it has been provided.</span></span>  
  
 <span data-ttu-id="3e55a-105">A partir do .NET Framework versão 4, os provedores de dados como <xref:System.Data.Odbc>, <xref:System.Data.OleDb>, <xref:System.Data.SqlClient> e <xref:System.Data.OracleClient> já não são listados no arquivo machine.config, mas os provedores personalizados continuarão a ser listados lá.</span><span class="sxs-lookup"><span data-stu-id="3e55a-105">Beginning in the .NET Framework version 4, data providers such as <xref:System.Data.Odbc>, <xref:System.Data.OleDb>, <xref:System.Data.SqlClient>, and <xref:System.Data.OracleClient> are no longer listed in machine.config file, but custom providers will continue to be listed there.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3e55a-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="3e55a-106">In This Section</span></span>  
 [<span data-ttu-id="3e55a-107">Visão geral do modelo de fábrica</span><span class="sxs-lookup"><span data-stu-id="3e55a-107">Factory Model Overview</span></span>](../../../../docs/framework/data/adonet/factory-model-overview.md)  
 <span data-ttu-id="3e55a-108">Fornece uma visão geral do padrão de design de fábrica e da interface de programação.</span><span class="sxs-lookup"><span data-stu-id="3e55a-108">Provides an overview of the factory design pattern and programming interface.</span></span>  
  
 [<span data-ttu-id="3e55a-109">Obtendo um DbProviderFactory</span><span class="sxs-lookup"><span data-stu-id="3e55a-109">Obtaining a DbProviderFactory</span></span>](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 <span data-ttu-id="3e55a-110">Demonstra como listar os provedores de dados instalados e criar um <xref:System.Data.Common.DbConnection> de um `DbProviderFactory`.</span><span class="sxs-lookup"><span data-stu-id="3e55a-110">Demonstrates how to list the installed data providers and create a <xref:System.Data.Common.DbConnection> from a `DbProviderFactory`.</span></span>  
  
 [<span data-ttu-id="3e55a-111">DbConnection, DbCommand e DbException</span><span class="sxs-lookup"><span data-stu-id="3e55a-111">DbConnection, DbCommand and DbException</span></span>](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 <span data-ttu-id="3e55a-112">Demonstra como criar um <xref:System.Data.Common.DbCommand> e <xref:System.Data.Common.DbDataReader> e como manipular erros de dados usando <xref:System.Data.Common.DbException>.</span><span class="sxs-lookup"><span data-stu-id="3e55a-112">Demonstrates how to create a <xref:System.Data.Common.DbCommand> and <xref:System.Data.Common.DbDataReader>, and how to handle data errors using <xref:System.Data.Common.DbException>.</span></span>  
  
 [<span data-ttu-id="3e55a-113">Modificando dados com um DbDataAdapter</span><span class="sxs-lookup"><span data-stu-id="3e55a-113">Modifying Data with a DbDataAdapter</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 <span data-ttu-id="3e55a-114">Demonstra como usar um <xref:System.Data.Common.DbCommandBuilder> com um <xref:System.Data.Common.DbDataAdapter> para recuperar e modificar dados.</span><span class="sxs-lookup"><span data-stu-id="3e55a-114">Demonstrates how to use a <xref:System.Data.Common.DbCommandBuilder> with a <xref:System.Data.Common.DbDataAdapter> to retrieve and modify data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e55a-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e55a-115">See also</span></span>
- <span data-ttu-id="3e55a-116">[Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="3e55a-116">[Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)</span></span>
- <span data-ttu-id="3e55a-117">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="3e55a-117">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
