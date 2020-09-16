---
title: Rastreamento de dados
ms.date: 03/30/2017
ms.assetid: a6a752a5-d2a9-4335-a382-b58690ccb79f
ms.openlocfilehash: 5fe04d6b6146079db7d4e110a94ced361949998c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557104"
---
# <a name="data-tracing-in-adonet"></a>Rastreamento de dados no ADO.NET

O ADO.NET apresenta a funcionalidade de rastreamento de dados interna com suporte dos provedores de dados .NET para SQL Server, Oracle, OLE DB e ODBC, bem como o ADO.NET <xref:System.Data.DataSet> e os protocolos de rede SQL Server.

O rastreamento de chamadas à API de acesso a dados pode ajudar a diagnosticar os seguintes problemas:

- Incompatibilidade de esquema entre o programa cliente e o banco de dados.

- Problemas de biblioteca de rede ou indisponibilidade de banco de dados.

- SQL incorreto se embutido em código ou gerado por um aplicativo.

- Lógica de programação incorreta.

- Problemas resultantes da interação entre vários componentes do ADO.NET ou entre ADO.NET e seus próprios componentes.

Para dar suporte a diferentes tecnologias de rastreamento, o rastreamento é extensível, portanto, um desenvolvedor pode rastrear um problema em qualquer nível da pilha de aplicativos. Embora o rastreamento não seja um recurso ADO.NET, os provedores da Microsoft aproveitam as APIs generalizadas de rastreamento e instrumentação.

Para obter mais informações sobre como configurar e configurar o rastreamento gerenciado no ADO.NET, consulte [rastreamento de acesso a dados](/previous-versions/sql/sql-server-2012/hh880086(v=msdn.10)).

## <a name="accessing-diagnostic-information-in-the-extended-events-log"></a>Acessar informações de diagnóstico nos logs de eventos estendidos

No .NET Framework Provedor de Dados para SQL Server, o rastreamento de acesso a dados ([rastreamento de acesso a dados](/previous-versions/sql/sql-server-2012/hh880086(v=msdn.10))) foi atualizado para facilitar a correlação de eventos de cliente com informações de diagnóstico, como falhas de conexão, do buffer de anéis de conectividade do servidor e das informações de desempenho do aplicativo no log de eventos estendidos. Para obter mais informações sobre como ler o log de eventos estendidos, consulte [View Event Session Data](/previous-versions/sql/sql-server-2012/hh710068(v=sql.110)).

Para operações de conexão, o ADO.NET enviará uma ID de conexão de cliente. Se a conexão falhar, você poderá acessar o buffer de anéis de conectividade ([solução de problemas de conectividade no SQL Server 2008 com o buffer de anéis de conectividade](/archive/blogs/sql_protocols/connectivity-troubleshooting-in-sql-server-2008-with-the-connectivity-ring-buffer)) e localizar o `ClientConnectionID` campo e obter informações de diagnóstico sobre a falha de conexão. As IDs de conexão de cliente estarão registradas no buffer de anéis se um erro ocorrer. (Se uma conexão falhar antes de enviar o pacote anterior ao logon, uma ID conexão de cliente não será gerada.) A ID de conexão de cliente é um GUID de 16 bytes. Você também pode encontrar a ID de conexão do cliente na saída de destino de eventos estendidos, se a `client_connection_id` ação for adicionada a eventos em uma sessão de eventos estendidos. Você pode habilitar o rastreamento de acesso a dados e executar novamente o comando de conexão e observar o `ClientConnectionID` campo no rastreamento de acesso a dados, se precisar de mais assistência de diagnóstico de driver de cliente.

Você pode obter a ID de conexão do cliente programaticamente usando a `SqlConnection.ClientConnectionID` propriedade.

O `ClientConnectionID` está disponível para um <xref:System.Data.SqlClient.SqlConnection> objeto que estabelece com êxito uma conexão. Se uma tentativa de conexão falhar, o `ClientConnectionID` poderá estar disponível via `SqlException.ToString` .

O ADO.NET também envia uma ID de atividade específica do thread. A ID da atividade será capturada nas sessões de eventos estendidos se as sessões forem iniciadas com a opção TRACK_CAUSALITY habilitada. Para problemas de desempenho com uma conexão ativa, você poderá obter a ID de atividade do rastreamento de acesso a dados do cliente (campo `ActivityID`) e, em seguida, localizar a ID de atividade nas saídas dos eventos estendidos. A ID de atividade nos eventos estendidos é um GUID de 16 bytes (não é o mesmo que o GUID da ID de conexão do cliente) com um número sequencial de quatro bytes. O número de sequência representa a ordem de uma solicitação dentro de um thread e indica a ordenação relativa de lote e as instruções RPC para o thread. O `ActivityID` atualmente é enviado opcionalmente para instruções de lote SQL e solicitações RPC quando o rastreamento de acesso a dados está habilitado e o bit de 18 no Word de configuração de rastreamento de acesso a dados é ativado.

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

## <a name="see-also"></a>Confira também

- [Rastreamento de rede no .NET Framework](../../network-programming/network-tracing.md)
- [Como rastrear e instrumentar aplicativos](../../debug-trace-profile/tracing-and-instrumenting-applications.md)
- [Visão geral do ADO.NET](ado-net-overview.md)
