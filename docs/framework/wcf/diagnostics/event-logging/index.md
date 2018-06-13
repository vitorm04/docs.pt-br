---
title: Registro de eventos em log no WCF
ms.date: 03/30/2017
helpviewer_keywords:
- event logging [WCF]
ms.assetid: aac0530d-f44c-45a1-bada-e30e0677b41f
ms.openlocfilehash: ea0e6f3dc66bf40d631077c0dce20ea46f3a6688
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33804931"
---
# <a name="event-logging-in-wcf"></a>Registro de eventos em log no WCF
Windows Communication Foundation (WCF) rastreia eventos internos no log de eventos do Windows.  
  
## <a name="viewing-event-logs"></a>Exibindo Logs de eventos  
 O log de eventos é habilitado automaticamente por padrão, e não há nenhum mecanismo para desabilitá-lo. Eventos registrados pelo WCF podem ser exibidos usando o Visualizador de eventos. Para iniciar essa ferramenta, clique em **iniciar**, clique em **painel de controle**, clique duas vezes em **ferramentas administrativas**e, em seguida, clique duas vezes em **Visualizador de eventos**.  
  
### <a name="application-event-log"></a>Log de eventos do aplicativo  
 O **Log de eventos do aplicativo** contém a maioria dos eventos gerados pelo WCF. A maioria das entradas de indica que um determinado recurso não foi inicializado para um aplicativo. Os exemplos incluem:  
  
-   Log de mensagem/rastreamento: WCF grava um evento no log de eventos quando a falha de rastreamento e registro em log de mensagem. No entanto, não cada falha de rastreamento dispara um evento. Para impedir que o log de eventos que estão sendo completamente preenchido com falhas de rastreamentos, o WCF implementa um período de indisponibilidade de 10 minutos para um evento. Isso significa que se WCF grava uma falha de rastreamento para o log de eventos, ele não executará novamente pelo menos 10 minutos.  
  
-   Compartilhado ouvinte: O serviço de compartilhamento de porta de TCP do WCF registra um evento quando ele não for iniciado.  
  
-   [!INCLUDE[infocard](../../../../../includes/infocard-md.md)]: Logs de eventos quando o serviço não for iniciado.  
  
-   Eventos críticos e de erro, como falhas de inicialização ou falha  
  
-   O log de mensagem ativado: Logs de eventos quando a mensagem de log está ativada. Isso é para notificar o administrador que informações confidenciais, específicos do aplicativo podem ser registradas em cabeçalhos e corpos.  
  
-   Um evento é registrado quando o `enableLoggingKnownPII` atributo o `machineSettings` elemento do `machine.config` arquivo está definido. Esse atributo especifica se qualquer aplicativo em execução no computador tem permissão para efetuar conhecidas informações de identificação pessoal (PII).  
  
-   Se o `logKnownPii` atributo no `app.config` ou `web.config` arquivo é definido como `true` para um aplicativo específico ativar o log de PII, mas o `enableLoggingKnownPII` atributo no `machineSettings` elemento do `machine.config` arquivo está definido para `false`, um evento é registrado. Além disso, se ambos os `logKnownPii` e `enableLoggingKnownPII` são definidos como `true`, e o evento é registrado. Para obter mais informações sobre essas configurações, consulte a seção de segurança de [Configurando o log de mensagens](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) tópico.  
  
### <a name="security-event-log"></a>Log de eventos de segurança  
 O **Log de eventos de segurança** contém eventos de auditoria de segurança que são registrados pelo WCF.  
  
### <a name="system-event-log"></a>Log de eventos do sistema  
 WCF não fazer nada **Log de eventos do sistema**.  
  
### <a name="event-log-entries"></a>Entradas de Log de eventos  
 O **fonte** de um evento é o nome do assembly que gera a entrada de log.  
  
 O tipo de uma entrada de log de eventos é usado para indicar a severidade de um evento. Cada evento deve ser de um único tipo, o aplicativo indica quando o evento informa. O Visualizador de eventos usa esse tipo para determinar qual ícone será exibido na exibição de lista do log. O tipo de evento diferente de uma entrada de log de eventos, consulte <xref:System.Diagnostics.EventLogEntryType>.  
  
 Quando você clica em "mais informações" ao exibir um evento no Visualizador de eventos, o Visualizador de eventos pode enviar informações pela Internet. Para obter mais informações, consulte a Ajuda do Visualizador de eventos.  
  
## <a name="see-also"></a>Consulte também  
 [Administração e diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [Referência geral de eventos](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
