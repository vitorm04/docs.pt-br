---
title: Rastreamento de dados no ADO.NET
ms.date: 03/30/2017
ms.assetid: a6a752a5-d2a9-4335-a382-b58690ccb79f
ms.openlocfilehash: 8f9388d084e9e598e43c0f871b21d05c053e77ce
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367161"
---
# <a name="data-tracing-in-adonet"></a>Rastreamento de dados no ADO.NET

ADO.NET apresenta a funcionalidade de rastreamento de dados internos que há suporte para os provedores de dados .NET para SQL Server, Oracle, OLE DB e ODBC, bem como o ADO.NET <xref:System.Data.DataSet>e os protocolos de rede do SQL Server.

Rastreamento de dados chamadas de API de acesso podem ajudar a diagnosticar os problemas a seguir:

- Incompatibilidade de esquema entre o programa cliente e o banco de dados.

- Indisponibilidade do banco de dados ou problemas de biblioteca de rede.

- SQL incorreta se rígida codificado ou gerado por um aplicativo.

- Lógica de programação incorreta.

- Problemas resultantes da interação entre os vários componentes do ADO.NET ou entre seus próprios componentes e o ADO.NET.

Para dar suporte a tecnologias diferentes de rastreamento, o rastreamento é extensível, para que um desenvolvedor pode rastrear um problema em qualquer nível da pilha do aplicativo. Embora o rastreamento não é um recurso somente do ADO.NET, provedores Microsoft tirar proveito de rastreamento generalizado e APIs de instrumentação.

Para obter mais informações sobre a configuração e configurando o rastreamento gerenciado no ADO.NET, consulte [acesso aos dados de rastreamento](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/hh880086(v=msdn.10)).

## <a name="accessing-diagnostic-information-in-the-extended-events-log"></a>Acessar informações de diagnóstico no Log de eventos estendidos

No [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] provedor de dados para o SQL Server, rastreamento de acesso a dados ([rastreamento de acesso a dados](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/hh880086(v=msdn.10))) foi atualizado para facilitar a mais fácil correlacionar eventos de cliente com informações de diagnóstico, tais como falhas de conexão das informações de desempenho de buffer e o aplicativo no log de eventos estendidos de anéis de conectividade do servidor. Para obter informações sobre como ler o log de eventos estendidos, consulte [exibir dados de sessão de evento](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/hh710068(v=sql.110)).

Para operações de conexão ADO.NET enviará um cliente de ID de conexão. Se a conexão falhar, você pode acessar o buffer de anéis de conectividade ([solução de problemas de conectividade no SQL Server 2008 com o Buffer de anéis de conectividade](https://go.microsoft.com/fwlink/?LinkId=207752)) e encontre o `ClientConnectionID` do campo e obter informações de diagnóstico o Falha na conexão. IDs de conexão de cliente são registradas no buffer de anéis somente se ocorrer um erro. (Se uma conexão falhar antes de enviar o pacote anterior ao logon, uma ID de conexão do cliente não será ser gerada.) A ID de conexão do cliente é um GUID de 16 bytes. Você também pode encontrar a conexão de cliente ID na saída de destino de eventos estendidos, se o `client_connection_id` ação for adicionada a eventos em uma sessão de eventos estendidos. Você pode habilitar o rastreamento de acesso de dados e execute novamente o comando de conexão e observar o `ClientConnectionID` campo no rastreamento de acesso a dados, se você precisar de mais assistência de diagnóstico de driver do cliente.

Você pode obter o cliente do ID de conexão programaticamente, usando o `SqlConnection.ClientConnectionID` propriedade.

O `ClientConnectionID` está disponível para um <xref:System.Data.SqlClient.SqlConnection> objeto que estabelece a uma conexão com êxito. Se uma tentativa de conexão falhar, `ClientConnectionID` podem estar disponíveis por meio de `SqlException.ToString`.

ADO.NET também envia uma ID de atividade específica de thread. A ID de atividade é capturada em sessões de eventos estendidas se as sessões são iniciadas com a opção TRACK_CAUSALITY habilitada. Para problemas de desempenho com uma conexão ativa, você pode obter a ID de atividade do rastreamento de acesso de dados do cliente (`ActivityID` campo) e, em seguida, localize a ID de atividade nas saídas dos eventos estendidos. A ID de atividade nos eventos estendidos é um GUID de 16 bytes (não o mesmo GUID para a ID de conexão do cliente) anexado com um número de sequência de quatro bytes. O número de sequência representa a ordem de uma solicitação dentro de um thread e indica a ordenação relativa de lote e as instruções RPC para o thread. O `ActivityID` é enviado no momento, opcionalmente para instruções SQL em lotes e solicitações do RPC quando o rastreamento de acesso de dados está habilitado e o 18º bit na palavra de configuração de rastreamento de acesso a dados está ativado.

A seguir está um exemplo que usa [!INCLUDE[tsql](../../../../includes/tsql-md.md)] para iniciar uma sessão de eventos estendidos que será armazenada em um buffer de anel e registrará a ID de atividade enviada de um cliente em operações em lote e RPC.

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

- [Rastreamento de rede no .NET Framework](../../../../docs/framework/network-programming/network-tracing.md)
- [Rastreando e instrumentando aplicativos](../../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
