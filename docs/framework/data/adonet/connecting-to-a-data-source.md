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
# <a name="connecting-to-a-data-source-in-adonet"></a>Conectando-se a uma fonte de dados no ADO.NET
No ADO.NET, você usa um **Conexão** objeto para se conectar a uma fonte de dados específico fornecendo informações de autenticação necessária em uma cadeia de caracteres de conexão. O **Conexão** objeto usado depende do tipo de fonte de dados.  
  
 Cada provedor de dados .NET Framework incluído no .NET Framework tem um objeto <xref:System.Data.Common.DbConnection>: o Provedor de Dados .NET Framework para OLE DB inclui um objeto <xref:System.Data.OleDb.OleDbConnection>, o Provedor de Dados .NET Framework para SQL Server inclui um objeto <xref:System.Data.SqlClient.SqlConnection>, o Provedor de Dados .NET Framework para ODBC inclui um objeto <xref:System.Data.Odbc.OdbcConnection> e o Provedor de Dados .NET Framework para Oracle inclui um objeto <xref:System.Data.OracleClient.OracleConnection>.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Estabelecendo a Conexão](../../../../docs/framework/data/adonet/establishing-the-connection.md)  
 Descreve como usar um **Conexão** objeto para estabelecer uma conexão com uma fonte de dados.  
  
 [Eventos de Conexão](../../../../docs/framework/data/adonet/connection-events.md)  
 Descreve como usar um **InfoMessage** evento para recuperar mensagens informativas de uma fonte de dados.  
  
## <a name="see-also"></a>Consulte também  
 [Cadeias de caracteres de Conexão](../../../../docs/framework/data/adonet/connection-strings.md)  
 [Pooling de Conexão](../../../../docs/framework/data/adonet/connection-pooling.md)  
 [Comandos e parâmetros](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [DataAdapters e DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Transações e simultaneidade](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
