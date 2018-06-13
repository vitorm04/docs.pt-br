---
title: Rastreamento de dados no ADO.NET
ms.date: 03/30/2017
ms.assetid: a6a752a5-d2a9-4335-a382-b58690ccb79f
ms.openlocfilehash: 6dd385cd58d1c8400c45139492d84e6ca4fe1bd7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758497"
---
# <a name="data-tracing-in-adonet"></a>Rastreamento de dados no ADO.NET
ADO.NET apresenta funcionalidade de rastreamento de dados interna que tem suporte pelo provedor de dados .NET para SQL Server, Oracle, OLE DB e ODBC, bem como o ADO.NET <xref:System.Data.DataSet>e os protocolos de rede do SQL Server.  
  
 Rastreamento de dados chamadas de API de acesso podem ajudar a diagnosticar os problemas a seguir:  
  
-   Incompatibilidade de esquema entre cliente e o banco de dados.  
  
-   Indisponibilidade do banco de dados ou problemas de biblioteca de rede.  
  
-   SQL incorreto se hard codificado ou gerado por um aplicativo.  
  
-   Lógica de programação incorretova.  
  
-   Problemas resultantes da interação entre os vários componentes do ADO.NET ou entre seus próprios componentes e ADO.NET.  
  
 Para dar suporte a tecnologias de rastreamento diferente, o rastreamento é extensível, para que um desenvolvedor pode rastrear um problema em qualquer nível da pilha do aplicativo. Embora o rastreamento não é um recurso somente ADO.NET, provedores Microsoft aproveitar generalizada de rastreamento e instrumentação APIs.  
  
 Para obter mais informações sobre a configuração e configurando o rastreamento gerenciado no ADO.NET, consulte [acesso aos dados de rastreamento](http://msdn.microsoft.com/library/hh880086.aspx).  
  
## <a name="accessing-diagnostic-information-in-the-extended-events-log"></a>Acessar informações de diagnóstico no Log de eventos estendidos  
 No [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] provedor de dados do SQL Server, rastreamento de acesso a dados ([rastreamento de acesso a dados](http://msdn.microsoft.com/library/hh880086.aspx)) foi atualizado para facilitar para correlacionar eventos do cliente com informações de diagnóstico, tais como falhas de conexão, do informações de desempenho de aplicativo e o buffer no log de eventos estendidos do anel de conectividade do servidor. Para obter informações sobre como ler o log de eventos estendidos, consulte [exibir dados de sessão de evento](http://msdn.microsoft.com/library/hh710068\(SQL.110\).aspx).  
  
 Para operações de conexão ADO.NET enviará um cliente ID de conexão. Se a conexão falhar, você pode acessar o buffer de anéis de conectividade ([solução de problemas de conectividade no SQL Server 2008 com o Buffer de anéis de conectividade](http://go.microsoft.com/fwlink/?LinkId=207752)) e localize o `ClientConnectionID` campo e obter informações de diagnóstico o Falha na conexão. As IDs de conexão de cliente são registradas no buffer de anéis se ocorrer um erro. (Se uma conexão falhar antes de enviar o pacote anterior ao logon, uma ID de conexão do cliente não será gerada.) A ID de conexão do cliente é um GUID de 16 bytes. Você também pode encontrar a conexão de cliente ID na saída de destino de eventos estendidos, se o `client_connection_id` ação for adicionada aos eventos em uma sessão de eventos estendidos. Você pode habilitar o rastreamento de acesso de dados e execute novamente o comando de conexão e observar o `ClientConnectionID` campo no rastreamento de acesso a dados, se você precisar de mais assistência de diagnóstico de driver do cliente.  
  
 Você pode obter o cliente ID de conexão programaticamente, usando o `SqlConnection.ClientConnectionID` propriedade.  
  
 O `ClientConnectionID` está disponível para um <xref:System.Data.SqlClient.SqlConnection> objeto que estabelece com êxito uma conexão. Se uma tentativa de conexão falhar, `ClientConnectionID` podem estar disponíveis por meio de `SqlException.ToString`.  
  
 ADO.NET também envia uma ID de atividade específica do thread. A ID de atividade é capturada em sessões de eventos estendidas se as sessões são iniciadas com a opção de TRACK_CAUSAILITY habilitada. Para problemas de desempenho com uma conexão ativa, você pode obter a ID de atividade de rastreamento de acesso de dados do cliente (`ActivityID` campo) e, em seguida, localize a ID de atividade na saída de eventos estendidos. A ID de atividade nos eventos estendidos é um GUID de 16 bytes (não o mesmo GUID para a ID de conexão do cliente) anexado com um número de sequência de quatro bytes. O número de sequência representa a ordem de uma solicitação dentro de um thread e indica a ordenação relativa de lote e as instruções RPC para o thread. O `ActivityID` é enviado atualmente opcionalmente para instruções SQL em lotes e solicitações do RPC quando o rastreamento de acesso de dados está habilitado e o 18º bit na palavra de configuração de rastreamento de acesso a dados está desativado.  
  
 A seguir está um exemplo que usa [!INCLUDE[tsql](../../../../includes/tsql-md.md)] para iniciar uma sessão de eventos estendidos que será armazenada em um buffer de anel e registrará a ID de atividade enviada de um cliente em operações em lote e RPC.  
  
```  
create event session MySession on server   
add event connectivity_ring_buffer_recorded,   
add event sql_statement_starting (action (client_connection_id)),   
add event sql_statement_completed (action (client_connection_id)),   
add event rpc_starting (action (client_connection_id)),   
add event rpc_completed (action (client_connection_id))  
add target ring_buffer with (track_causality=on)  
```  
  
## <a name="see-also"></a>Consulte também  
 [Rastreamento de rede no .NET Framework](../../../../docs/framework/network-programming/network-tracing.md)  
 [Rastreando e instrumentando aplicativos](../../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
