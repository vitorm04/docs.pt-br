---
title: Rastreamento de dados no ADO.NET
ms.date: 03/30/2017
ms.assetid: a6a752a5-d2a9-4335-a382-b58690ccb79f
ms.openlocfilehash: 1b2ee679ce4b0d39b993b9081f428fe585ef7d92
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784894"
---
# <a name="data-tracing-in-adonet"></a>Rastreamento de dados no ADO.NET

O ADO.net apresenta a funcionalidade de rastreamento de dados interna com suporte dos provedores de dados .net para SQL Server, Oracle, OLE DB e ODBC, bem como o ADO.NET <xref:System.Data.DataSet>e os protocolos de rede SQL Server.

O rastreamento de chamadas à API de acesso a dados pode ajudar a diagnosticar os seguintes problemas:

- Incompatibilidade de esquema entre o programa cliente e o banco de dados.

- Problemas de biblioteca de rede ou indisponibilidade de banco de dados.

- SQL incorreto se embutido em código ou gerado por um aplicativo.

- Lógica de programação incorreta.

- Problemas resultantes da interação entre vários componentes do ADO.NET ou entre ADO.NET e seus próprios componentes.

Para dar suporte a diferentes tecnologias de rastreamento, o rastreamento é extensível, portanto, um desenvolvedor pode rastrear um problema em qualquer nível da pilha de aplicativos. Embora o rastreamento não seja um recurso ADO.NET, os provedores da Microsoft aproveitam as APIs generalizadas de rastreamento e instrumentação.

Para obter mais informações sobre como configurar e configurar o rastreamento gerenciado no ADO.NET, consulte [rastreamento de acesso a dados](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/hh880086(v=msdn.10)).

## <a name="accessing-diagnostic-information-in-the-extended-events-log"></a>Acessando informações de diagnóstico no log de eventos estendidos

No .NET Framework Provedor de Dados para SQL Server, o rastreamento de acesso a dados ([rastreamento de acesso a dados](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/hh880086(v=msdn.10))) foi atualizado para tornar mais fácil correlacionar eventos de cliente com informações de diagnóstico, como falhas de conexão, da conectividade do servidor informações de desempenho do aplicativo e do buffer do anel no log de eventos estendidos. Para obter informações sobre como ler o log de eventos estendidos, consulte [exibir dados de sessão de evento](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/hh710068(v=sql.110)).

Para operações de conexão, o ADO.NET enviará uma ID de conexão de cliente. Se a conexão falhar, você poderá acessar o buffer de anéis de conectividade ([solução de problemas de conectividade no SQL Server 2008 com o buffer de anéis de conectividade](https://go.microsoft.com/fwlink/?LinkId=207752)) e localizar o `ClientConnectionID` campo e obter informações de diagnóstico sobre a falha de conexão. As IDs de conexão de cliente serão registradas no buffer de anéis somente se ocorrer um erro. (Se uma conexão falhar antes de enviar o pacote de pré-logon, uma ID de conexão de cliente não será gerada.) A ID de conexão do cliente é um GUID de 16 bytes. Você também pode encontrar a ID de conexão do cliente na saída de destino de eventos estendidos, se a `client_connection_id` ação for adicionada a eventos em uma sessão de eventos estendidos. Você pode habilitar o rastreamento de acesso a dados e executar novamente o comando `ClientConnectionID` de conexão e observar o campo no rastreamento de acesso a dados, se precisar de mais assistência de diagnóstico de driver de cliente.

Você pode obter a ID de conexão do cliente programaticamente usando a `SqlConnection.ClientConnectionID` propriedade.

O `ClientConnectionID` está disponível para um <xref:System.Data.SqlClient.SqlConnection> objeto que estabelece com êxito uma conexão. Se uma tentativa de conexão falhar `ClientConnectionID` , o poderá estar `SqlException.ToString`disponível via.

O ADO.NET também envia uma ID de atividade específica do thread. A ID da atividade será capturada nas sessões de eventos estendidos se as sessões forem iniciadas com a opção TRACK_CAUSALITY habilitada. Para problemas de desempenho com uma conexão ativa, você pode obter a ID da atividade do rastreamento de acesso a dados`ActivityID` do cliente (campo) e, em seguida, localizar a ID da atividade na saída de eventos estendidos. A ID da atividade em eventos estendidos é um GUID de 16 bytes (não o mesmo que o GUID da ID de conexão do cliente) acrescentado com um número de sequência de quatro bytes. O número de sequência representa a ordem de uma solicitação dentro de um thread e indica a ordenação relativa de instruções de lote e RPC para o thread. O `ActivityID` atualmente é enviado opcionalmente para instruções de lote SQL e solicitações RPC quando o rastreamento de acesso a dados está habilitado e o bit de 18 no Word de configuração de rastreamento de acesso a dados é ativado.

Veja a seguir um exemplo que usa o Transact-SQL para iniciar uma sessão de eventos estendidos que será armazenada em um buffer de anéis e registrará a ID de atividade enviada de um cliente em operações RPC e em lote.

```sql
create event session MySession on server
add event connectivity_ring_buffer_recorded,
add event sql_statement_starting (action (client_connection_id)),
add event sql_statement_completed (action (client_connection_id)),
add event rpc_starting (action (client_connection_id)),
add event rpc_completed (action (client_connection_id))
add target ring_buffer with (track_causality=on)
```

## <a name="see-also"></a>Consulte também

- [Rastreamento de rede no .NET Framework](../../network-programming/network-tracing.md)
- [Rastreando e instrumentando aplicativos](../../debug-trace-profile/tracing-and-instrumenting-applications.md)
- [ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)
