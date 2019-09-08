---
title: Conectando-se a uma fonte de dados no ADO.NET
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: 01e4048fb9c7b53b1b1907d1965f822b9a4644a4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786770"
---
# <a name="connecting-to-a-data-source-in-adonet"></a><span data-ttu-id="14c4f-102">Conectando-se a uma fonte de dados no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="14c4f-102">Connecting to a Data Source in ADO.NET</span></span>
<span data-ttu-id="14c4f-103">No ADO.NET, você usa um objeto de **conexão** para se conectar a uma fonte de dados específica fornecendo informações de autenticação necessárias em uma cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="14c4f-103">In ADO.NET you use a **Connection** object to connect to a specific data source by supplying necessary authentication information in a connection string.</span></span> <span data-ttu-id="14c4f-104">O objeto de **conexão** que você usa depende do tipo de fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="14c4f-104">The **Connection** object you use depends on the type of data source.</span></span>  
  
 <span data-ttu-id="14c4f-105">Cada provedor de dados .NET Framework incluído no .NET Framework tem um objeto <xref:System.Data.Common.DbConnection>: o Provedor de Dados .NET Framework para OLE DB inclui um objeto <xref:System.Data.OleDb.OleDbConnection>, o Provedor de Dados .NET Framework para SQL Server inclui um objeto <xref:System.Data.SqlClient.SqlConnection>, o Provedor de Dados .NET Framework para ODBC inclui um objeto <xref:System.Data.Odbc.OdbcConnection> e o Provedor de Dados .NET Framework para Oracle inclui um objeto <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="14c4f-105">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbConnection> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbConnection> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlConnection> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcConnection> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleConnection> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="14c4f-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="14c4f-106">In This Section</span></span>  
 [<span data-ttu-id="14c4f-107">Estabelecendo a conexão</span><span class="sxs-lookup"><span data-stu-id="14c4f-107">Establishing the Connection</span></span>](establishing-the-connection.md)  
 <span data-ttu-id="14c4f-108">Descreve como usar um objeto de **conexão** para estabelecer uma conexão com uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="14c4f-108">Describes how to use a **Connection** object to establish a connection to a data source.</span></span>  
  
 [<span data-ttu-id="14c4f-109">Eventos de Conexão</span><span class="sxs-lookup"><span data-stu-id="14c4f-109">Connection Events</span></span>](connection-events.md)  
 <span data-ttu-id="14c4f-110">Descreve como usar um evento **InfoMessage** para recuperar mensagens informativas de uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="14c4f-110">Describes how to use an **InfoMessage** event to retrieve informational messages from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14c4f-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="14c4f-111">See also</span></span>

- [<span data-ttu-id="14c4f-112">Cadeia de Conexão</span><span class="sxs-lookup"><span data-stu-id="14c4f-112">Connection Strings</span></span>](connection-strings.md)
- [<span data-ttu-id="14c4f-113">Pooling de Conexão</span><span class="sxs-lookup"><span data-stu-id="14c4f-113">Connection Pooling</span></span>](connection-pooling.md)
- [<span data-ttu-id="14c4f-114">Comandos e parâmetros</span><span class="sxs-lookup"><span data-stu-id="14c4f-114">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="14c4f-115">DataAdapters e DataReaders</span><span class="sxs-lookup"><span data-stu-id="14c4f-115">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="14c4f-116">Transações e simultaneidade</span><span class="sxs-lookup"><span data-stu-id="14c4f-116">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- <span data-ttu-id="14c4f-117">[ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="14c4f-117">[ADO.NET Overview](ado-net-overview.md)</span></span>
