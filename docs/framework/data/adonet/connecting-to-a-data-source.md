---
title: Conectando-se a uma fonte de dados no ADO.NET
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: f5788b9b0b19f32d03c917575db7b3f40324c0a2
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44031720"
---
# <a name="connecting-to-a-data-source-in-adonet"></a><span data-ttu-id="78706-102">Conectando-se a uma fonte de dados no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="78706-102">Connecting to a Data Source in ADO.NET</span></span>
<span data-ttu-id="78706-103">No ADO.NET você usa um **Conexão** objeto para se conectar a uma fonte de dados específica fornecendo as informações de autenticação necessárias em uma cadeia de caracteres de conexão.</span><span class="sxs-lookup"><span data-stu-id="78706-103">In ADO.NET you use a **Connection** object to connect to a specific data source by supplying necessary authentication information in a connection string.</span></span> <span data-ttu-id="78706-104">O **Conexão** objeto que você usa depende do tipo de fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="78706-104">The **Connection** object you use depends on the type of data source.</span></span>  
  
 <span data-ttu-id="78706-105">Cada provedor de dados .NET Framework incluído no .NET Framework tem um objeto <xref:System.Data.Common.DbConnection>: o Provedor de Dados .NET Framework para OLE DB inclui um objeto <xref:System.Data.OleDb.OleDbConnection>, o Provedor de Dados .NET Framework para SQL Server inclui um objeto <xref:System.Data.SqlClient.SqlConnection>, o Provedor de Dados .NET Framework para ODBC inclui um objeto <xref:System.Data.Odbc.OdbcConnection> e o Provedor de Dados .NET Framework para Oracle inclui um objeto <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="78706-105">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbConnection> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbConnection> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlConnection> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcConnection> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleConnection> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="78706-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="78706-106">In This Section</span></span>  
 [<span data-ttu-id="78706-107">Estabelecendo a conexão</span><span class="sxs-lookup"><span data-stu-id="78706-107">Establishing the Connection</span></span>](../../../../docs/framework/data/adonet/establishing-the-connection.md)  
 <span data-ttu-id="78706-108">Descreve como usar um **Conexão** objeto para estabelecer uma conexão a uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="78706-108">Describes how to use a **Connection** object to establish a connection to a data source.</span></span>  
  
 [<span data-ttu-id="78706-109">Eventos de Conexão</span><span class="sxs-lookup"><span data-stu-id="78706-109">Connection Events</span></span>](../../../../docs/framework/data/adonet/connection-events.md)  
 <span data-ttu-id="78706-110">Descreve como usar um **InfoMessage** evento para recuperar mensagens informativas de uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="78706-110">Describes how to use an **InfoMessage** event to retrieve informational messages from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78706-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="78706-111">See Also</span></span>  
 [<span data-ttu-id="78706-112">Cadeia de Conexão</span><span class="sxs-lookup"><span data-stu-id="78706-112">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)  
 [<span data-ttu-id="78706-113">Pooling de Conexão</span><span class="sxs-lookup"><span data-stu-id="78706-113">Connection Pooling</span></span>](../../../../docs/framework/data/adonet/connection-pooling.md)  
 [<span data-ttu-id="78706-114">Comandos e parâmetros</span><span class="sxs-lookup"><span data-stu-id="78706-114">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="78706-115">DataAdapters e DataReaders</span><span class="sxs-lookup"><span data-stu-id="78706-115">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="78706-116">Transações e simultaneidade</span><span class="sxs-lookup"><span data-stu-id="78706-116">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 <span data-ttu-id="78706-117">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="78706-117">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
