---
title: Conectando a uma Fonte de Dados
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: 84dc15c0965b7ac8209bd9115d611162e57d6dda
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980243"
---
# <a name="connecting-to-a-data-source-in-adonet"></a>Conectando-se a uma fonte de dados no ADO.NET
No ADO.NET, você usa um objeto de **conexão** para se conectar a uma fonte de dados específica fornecendo informações de autenticação necessárias em uma cadeia de conexão. O objeto de **conexão** que você usa depende do tipo de fonte de dados.  
  
 Cada provedor de dados .NET Framework incluído no .NET Framework tem um objeto <xref:System.Data.Common.DbConnection>: o Provedor de Dados .NET Framework para OLE DB inclui um objeto <xref:System.Data.OleDb.OleDbConnection>, o Provedor de Dados .NET Framework para SQL Server inclui um objeto <xref:System.Data.SqlClient.SqlConnection>, o Provedor de Dados .NET Framework para ODBC inclui um objeto <xref:System.Data.Odbc.OdbcConnection> e o Provedor de Dados .NET Framework para Oracle inclui um objeto <xref:System.Data.OracleClient.OracleConnection>.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Estabelecendo a conexão](establishing-the-connection.md)  
 Descreve como usar um objeto de **conexão** para estabelecer uma conexão com uma fonte de dados.  
  
 [Eventos de Conexão](connection-events.md)  
 Descreve como usar um evento **InfoMessage** para recuperar mensagens informativas de uma fonte de dados.  
  
## <a name="see-also"></a>Veja também

- [Cadeia de Conexão](connection-strings.md)
- [Pooling de Conexão](connection-pooling.md)
- [Comandos e parâmetros](commands-and-parameters.md)
- [DataAdapters e DataReaders](dataadapters-and-datareaders.md)
- [Transações e simultaneidade](transactions-and-concurrency.md)
- [ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)
