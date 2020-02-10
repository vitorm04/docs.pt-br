---
title: Conectando-se a uma fonte de dados
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: 206a4f741b6bf711b51da794e23f779c2bea6fa0
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094443"
---
# <a name="connecting-to-a-data-source-in-adonet"></a><span data-ttu-id="d5d41-102">Conectando-se a uma fonte de dados no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d5d41-102">Connecting to a Data Source in ADO.NET</span></span>

<span data-ttu-id="d5d41-103">No ADO.NET, você usa um objeto de **conexão** para se conectar a uma fonte de dados específica fornecendo informações de autenticação necessárias em uma cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="d5d41-103">In ADO.NET, you use a **Connection** object to connect to a specific data source by supplying necessary authentication information in a connection string.</span></span> <span data-ttu-id="d5d41-104">O objeto de **conexão** que você usa depende do tipo de fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="d5d41-104">The **Connection** object you use depends on the type of data source.</span></span>  
  
 <span data-ttu-id="d5d41-105">Cada provedor de dados .NET Framework incluído no .NET Framework tem um objeto <xref:System.Data.Common.DbConnection>: o Provedor de Dados .NET Framework para OLE DB inclui um objeto <xref:System.Data.OleDb.OleDbConnection>, o Provedor de Dados .NET Framework para SQL Server inclui um objeto <xref:System.Data.SqlClient.SqlConnection>, o Provedor de Dados .NET Framework para ODBC inclui um objeto <xref:System.Data.Odbc.OdbcConnection> e o Provedor de Dados .NET Framework para Oracle inclui um objeto <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="d5d41-105">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbConnection> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbConnection> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlConnection> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcConnection> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleConnection> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d5d41-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="d5d41-106">In This Section</span></span>  
 <span data-ttu-id="d5d41-107">[Estabelecendo a conexão](establishing-the-connection.md)</span><span class="sxs-lookup"><span data-stu-id="d5d41-107">[Establishing the Connection](establishing-the-connection.md)</span></span>\
 <span data-ttu-id="d5d41-108">Descreve como usar um objeto de **conexão** para estabelecer uma conexão com uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="d5d41-108">Describes how to use a **Connection** object to establish a connection to a data source.</span></span>  
  
 <span data-ttu-id="d5d41-109">[Eventos de conexão](connection-events.md)</span><span class="sxs-lookup"><span data-stu-id="d5d41-109">[Connection Events](connection-events.md)</span></span>\
 <span data-ttu-id="d5d41-110">Descreve como usar um evento **InfoMessage** para recuperar mensagens informativas de uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="d5d41-110">Describes how to use an **InfoMessage** event to retrieve informational messages from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5d41-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="d5d41-111">See also</span></span>

- [<span data-ttu-id="d5d41-112">Cadeias de conexão</span><span class="sxs-lookup"><span data-stu-id="d5d41-112">Connection Strings</span></span>](connection-strings.md)
- [<span data-ttu-id="d5d41-113">Pool de conexão</span><span class="sxs-lookup"><span data-stu-id="d5d41-113">Connection Pooling</span></span>](connection-pooling.md)
- [<span data-ttu-id="d5d41-114">Comandos e parâmetros</span><span class="sxs-lookup"><span data-stu-id="d5d41-114">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="d5d41-115">DataAdapters e DataReaders</span><span class="sxs-lookup"><span data-stu-id="d5d41-115">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="d5d41-116">Transações e simultaneidade</span><span class="sxs-lookup"><span data-stu-id="d5d41-116">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- <span data-ttu-id="d5d41-117">[ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="d5d41-117">[ADO.NET Overview](ado-net-overview.md)</span></span>
