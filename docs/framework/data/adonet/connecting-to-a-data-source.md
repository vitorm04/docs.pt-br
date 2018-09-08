---
title: Conectando-se a uma fonte de dados no ADO.NET
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: f5788b9b0b19f32d03c917575db7b3f40324c0a2
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44189258"
---
# <a name="connecting-to-a-data-source-in-adonet"></a>Conectando-se a uma fonte de dados no ADO.NET
No ADO.NET você usa um **Conexão** objeto para se conectar a uma fonte de dados específica fornecendo as informações de autenticação necessárias em uma cadeia de caracteres de conexão. O **Conexão** objeto que você usa depende do tipo de fonte de dados.  
  
 Cada provedor de dados .NET Framework incluído no .NET Framework tem um objeto <xref:System.Data.Common.DbConnection>: o Provedor de Dados .NET Framework para OLE DB inclui um objeto <xref:System.Data.OleDb.OleDbConnection>, o Provedor de Dados .NET Framework para SQL Server inclui um objeto <xref:System.Data.SqlClient.SqlConnection>, o Provedor de Dados .NET Framework para ODBC inclui um objeto <xref:System.Data.Odbc.OdbcConnection> e o Provedor de Dados .NET Framework para Oracle inclui um objeto <xref:System.Data.OracleClient.OracleConnection>.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Estabelecendo a conexão](../../../../docs/framework/data/adonet/establishing-the-connection.md)  
 Descreve como usar um **Conexão** objeto para estabelecer uma conexão a uma fonte de dados.  
  
 [Eventos de Conexão](../../../../docs/framework/data/adonet/connection-events.md)  
 Descreve como usar um **InfoMessage** evento para recuperar mensagens informativas de uma fonte de dados.  
  
## <a name="see-also"></a>Consulte também  
 [Cadeia de Conexão](../../../../docs/framework/data/adonet/connection-strings.md)  
 [Pooling de Conexão](../../../../docs/framework/data/adonet/connection-pooling.md)  
 [Comandos e parâmetros](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [DataAdapters e DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Transações e simultaneidade](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
