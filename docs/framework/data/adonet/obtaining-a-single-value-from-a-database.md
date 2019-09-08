---
title: Obter um único valor de um banco de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.openlocfilehash: fb43d21546a0e98e87aab23db9213309b62320b9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794742"
---
# <a name="obtaining-a-single-value-from-a-database"></a>Obter um único valor de um banco de dados
Talvez seja necessário retornar informações do banco de dados que seja simplesmente um único valor em vez de na forma de um fluxo de tabela ou data. Por exemplo, talvez você queira retornar o resultado de uma função de agregação, como Count\*(), Sum (Price) ou AVG (quantity). O objeto **Command** fornece a capacidade de retornar valores únicos usando o método **ExecuteScalar** . O método **ExecuteScalar** retorna, como um valor escalar, o valor da primeira coluna da primeira linha do conjunto de resultados.  
  
 O exemplo de código a seguir insere um novo valor no banco de <xref:System.Data.SqlClient.SqlCommand>dados usando um. O <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> método é usado para retornar o valor da coluna de identidade para o registro inserido.  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- [Comandos e parâmetros](commands-and-parameters.md)
- [Executar um comando](executing-a-command.md)
- [DbConnection, DbCommand e DbException](dbconnection-dbcommand-and-dbexception.md)
- [ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)
