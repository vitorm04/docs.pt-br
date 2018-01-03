---
title: "Obter um único valor de um banco de dados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 09231a360408efe3a167a9e613fdf85631c0be52
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="obtaining-a-single-value-from-a-database"></a>Obter um único valor de um banco de dados
Para obter informações de banco de dados de retorno é simplesmente um único valor em vez de na forma de um fluxo de dados de tabela ou talvez seja necessário. Por exemplo, você talvez queira retornar o resultado de uma função de agregação, como contagem (\*), Sum, ou AVG(Quantity). O **comando** objeto fornece a capacidade de retornar valores únicos usando o **ExecuteScalar** método. O **ExecuteScalar** método retorna, como um valor escalar, o valor da primeira coluna da primeira linha do conjunto de resultados.  
  
 O exemplo de código a seguir insere um novo valor no banco de dados usando um <xref:System.Data.SqlClient.SqlCommand>. O <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> método é usado para retornar o valor da coluna de identidade para o registro inserido.  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Comandos e parâmetros](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Executar um comando](../../../../docs/framework/data/adonet/executing-a-command.md)  
 [DbConnection, DbCommand e DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
