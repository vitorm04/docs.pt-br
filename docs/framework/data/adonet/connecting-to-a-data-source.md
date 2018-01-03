---
title: Conectando-se a uma fonte de dados no ADO.NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 01a7342d6e081bec88aeef2c55461be2d936e4a7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="connecting-to-a-data-source-in-adonet"></a><span data-ttu-id="6b8b2-102">Conectando-se a uma fonte de dados no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6b8b2-102">Connecting to a Data Source in ADO.NET</span></span>
<span data-ttu-id="6b8b2-103">No ADO.NET, você usa um **Conexão** objeto para se conectar a uma fonte de dados específico fornecendo informações de autenticação necessária em uma cadeia de caracteres de conexão.</span><span class="sxs-lookup"><span data-stu-id="6b8b2-103">In ADO.NET you use a **Connection** object to connect to a specific data source by supplying necessary authentication information in a connection string.</span></span> <span data-ttu-id="6b8b2-104">O **Conexão** objeto usado depende do tipo de fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="6b8b2-104">The **Connection** object you use depends on the type of data source.</span></span>  
  
 <span data-ttu-id="6b8b2-105">Cada provedor de dados .NET Framework incluído no .NET Framework tem um objeto <xref:System.Data.Common.DbConnection>: o Provedor de Dados .NET Framework para OLE DB inclui um objeto <xref:System.Data.OleDb.OleDbConnection>, o Provedor de Dados .NET Framework para SQL Server inclui um objeto <xref:System.Data.SqlClient.SqlConnection>, o Provedor de Dados .NET Framework para ODBC inclui um objeto <xref:System.Data.Odbc.OdbcConnection> e o Provedor de Dados .NET Framework para Oracle inclui um objeto <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="6b8b2-105">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbConnection> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbConnection> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlConnection> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcConnection> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleConnection> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6b8b2-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="6b8b2-106">In This Section</span></span>  
 [<span data-ttu-id="6b8b2-107">Estabelecendo a conexão</span><span class="sxs-lookup"><span data-stu-id="6b8b2-107">Establishing the Connection</span></span>](../../../../docs/framework/data/adonet/establishing-the-connection.md)  
 <span data-ttu-id="6b8b2-108">Descreve como usar um **Conexão** objeto para estabelecer uma conexão com uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="6b8b2-108">Describes how to use a **Connection** object to establish a connection to a data source.</span></span>  
  
 [<span data-ttu-id="6b8b2-109">Eventos de Conexão</span><span class="sxs-lookup"><span data-stu-id="6b8b2-109">Connection Events</span></span>](../../../../docs/framework/data/adonet/connection-events.md)  
 <span data-ttu-id="6b8b2-110">Descreve como usar um **InfoMessage** evento para recuperar mensagens informativas de uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="6b8b2-110">Describes how to use an **InfoMessage** event to retrieve informational messages from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b8b2-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6b8b2-111">See Also</span></span>  
 [<span data-ttu-id="6b8b2-112">Cadeia de Conexão</span><span class="sxs-lookup"><span data-stu-id="6b8b2-112">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)  
 [<span data-ttu-id="6b8b2-113">Pooling de Conexão</span><span class="sxs-lookup"><span data-stu-id="6b8b2-113">Connection Pooling</span></span>](../../../../docs/framework/data/adonet/connection-pooling.md)  
 [<span data-ttu-id="6b8b2-114">Comandos e parâmetros</span><span class="sxs-lookup"><span data-stu-id="6b8b2-114">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="6b8b2-115">DataAdapters e DataReaders</span><span class="sxs-lookup"><span data-stu-id="6b8b2-115">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="6b8b2-116">Transações e simultaneidade</span><span class="sxs-lookup"><span data-stu-id="6b8b2-116">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 <span data-ttu-id="6b8b2-117">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="6b8b2-117">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
