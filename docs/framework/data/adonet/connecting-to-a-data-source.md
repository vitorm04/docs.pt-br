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
ms.openlocfilehash: 0d21c571b659e9d7aef65893db18b034d614e2af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="connecting-to-a-data-source-in-adonet"></a><span data-ttu-id="33c80-102">Conectando-se a uma fonte de dados no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="33c80-102">Connecting to a Data Source in ADO.NET</span></span>
<span data-ttu-id="33c80-103">No ADO.NET, você usa um **Conexão** objeto para se conectar a uma fonte de dados específico fornecendo informações de autenticação necessária em uma cadeia de caracteres de conexão.</span><span class="sxs-lookup"><span data-stu-id="33c80-103">In ADO.NET you use a **Connection** object to connect to a specific data source by supplying necessary authentication information in a connection string.</span></span> <span data-ttu-id="33c80-104">O **Conexão** objeto usado depende do tipo de fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="33c80-104">The **Connection** object you use depends on the type of data source.</span></span>  
  
 <span data-ttu-id="33c80-105">Cada provedor de dados .NET Framework incluído no .NET Framework tem um objeto <xref:System.Data.Common.DbConnection>: o Provedor de Dados .NET Framework para OLE DB inclui um objeto <xref:System.Data.OleDb.OleDbConnection>, o Provedor de Dados .NET Framework para SQL Server inclui um objeto <xref:System.Data.SqlClient.SqlConnection>, o Provedor de Dados .NET Framework para ODBC inclui um objeto <xref:System.Data.Odbc.OdbcConnection> e o Provedor de Dados .NET Framework para Oracle inclui um objeto <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="33c80-105">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbConnection> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbConnection> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlConnection> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcConnection> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleConnection> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="33c80-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="33c80-106">In This Section</span></span>  
 [<span data-ttu-id="33c80-107">Estabelecendo a Conexão</span><span class="sxs-lookup"><span data-stu-id="33c80-107">Establishing the Connection</span></span>](../../../../docs/framework/data/adonet/establishing-the-connection.md)  
 <span data-ttu-id="33c80-108">Descreve como usar um **Conexão** objeto para estabelecer uma conexão com uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="33c80-108">Describes how to use a **Connection** object to establish a connection to a data source.</span></span>  
  
 [<span data-ttu-id="33c80-109">Eventos de Conexão</span><span class="sxs-lookup"><span data-stu-id="33c80-109">Connection Events</span></span>](../../../../docs/framework/data/adonet/connection-events.md)  
 <span data-ttu-id="33c80-110">Descreve como usar um **InfoMessage** evento para recuperar mensagens informativas de uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="33c80-110">Describes how to use an **InfoMessage** event to retrieve informational messages from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33c80-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="33c80-111">See Also</span></span>  
 [<span data-ttu-id="33c80-112">Cadeias de caracteres de Conexão</span><span class="sxs-lookup"><span data-stu-id="33c80-112">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)  
 [<span data-ttu-id="33c80-113">Pooling de Conexão</span><span class="sxs-lookup"><span data-stu-id="33c80-113">Connection Pooling</span></span>](../../../../docs/framework/data/adonet/connection-pooling.md)  
 [<span data-ttu-id="33c80-114">Comandos e parâmetros</span><span class="sxs-lookup"><span data-stu-id="33c80-114">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="33c80-115">DataAdapters e DataReaders</span><span class="sxs-lookup"><span data-stu-id="33c80-115">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="33c80-116">Transações e simultaneidade</span><span class="sxs-lookup"><span data-stu-id="33c80-116">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 <span data-ttu-id="33c80-117">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="33c80-117">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
