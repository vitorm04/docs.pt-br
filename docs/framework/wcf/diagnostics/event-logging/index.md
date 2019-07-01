---
title: Registro de eventos em log no WCF
ms.date: 03/30/2017
helpviewer_keywords:
- event logging [WCF]
ms.assetid: aac0530d-f44c-45a1-bada-e30e0677b41f
ms.openlocfilehash: c4f73480208fbf900bb8742eb6d7b2e2c0e6a4ff
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67486622"
---
# <a name="event-logging-in-wcf"></a>Registro de eventos em log no WCF
Windows Communication Foundation (WCF) rastreia eventos internos no log de eventos do Windows.  
  
## <a name="viewing-event-logs"></a>Exibindo Logs de eventos  
 O log de eventos é habilitado automaticamente por padrão, e não há nenhum mecanismo para desabilitá-lo. Eventos registrados pelo WCF podem ser exibidos usando o Visualizador de eventos. Para iniciar essa ferramenta, clique **inicie**, clique em **painel de controle**, clique duas vezes em **ferramentas administrativas**e, em seguida, clique duas vezes em **Visualizador de eventos**.  
  
### <a name="application-event-log"></a>Log de Eventos do Aplicativo  
 O **Log de eventos do aplicativo** contém a maioria dos eventos gerados pelo WCF. A maioria das entradas indica que um determinado recurso não foi inicializado para um aplicativo. Os exemplos incluem:  
  
- Registro em log/rastreamento de mensagem: WCF grava um evento no log de eventos quando a falha de rastreamento e registro em log de mensagem. No entanto, nem toda falha de rastreamento dispara um evento. Para impedir que o log de eventos que estão sendo totalmente preenchido com falhas de rastreamentos, o WCF implementa um período de indisponibilidade de 10 minutos para tal evento. Isso significa que se WCF grava uma falha de rastreamento no log de eventos, ele não executará novamente pelo menos 10 minutos.  
  
- Ouvinte compartilhado: O serviço de compartilhamento de porta de TCP do WCF registra um evento quando ele falha ao iniciar.  
  
- CardSpace: Logs de eventos quando o serviço não for iniciado.  
  
- Eventos críticos e de erro, como falhas de inicialização ou falhas  
  
- Log de mensagem ativado: Logs de eventos quando o log de mensagem está ativado. Isso serve para notificar o administrador que informações confidenciais, específicos do aplicativo podem ser registradas no corpo e cabeçalhos de mensagem.  
  
- Um evento é registrado quando o `enableLoggingKnownPII` de atributo na `machineSettings` elemento da `machine.config` arquivo está definido. Esse atributo especifica se qualquer aplicativo em execução no computador tem permissão para efetuar o conhecido informações de identificação pessoal (PII).  
  
- Se o `logKnownPii` atributo em qualquer um a `app.config` ou `web.config` arquivo é definido como `true` para um aplicativo específico ativar o registro em log o PII, mas o `enableLoggingKnownPII` atributo no `machineSettings` elemento do `machine.config` arquivo é definido para `false`, um evento é registrado. Além disso, se os dois `logKnownPii` e `enableLoggingKnownPII` são definidos como `true`, e o evento é registrado. Para obter mais informações sobre essas definições de configuração, consulte a seção de segurança de [Configurando o log de mensagens](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) tópico.  
  
### <a name="security-event-log"></a>Log de eventos de segurança  
 O **Log de eventos de segurança** contém eventos de auditoria de segurança que são registrados em log pelo WCF.  
  
### <a name="system-event-log"></a>Log de eventos do sistema  
 O WCF não fizer nada **Log de eventos do sistema**.  
  
### <a name="event-log-entries"></a>Entradas de Log de eventos  
 O **origem** de um evento é o nome do assembly que gera a entrada de log.  
  
 O tipo de uma entrada de log de eventos é usado para indicar a severidade de um evento. Cada evento deve ser de um único tipo, o aplicativo indica quando ele relata o evento. O Visualizador de eventos usa esse tipo para determinar qual ícone será exibido na exibição de lista do log. Para o tipo de evento diferente de uma entrada de log de eventos, consulte <xref:System.Diagnostics.EventLogEntryType>.  
  
 Quando você clica em "obter mais informações" ao exibir um evento no Visualizador de eventos, o Visualizador de eventos pode enviar informações pela Internet. Para obter mais informações, consulte a Ajuda do Visualizador de eventos.  
  
## <a name="see-also"></a>Consulte também

- [Administração e diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)
- [Referência geral de eventos](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
