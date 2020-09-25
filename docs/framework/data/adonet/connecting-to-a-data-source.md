---
title: Conectando-se a uma fonte de dados
deescription: Learn about Connection objects, used to connect to data sources in ADO.NET. The Connection object you choose depends on the type of data source.
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: b9e69b029ad37c583e51c219f87ff9d7d8e7315c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203768"
---
# <a name="connecting-to-a-data-source-in-adonet"></a><span data-ttu-id="6b4eb-102">Conectando-se a uma fonte de dados no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6b4eb-102">Connecting to a Data Source in ADO.NET</span></span>

<span data-ttu-id="6b4eb-103">No ADO.NET, você usa um objeto de **conexão** para se conectar a uma fonte de dados específica fornecendo informações de autenticação necessárias em uma cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="6b4eb-103">In ADO.NET, you use a **Connection** object to connect to a specific data source by supplying necessary authentication information in a connection string.</span></span> <span data-ttu-id="6b4eb-104">O objeto de **conexão** que você usa depende do tipo de fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="6b4eb-104">The **Connection** object you use depends on the type of data source.</span></span>  
  
 <span data-ttu-id="6b4eb-105">Cada provedor de dados .NET Framework incluído no .NET Framework tem um objeto <xref:System.Data.Common.DbConnection>: o Provedor de Dados .NET Framework para OLE DB inclui um objeto <xref:System.Data.OleDb.OleDbConnection>, o Provedor de Dados .NET Framework para SQL Server inclui um objeto <xref:System.Data.SqlClient.SqlConnection>, o Provedor de Dados .NET Framework para ODBC inclui um objeto <xref:System.Data.Odbc.OdbcConnection> e o Provedor de Dados .NET Framework para Oracle inclui um objeto <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="6b4eb-105">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbConnection> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbConnection> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlConnection> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcConnection> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleConnection> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6b4eb-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="6b4eb-106">In This Section</span></span>  

 <span data-ttu-id="6b4eb-107">[Estabelecendo a conexão](establishing-the-connection.md)</span><span class="sxs-lookup"><span data-stu-id="6b4eb-107">[Establishing the Connection](establishing-the-connection.md)</span></span>\
 <span data-ttu-id="6b4eb-108">Descreve como usar um objeto de **conexão** para estabelecer uma conexão com uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="6b4eb-108">Describes how to use a **Connection** object to establish a connection to a data source.</span></span>  
  
 <span data-ttu-id="6b4eb-109">[Eventos de conexão](connection-events.md)</span><span class="sxs-lookup"><span data-stu-id="6b4eb-109">[Connection Events](connection-events.md)</span></span>\
 <span data-ttu-id="6b4eb-110">Descreve como usar um evento **InfoMessage** para recuperar mensagens informativas de uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="6b4eb-110">Describes how to use an **InfoMessage** event to retrieve informational messages from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b4eb-111">Veja também</span><span class="sxs-lookup"><span data-stu-id="6b4eb-111">See also</span></span>

- [<span data-ttu-id="6b4eb-112">Cadeias de conexão</span><span class="sxs-lookup"><span data-stu-id="6b4eb-112">Connection Strings</span></span>](connection-strings.md)
- [<span data-ttu-id="6b4eb-113">Pool de conexões</span><span class="sxs-lookup"><span data-stu-id="6b4eb-113">Connection Pooling</span></span>](connection-pooling.md)
- [<span data-ttu-id="6b4eb-114">Comandos e parâmetros</span><span class="sxs-lookup"><span data-stu-id="6b4eb-114">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="6b4eb-115">DataAdapters e DataReaders</span><span class="sxs-lookup"><span data-stu-id="6b4eb-115">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="6b4eb-116">Transações e simultaneidade</span><span class="sxs-lookup"><span data-stu-id="6b4eb-116">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- [<span data-ttu-id="6b4eb-117">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6b4eb-117">ADO.NET Overview</span></span>](ado-net-overview.md)
