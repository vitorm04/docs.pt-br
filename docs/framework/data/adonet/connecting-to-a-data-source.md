---
title: Conectando-se a uma fonte de dados no ADO.NET
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: c04624be758e4bc7c8b1981ad6a9dc44430d62b5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083706"
---
# <a name="connecting-to-a-data-source-in-adonet"></a>Conectando-se a uma fonte de dados no ADO.NET
No ADO.NET você usa um **Conexão** objeto para se conectar a uma fonte de dados específica fornecendo as informações de autenticação necessárias em uma cadeia de caracteres de conexão. O **Conexão** objeto que você usa depende do tipo de fonte de dados.  
  
 Cada provedor de dados .NET Framework incluído no .NET Framework tem um objeto <xref:System.Data.Common.DbConnection>: o Provedor de Dados .NET Framework para OLE DB inclui um objeto <xref:System.Data.OleDb.OleDbConnection>, o Provedor de Dados .NET Framework para SQL Server inclui um objeto <xref:System.Data.SqlClient.SqlConnection>, o Provedor de Dados .NET Framework para ODBC inclui um objeto <xref:System.Data.Odbc.OdbcConnection> e o Provedor de Dados .NET Framework para Oracle inclui um objeto <xref:System.Data.OracleClient.OracleConnection>.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Estabelecendo a conexão](../../../../docs/framework/data/adonet/establishing-the-connection.md)  
 Descreve como usar um **Conexão** objeto para estabelecer uma conexão a uma fonte de dados.  
  
 [Eventos de conexão](../../../../docs/framework/data/adonet/connection-events.md)  
 Descreve como usar um **InfoMessage** evento para recuperar mensagens informativas de uma fonte de dados.  
  
## <a name="see-also"></a>Consulte também

- [Cadeias de caracteres de conexão](../../../../docs/framework/data/adonet/connection-strings.md)
- [Pool de conexões](../../../../docs/framework/data/adonet/connection-pooling.md)
- [Comandos e parâmetros](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [DataAdapters e DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [Transações e simultaneidade](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)
- [Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
