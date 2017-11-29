---
title: "Referência de evento de rastreamento analítico"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: analytic tracing [WCF]. reference
ms.assetid: e44540cf-44a1-4efc-b965-7fbfd2131d73
caps.latest.revision: "50"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3b47456ecea86652e80bb60f155bffd6100e1fc7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="analytic-trace-event-reference"></a>Referência de evento de rastreamento analítico
A tabela a seguir define os níveis de eventos, identificadores e as mensagens associadas a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] rastreamento analítico.  
  
## <a name="event-reference"></a>Referência de eventos  
  
|ID do evento|Evento em nível|Mensagem de evento|Palavras-chave|  
|--------------|-----------------|-------------------|--------------|  
|[131 - BufferPoolAllocation](../../../../../docs/framework/wcf/diagnostics/etw/131-bufferpoolallocation.md)|Detalhado|Alocando %1 Bytes de pool.|Infraestrutura|  
|[132 - BufferPoolChangeQuota](../../../../../docs/framework/wcf/diagnostics/etw/132-bufferpoolchangequota.md)|Detalhado|BufferPool de tamanho %1, alterando a cota em %2.|Infraestrutura|  
|[133 - ActionItemScheduled](../../../../../docs/framework/wcf/diagnostics/etw/133-actionitemscheduled.md)|Detalhado|E/s de Thread do Agendador retorno de chamada invocado.|Infraestrutura|  
|[134 - ActionItemCallbackInvoked](../../../../../docs/framework/wcf/diagnostics/etw/134-actionitemcallbackinvoked.md)|Detalhado|E/s de Thread do Agendador retorno de chamada invocado.|Infraestrutura|  
|[201 - ClientMessageInspectorAfterReceiveInvoked](../../../../../docs/framework/wcf/diagnostics/etw/201-clientmessageinspectorafterreceiveinvoked.md)|Informações|O Dispatcher invocou 'AfterReceiveReply' em um ClientMessageInspector do tipo '%1'.|Solução de problemas, ServiceModel|  
|[202 - ClientMessageInspectorBeforeSendInvoked](../../../../../docs/framework/wcf/diagnostics/etw/202-clientmessageinspectorbeforesendinvoked.md)|Informações|O Dispatcher invocou 'BeforeSendRequest' em um ClientMessageInspector do tipo '%1'.|Solução de problemas, ServiceModel|  
|[203 - ClientParameterInspectorAfterCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/203-clientparameterinspectoraftercallinvoked.md)|Informações|O Dispatcher invocou 'AfterCall' em um ClientParameterInspector. do tipo '%1'.|Solução de problemas, ServiceModel|  
|[204 - ClientParameterInspectorBeforeCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/204-clientparameterinspectorbeforecallinvoked.md)|Informações|O Dispatcher invocou 'BeforeCall' em um ClientParameterInspector do tipo '%1'.|Solução de problemas, ServiceModel|  
|[205 - OperationInvoked](../../../../../docs/framework/wcf/diagnostics/etw/205-operationinvoked.md)|Informações|Um OperationInvoker invocou o método '%1'.|EndToEndMonitoring, solução de problemas, ServiceModel|  
|[206 - ErrorHandlerInvoked](../../../../../docs/framework/wcf/diagnostics/etw/206-errorhandlerinvoked.md)|Informações|O Dispatcher invocou um ErrorHandler do tipo '%1' com uma exceção do tipo '%3'.  ErrorHandled = = '%2'.|Solução de problemas, ServiceModel|  
|[207 - FaultProviderInvoked](../../../../../docs/framework/wcf/diagnostics/etw/207-faultproviderinvoked.md)|Informações|O Dispatcher invocou um FaultProvider do tipo '%1' com uma exceção do tipo '%2'.|Solução de problemas, ServiceModel|  
|[208 - MessageInspectorAfterReceiveInvoked](../../../../../docs/framework/wcf/diagnostics/etw/208-messageinspectorafterreceiveinvoked.md)|Informações|O Dispatcher invocou 'AfterReceiveReply' em um MessageInspector do tipo '%1'.|Solução de problemas, ServiceModel|  
|[209 - MessageInspectorBeforeSendInvoked](../../../../../docs/framework/wcf/diagnostics/etw/209-messageinspectorbeforesendinvoked.md)|Informações|O Dispatcher invocou 'BeforeSendRequest' em um MessageInspector do tipo '%1'.|Solução de problemas, ServiceModel|  
|[210 - MessageThrottleExceeded](../../../../../docs/framework/wcf/diagnostics/etw/210-messagethrottleexceeded.md)|Aviso|Foi atingido o limite de restrição '%1' de '%2'.|HealthMonitoring, EndToEndMonitoring, solução de problemas, ServiceModel|  
|[211 - ParameterInspectorAfterCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/211-parameterinspectoraftercallinvoked.md)|Informações|O Dispatcher invocou 'AfterCall' em um ParameterInspector do tipo '%1'.|Solução de problemas, ServiceModel|  
|[212 - ParameterInspectorBeforeCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/212-parameterinspectorbeforecallinvoked.md)|Informações|O Dispatcher invocou 'BeforeCall' em um ParameterInspector do tipo '%1'.|Solução de problemas, ServiceModel|  
|[213 - ServiceHostStarted](../../../../../docs/framework/wcf/diagnostics/etw/213-servicehoststarted.md)|LogAlways|ServiceHost iniciado: '%1'.|HealthMonitoring, EndToEndMonitoring, solução de problemas, ServiceModel|  
|[214 - OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md)|Informações|Um OperationInvoker concluiu a chamada ao método '%1'.  A duração da chamada de método foi '%2' ms.|HealthMonitoring, EndToEndMonitoring, solução de problemas, ServiceModel|  
|[215 - MessageReceivedByTransport](../../../../../docs/framework/wcf/diagnostics/etw/215-messagereceivedbytransport.md)|Informações|O transporte recebeu uma mensagem de '%1'.|Solução de problemas, ServiceModel|  
|[216 - MessageSentByTransport](../../../../../docs/framework/wcf/diagnostics/etw/216-messagesentbytransport.md)|Informações|O transporte enviou uma mensagem para '%1'.|Solução de problemas, ServiceModel|  
|[217 - ClientOperationPrepared](../../../../../docs/framework/wcf/diagnostics/etw/217-clientoperationprepared.md)|Informações|O cliente está executando a operação '%1' definida no contrato '%2'. A mensagem será enviada para '%3'.|Solução de problemas, ServiceModel|  
|[218 - ClientOperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/218-clientoperationcompleted.md)|Informações|O cliente concluiu a execução da operação '%1' definida no contrato '%2'. A mensagem foi enviada para '%3'.|Solução de problemas, ServiceModel|  
|[219 - ServiceException](../../../../../docs/framework/wcf/diagnostics/etw/219-serviceexception.md)|Erro|Ocorreu uma exceção sem tratamento do tipo '%2' durante o processamento de mensagem.  ToString completo da exceção: %1.|HealthMonitoring, EndToEndMonitoring, solução de problemas, ServiceModel|  
|[220 - MessageSentToTransport](../../../../../docs/framework/wcf/diagnostics/etw/220-messagesenttotransport.md)|Informações|O Dispatcher enviou uma mensagem para o transporte. ID de correlação = = '%1'.|EndToEndMonitoring, solução de problemas, ServiceModel|  
|[221 - MessageReceivedFromTransport](../../../../../docs/framework/wcf/diagnostics/etw/221-messagereceivedfromtransport.md)|Informações|O Dispatcher recebeu uma mensagem do transporte. ID de correlação = = '%1'.|EndToEndMonitoring, solução de problemas, ServiceModel|  
|[222 - OperationFailed](../../../../../docs/framework/wcf/diagnostics/etw/222-operationfailed.md)|Aviso|O método '%1' gerou uma exceção sem tratamento quando invocado pelo OperationInvoker. A duração da chamada de método foi '%2' ms.|HealthMonitoring, EndToEndMonitoring, solução de problemas, ServiceModel|  
|[223 - OperationFaulted](../../../../../docs/framework/wcf/diagnostics/etw/223-operationfaulted.md)|Aviso|O método '%1' gerou uma FaultException quando invocado pelo OperationInvoker. A duração da chamada de método foi '%2' ms.|HealthMonitoring, EndToEndMonitoring, solução de problemas, ServiceModel|  
|[224 - MessageThrottleAtSeventyPercent](../../../../../docs/framework/wcf/diagnostics/etw/224-messagethrottleatseventypercent.md)|Aviso|O limite de restrição '%1' de '%2' é de 70%.|HealthMonitoring, EndToEndMonitoring, solução de problemas, ServiceModel|  
|[226 - IdleServicesClosed](../../../../../docs/framework/wcf/diagnostics/etw/226-idleservicesclosed.md)|LogAlways|serviços ociosos %1 total %2 serviços ativados fechados.|HealthMonitoring WebHost|  
|[301 - UserDefinedErrorOccurred](../../../../../docs/framework/wcf/diagnostics/etw/301-userdefinederroroccurred.md)|Erro|Nome: '%1', referência: '%2', carga: %3.|UserEvents, HealthMonitoring, EndToEndMonitoring, solução de problemas, ServiceModel|  
|[302 - UserDefinedWarningOccurred](../../../../../docs/framework/wcf/diagnostics/etw/302-userdefinedwarningoccurred.md)|Aviso|Nome: '%1', referência: '%2', carga: %3.|UserEvents, HealthMonitoring, EndToEndMonitoring, solução de problemas, ServiceModel|  
|[303 - UserDefinedInformationEventOccured](../../../../../docs/framework/wcf/diagnostics/etw/303-userdefinedinformationeventoccured.md)|Informações|Nome: '%1', referência: '%2', carga: %3.|UserEvents, HealthMonitoring, EndToEndMonitoring, solução de problemas, ServiceModel|  
|[401 - StopSignPostEvent](../../../../../docs/framework/wcf/diagnostics/etw/401-stopsignpostevent.md)|Informações|Limite de atividade.|Solução de problemas|  
|[402 - StartSignpostEvent](../../../../../docs/framework/wcf/diagnostics/etw/402-startsignpostevent.md)|Informações|Limite de atividade.|Solução de problemas|  
|[403 - SuspendSignpostEvent](../../../../../docs/framework/wcf/diagnostics/etw/403-suspendsignpostevent.md)|Informações|Limite de atividade.|Solução de problemas|  
|[404 - ResumeSignpostEvent](../../../../../docs/framework/wcf/diagnostics/etw/404-resumesignpostevent.md)|Informações|Limite de atividade.|Solução de problemas|  
|[451 - MessageLogInfo](../../../../../docs/framework/wcf/diagnostics/etw/451-messageloginfo.md)|Informações|%1|Solução de problemas, WCFMessageLogging|  
|[452 - MessageLogWarning](../../../../../docs/framework/wcf/diagnostics/etw/452-messagelogwarning.md)|Aviso|%1|Solução de problemas, WCFMessageLogging|  
|[499 - TransferEmitted](../../../../../docs/framework/wcf/diagnostics/etw/499-transferemitted.md)|LogAlways|Evento de transferência emitido.|Solução de problemas, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging|  
|[501 - CompilationStart](../../../../../docs/framework/wcf/diagnostics/etw/501-compilationstart.md)|Informações|Iniciar a compilação.|WebHost|  
|[502 - CompilationStop](../../../../../docs/framework/wcf/diagnostics/etw/502-compilationstop.md)|Informações|Finalizar a compilação.|WebHost|  
|[503 - ServiceHostFactoryCreationStart](../../../../../docs/framework/wcf/diagnostics/etw/503-servicehostfactorycreationstart.md)|Informações|ServiceHostFactory começar a criação.|WebHost|  
|[504 - ServiceHostFactoryCreationStop](../../../../../docs/framework/wcf/diagnostics/etw/504-servicehostfactorycreationstop.md)|Informações|Criação de end ServiceHostFactory.|WebHost|  
|[505 - CreateServiceHostStart](../../../../../docs/framework/wcf/diagnostics/etw/505-createservicehoststart.md)|Informações|Começar CreateServiceHost.|WebHost|  
|[506 - CreateServiceHostStop](../../../../../docs/framework/wcf/diagnostics/etw/506-createservicehoststop.md)|Informações|CreateServiceHost final.|WebHost|  
|[507 - HostedTransportConfigurationManagerConfigInitStart](../../../../../docs/framework/wcf/diagnostics/etw/507-hostedtransportconfigurationmanagerconfiginitstart.md)|Informações|Inicialização de configuração de hostedtransportconfigurationmanager.|WebHost|  
|[508 - HostedTransportConfigurationManagerConfigInitStop](../../../../../docs/framework/wcf/diagnostics/etw/508-hostedtransportconfigurationmanagerconfiginitstop.md)|Informações|Inicialização de configuração de final de HostedTransportConfigurationManager.|WebHost|  
|[509 - ServiceHostOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/509-servicehostopenstart.md)|Informações|Inicialização de configuração de final de HostedTransportConfigurationManager.|ServiceHost|  
|[510 - ServiceHostOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/510-servicehostopenstop.md)|Informações|Abrir ServiceHost concluída.|ServiceHost|  
|[513 - WebHostRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/513-webhostrequeststart.md)|Informações|Recebida solicitação com o caminho virtual '%2' de AppDomain '%1'.|WebHost|  
|[514 - WebHostRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/514-webhostrequeststop.md)|Informações|WebHostRequest parar.|WebHost|  
|[601 - CBAEntryRead](../../../../../docs/framework/wcf/diagnostics/etw/601-cbaentryread.md)|Detalhado|Endereço relativo do elemento ServiceActivation processado: '%1', normalizado endereço relativo '%2'.||  
|[602 - CBAMatchFound](../../../../../docs/framework/wcf/diagnostics/etw/602-cbamatchfound.md)|Detalhado|Solicitação de entrada corresponde a um elemento ServiceActivation com endereço '%1'.||  
|[603 - AspNetRoutingService](../../../../../docs/framework/wcf/diagnostics/etw/603-aspnetroutingservice.md)|Detalhado|Solicitação de entrada corresponde a um serviço WCF definido na rota Asp.Net com endereço %1.|RoutingServices|  
|[604 - AspNetRoute](../../../../../docs/framework/wcf/diagnostics/etw/604-aspnetroute.md)|Detalhado|Uma nova rota Asp.Net '%1' com serviceType '%2' e serviceHostFactoryType '%3' é adicionada.|RoutingServices|  
|[605 - IncrementBusyCount](../../../../../docs/framework/wcf/diagnostics/etw/605-incrementbusycount.md)|Detalhado|IncrementBusyCount chamado. Fonte: %1|WebHost|  
|[606 - DecrementBusyCount](../../../../../docs/framework/wcf/diagnostics/etw/606-decrementbusycount.md)|Detalhado|DecrementBusyCount chamado. Fonte: %1|WebHost|  
|[701 - ServiceChannelOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/701-servicechannelopenstart.md)|Detalhado|ServiceChannelOpen iniciado.|WebHost|  
|[702 - ServiceChannelOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/702-servicechannelopenstop.md)|Informações|ServiceChannelOpen concluída.|ServiceModel|  
|[703 - ServiceChannelCallStart](../../../../../docs/framework/wcf/diagnostics/etw/703-servicechannelcallstart.md)|Informações|ServiceChannelCall iniciado.|ServiceModel|  
|[704 - ServiceChannelBeginCallStart](../../../../../docs/framework/wcf/diagnostics/etw/704-servicechannelbegincallstart.md)|Informações|Chamadas assíncronas de ServiceChannel iniciadas.|ServiceModel|  
|[706 - HttpSendMessageStart](../../../../../docs/framework/wcf/diagnostics/etw/706-httpsendmessagestart.md)|Detalhado|Início de solicitação de envio HTTP.|HTTP|  
|[707 - HttpSendStop](../../../../../docs/framework/wcf/diagnostics/etw/707-httpsendstop.md)|Detalhado|Parada de solicitação de envio HTTP.|HTTP|  
|[708 - HttpMessageReceiveStart](../../../../../docs/framework/wcf/diagnostics/etw/708-httpmessagereceivestart.md)|Detalhado|Mensagem recebida de transporte http.|HTTP|  
|[709 - DispatchMessageStart](../../../../../docs/framework/wcf/diagnostics/etw/709-dispatchmessagestart.md)|Informações|Distribuição de mensagem iniciado.|ServiceModel|  
|[710 - HttpContextBeforeProcessAuthentication](../../../../../docs/framework/wcf/diagnostics/etw/710-httpcontextbeforeprocessauthentication.md)|Detalhado|Inicie a autenticação para distribuição de mensagem.|ServiceModel|  
|[711 - DispatchMessageBeforeAuthorization](../../../../../docs/framework/wcf/diagnostics/etw/711-dispatchmessagebeforeauthorization.md)|Detalhado|Inicie a autorização para distribuição de mensagem.|ServiceModel|  
|[712 - DispatchMessageStop](../../../../../docs/framework/wcf/diagnostics/etw/712-dispatchmessagestop.md)|Informações|Distribuição de mensagem concluída.|ServiceModel|  
|[715 - ClientChannelOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/715-clientchannelopenstart.md)|Informações|ServiceChannel abra Iniciar.|ServiceModel|  
|[716 - ClientChannelOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/716-clientchannelopenstop.md)|Informações|Parar de abrir ServiceChannel.|ServiceModel|  
|[717 - HttpSendStreamedMessageStart](../../../../../docs/framework/wcf/diagnostics/etw/717-httpsendstreamedmessagestart.md)|Informações|Mensagem transmitida de envio HTTP iniciada.|HTTP|  
|[1400 - ChannelInitializationTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1400-channelinitializationtimeout.md)|Erro|1%|ServiceModel|  
|[1401 - CloseTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1401-closetimeout.md)|Erro|1%|ServiceModel|  
|[1402 - IdleTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1402-idletimeout.md)|Erro|Chave de pool de Conexão %1: %2|ServiceModel|  
|[1403 - LeaseTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1403-leasetimeout.md)|Informações|Chave de pool de Conexão %1: %2|ServiceModel|  
|[1405 - OpenTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1405-opentimeout.md)|Erro|%1|ServiceModel|  
|[1406 - ReceiveTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1406-receivetimeout.md)|Erro|%1|ServiceModel|  
|[1407 - SendTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1407-sendtimeout.md)|Erro|%1|ServiceModel|  
|[1409 - InactivityTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1409-inactivitytimeout.md)|Informações|%1|ServiceModel|  
|[1416 - MaxReceivedMessageSizeExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1416-maxreceivedmessagesizeexceeded.md)|Erro|%1|Cota|  
|[1417 - MaxSentMessageSizeExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1417-maxsentmessagesizeexceeded.md)|Erro|%1|Cota|  
|[1418 - MaxOutboundConnectionsPerEndpointExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1418-maxoutboundconnectionsperendpointexceeded.md)|Informações|%1|Cota|  
|[1419 - MaxPendingConnectionsExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1419-maxpendingconnectionsexceeded.md)|Informações|%1|Cota|  
|[1420 - ReaderQuotaExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1420-readerquotaexceeded.md)|Erro|%1|Cota|  
|[1422 - NegotiateTokenAuthenticatorStateCacheExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1422-negotiatetokenauthenticatorstatecacheexceeded.md)|Erro|%1|Cota|  
|[1423 - NegotiateTokenAuthenticatorStateCacheRatio](../../../../../docs/framework/wcf/diagnostics/etw/1423-negotiatetokenauthenticatorstatecacheratio.md)|Detalhado|Negociar taxa de cache de estado do autenticador de token: %1 / %2|Cota|  
|[1424 - SecuritySessionRatio](../../../../../docs/framework/wcf/diagnostics/etw/1424-securitysessionratio.md)|Detalhado|Taxa de sessão de segurança: %1 / %2|Cota|  
|[1430 - PendingConnectionsRatio](../../../../../docs/framework/wcf/diagnostics/etw/1430-pendingconnectionsratio.md)|Detalhado|Taxa de conexões pendentes: %1 / %2|Cota|  
|[1431 - ConcurrentCallsRatio](../../../../../docs/framework/wcf/diagnostics/etw/1431-concurrentcallsratio.md)|Detalhado|Taxa de sessões simultâneas: %1 / %2|Cota|  
|[1432 - ConcurrentSessionsRatio](../../../../../docs/framework/wcf/diagnostics/etw/1432-concurrentsessionsratio.md)|Detalhado|Taxa de sessões simultâneas: %1 / %2|Cota|  
|[1433 - OutboundConnectionsPerEndpointRatio](../../../../../docs/framework/wcf/diagnostics/etw/1433-outboundconnectionsperendpointratio.md)|Detalhado|Conexões de saída por taxa de ponto de extremidade: %1 / %2|Cota|  
|[1433 - OutboundConnectionsPerEndpointRatio](../../../../../docs/framework/wcf/diagnostics/etw/1433-outboundconnectionsperendpointratio.md)|Detalhado|Conexões de saída por taxa de ponto de extremidade: %1 / %2|Cota|  
|[1436 - PendingMessagesPerChannelRatio](../../../../../docs/framework/wcf/diagnostics/etw/1436-pendingmessagesperchannelratio.md)|Detalhado|Mensagens pendentes por taxa de canal: %1 / %2|Cota|  
|[1438 - ConcurrentInstancesRatio](../../../../../docs/framework/wcf/diagnostics/etw/1438-concurrentinstancesratio.md)|Detalhado|Taxa de instâncias simultâneas: %1 / %2|Cota|  
|[1439 - PendingAcceptsAtZero](../../../../../docs/framework/wcf/diagnostics/etw/1439-pendingacceptsatzero.md)|Informações|Zero aceitações pendentes restantes|Cota|  
|[1441 - MaxSessionSizeReached](../../../../../docs/framework/wcf/diagnostics/etw/1441-maxsessionsizereached.md)|Aviso|1%|Cota|  
|[1442 - ReceiveRetryCountReached](../../../../../docs/framework/wcf/diagnostics/etw/1442-receiveretrycountreached.md)|Aviso|Contagem de repetição atingida na mensagem MSMQ com a id '%1' de recebimento|Cota|  
|[1443 - MaxRetryCyclesExceededMsmq](../../../../../docs/framework/wcf/diagnostics/etw/1443-maxretrycyclesexceededmsmq.md)|Erro|Ciclos máximos de repetições excedidos na mensagem MSMQ com a id '%1'|Cota|  
|[1445 - ReadPoolMiss](../../../../../docs/framework/wcf/diagnostics/etw/1445-readpoolmiss.md)|Detalhado|Novo criado '%1'|Cota|  
|[1446 - WritePoolMiss](../../../../../docs/framework/wcf/diagnostics/etw/1446-writepoolmiss.md)|Detalhado|Novo criado '%1'|Cota|  
|[1451 - MaxRetryCyclesExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1451-maxretrycyclesexceeded.md)|Erro|1%|Cota|  
|[3300 - ReceiveContextCompleteFailed](../../../../../docs/framework/wcf/diagnostics/etw/3300-receivecontextcompletefailed.md)|Aviso|Falha ao concluir a %1.|Canal|  
|[3301 - ReceiveContextAbandonFailed](../../../../../docs/framework/wcf/diagnostics/etw/3301-receivecontextabandonfailed.md)|Aviso|Falha ao abandono %1.|Canal|  
|[3303 - ReceiveContextAbandonWithException](../../../../../docs/framework/wcf/diagnostics/etw/3303-receivecontextabandonwithexception.md)|Aviso|Contexto de recebimento com defeito.|ServiceModel|  
|[3303 - ReceiveContextAbandonWithException](../../../../../docs/framework/wcf/diagnostics/etw/3303-receivecontextabandonwithexception.md)|Informações|%1 foi abandonado com a exceção: %2.|Canal|  
|[3305 - ClientBaseCachedChannelFactoryCount](../../../../../docs/framework/wcf/diagnostics/etw/3305-clientbasecachedchannelfactorycount.md)|Informações|Número de fábricas de canais armazenadas em cache é: '%1'.  No máximo '%2' fábricas de canais podem ser armazenados em cache.|ServiceModel|  
|[3306 - ClientBaseChannelFactoryAgedOutofCache](../../../../../docs/framework/wcf/diagnostics/etw/3306-clientbasechannelfactoryagedoutofcache.md)|Informações|Uma fábrica de canais ficou antiga no cache porque o cache atingiu seu limite de '%1'.|ServiceModel|  
|[3307 - ClientBaseChannelFactoryCacheHit](../../../../../docs/framework/wcf/diagnostics/etw/3307-clientbasechannelfactorycachehit.md)|Informações|Usado a fábrica de canais correspondente encontrada no cache.|ServiceModel|  
|[3308 - ClientBaseUsingLocalChannelFactory](../../../../../docs/framework/wcf/diagnostics/etw/3308-clientbaseusinglocalchannelfactory.md)|Informações|Não utilizando a fábrica de canais do cache, ou seja, o cache desabilitado para a instância.|ServiceModel|  
|[3309 - QueryCompositionExecuted](../../../../../docs/framework/wcf/diagnostics/etw/3309-querycompositionexecuted.md)|Informações|Composição de consulta usando '%1' foi executada no Uri da solicitação: '%2'.|ServiceModel|  
|[3310 - DispatchFailed](../../../../../docs/framework/wcf/diagnostics/etw/3310-dispatchfailed.md)|Erro|A operação '%1' foi distribuída com erros.|ServiceModel|  
|[3311 - DispatchSuccessful](../../../../../docs/framework/wcf/diagnostics/etw/3311-dispatchsuccessful.md)|Informações|A operação '%1' foi distribuída com êxito.|ServiceModel|  
|[3312 - MessageReadByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3312-messagereadbyencoder.md)|Informações|Uma mensagem com o tamanho '%1' bytes foi lida pelo codificador.|Canal|  
|[3312 - MessageReadByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3312-messagereadbyencoder.md)|Informações|Uma mensagem com o tamanho '%1' bytes foi gravada pelo codificador.|Canal|  
|[3314 - SessionIdleTimeout](../../../../../docs/framework/wcf/diagnostics/etw/3314-sessionidletimeout.md)|Erro|Anulando a sessão do canal ocioso para uri: '%1'.|ServiceModel|  
|[3319 - SocketAcceptEnqueued](../../../../../docs/framework/wcf/diagnostics/etw/3319-socketacceptenqueued.md)|Detalhado|Conexão aceitar iniciada.|TCP|  
|[3320 - SocketAccepted](../../../../../docs/framework/wcf/diagnostics/etw/3320-socketaccepted.md)|Detalhado|Socketid: % ListenerId:% 1 aceitada 2.|TCP|  
|[3321 - ConnectionPoolMiss](../../../../../docs/framework/wcf/diagnostics/etw/3321-connectionpoolmiss.md)|Detalhado|Pool para %1 não tem nenhuma conexão disponível e conexões de %2 ocupado.|Canal|  
|[3322 - DispatchFormatterDeserializeRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3322-dispatchformatterdeserializerequeststart.md)|Detalhado|Dispatcher iniciou a desserialização da mensagem de solicitação.|ServiceModel|  
|[3323 - DispatchFormatterDeserializeRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/3323-dispatchformatterdeserializerequeststop.md)|Detalhado|Dispatcher concluiu a desserialização da mensagem de solicitação.|ServiceModel|  
|[3324 - DispatchFormatterSerializeReplyStart](../../../../../docs/framework/wcf/diagnostics/etw/3324-dispatchformatterserializereplystart.md)|Detalhado|O Dispatcher iniciou a serialização da mensagem de resposta.|ServiceModel|  
|[3325 - DispatchFormatterSerializeReplyStop](../../../../../docs/framework/wcf/diagnostics/etw/3325-dispatchformatterserializereplystop.md)|Detalhado|O Dispatcher concluiu a serialização da mensagem de resposta.|ServiceModel|  
|[3326 - ClientFormatterSerializeRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3326-clientformatterserializerequeststart.md)|Detalhado|Serialização de solicitação do cliente é iniciado.|ServiceModel|  
|[3327 - ClientFormatterSerializeRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/3327-clientformatterserializerequeststop.md)|Detalhado|O cliente concluiu a serialização da mensagem de solicitação.|ServiceModel|  
|[3328 - ClientFormatterDeserializeReplyStart](../../../../../docs/framework/wcf/diagnostics/etw/3328-clientformatterdeserializereplystart.md)|Detalhado|Cliente iniciou a desserialização da mensagem de resposta.|ServiceModel|  
|[3329 - ClientFormatterDeserializeReplyStop](../../../../../docs/framework/wcf/diagnostics/etw/3329-clientformatterdeserializereplystop.md)|Detalhado|O cliente concluiu a desserialização da mensagem de resposta.|ServiceModel|  
|[3330 - SecurityNegotiationStart](../../../../../docs/framework/wcf/diagnostics/etw/3330-securitynegotiationstart.md)|Detalhado|Iniciar a negociação de segurança.|Segurança|  
|[3331 - SecurityNegotiationStop](../../../../../docs/framework/wcf/diagnostics/etw/3331-securitynegotiationstop.md)|Detalhado|Negociação de segurança concluída.|Segurança|  
|[3332 - SecurityTokenProviderOpened](../../../../../docs/framework/wcf/diagnostics/etw/3332-securitytokenprovideropened.md)|Detalhado|Abertura de SecurityTokenProvider concluída.|Segurança|  
|[3333 - OutgoingMessageSecured](../../../../../docs/framework/wcf/diagnostics/etw/3333-outgoingmessagesecured.md)|Detalhado|Mensagem de saída foi protegida.|Segurança|  
|[3334 - IncomingMessageVerified](../../../../../docs/framework/wcf/diagnostics/etw/3334-incomingmessageverified.md)|Detalhado|Mensagem de entrada foi verificada.|Segurança ServiceModel|  
|[3335 - GetServiceInstanceStart](../../../../../docs/framework/wcf/diagnostics/etw/3335-getserviceinstancestart.md)|Detalhado|Recuperação de instância de serviço é iniciado.|ServiceModel|  
|[3336 - GetServiceInstanceStop](../../../../../docs/framework/wcf/diagnostics/etw/3336-getserviceinstancestop.md)|Detalhado|Recuperar a instância de serviço.|ServiceModel|  
|[3337 - ChannelReceiveStart](../../../../../docs/framework/wcf/diagnostics/etw/3337-channelreceivestart.md)|Detalhado|Channelhandlerid: % 1 - mensagem de loop de recebimento iniciado.|Canal|  
|[3338 - ChannelReceiveStop](../../../../../docs/framework/wcf/diagnostics/etw/3338-channelreceivestop.md)|Detalhado|Channelhandlerid: % 1 - mensagem de loop de recebimento interrompido.|Canal|  
|[3339 - ChannelFactoryCreated](../../../../../docs/framework/wcf/diagnostics/etw/3339-channelfactorycreated.md)|Detalhado|ChannelFactory criado.|ServiceModel|  
|[3340 - PipeConnectionAcceptStart](../../../../../docs/framework/wcf/diagnostics/etw/3340-pipeconnectionacceptstart.md)|Detalhado|Conexão de pipe aceitar iniciada em %1.|Canal|  
|[3341 - PipeConnectionAcceptStop](../../../../../docs/framework/wcf/diagnostics/etw/3341-pipeconnectionacceptstop.md)|Detalhado|Aceita a conexão do pipe.|Canal|  
|[3342 - EstablishConnectionStart](../../../../../docs/framework/wcf/diagnostics/etw/3342-establishconnectionstart.md)|Detalhado|Estabelecimento de Conexão iniciado para %1.|Canal|  
|[3343 - EstablishConnectionStop](../../../../../docs/framework/wcf/diagnostics/etw/3343-establishconnectionstop.md)|Detalhado|Conexão estabelecida.|Canal|  
|[3345 - SessionPreambleUnderstood](../../../../../docs/framework/wcf/diagnostics/etw/3345-sessionpreambleunderstood.md)|Detalhado|Entendido Preâmbulo de sessão para '%1'.|Canal|  
|[3346 - ConnectionReaderSendFault](../../../../../docs/framework/wcf/diagnostics/etw/3346-connectionreadersendfault.md)|Erro|Leitor de Conexão enviar falha de '%1'.|Canal|  
|[3347 - SocketAcceptClosed](../../../../../docs/framework/wcf/diagnostics/etw/3347-socketacceptclosed.md)|Detalhado|Soquete aceitar fechado.|TCP|  
|[3348 - ServiceHostFaulted](../../../../../docs/framework/wcf/diagnostics/etw/3348-servicehostfaulted.md)|Crítico|Falha de host de serviço.|TCP|  
|[3349 - ListenerOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/3349-listeneropenstart.md)|Detalhado|Ouvinte de abertura para '%1'.|Canal|  
|[3350 - ListenerOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/3350-listeneropenstop.md)|Detalhado|Abrir do ouvinte concluído.|Canal|  
|[3351 - ServerMaxPooledConnectionsQuotaReached](../../../../../docs/framework/wcf/diagnostics/etw/3351-servermaxpooledconnectionsquotareached.md)|Detalhado|Cota máxima de conexões em pool do servidor atingido.|Cota|  
|[3352 - TcpConnectionTimedOut](../../../../../docs/framework/wcf/diagnostics/etw/3352-tcpconnectiontimedout.md)|Erro|Socketid: % 1 para endereço remoto %2 atingiu o tempo limite.|TCP|  
|[3353 - TcpConnectionResetError](../../../../../docs/framework/wcf/diagnostics/etw/3353-tcpconnectionreseterror.md)|Aviso|Socketid: % 1 para endereço remoto %2 tinha uma conexão redefinir o erro.|TCP|  
|[3354 - ServiceSecurityNegotiationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/3354-servicesecuritynegotiationcompleted.md)|Detalhado|Negociação de segurança do serviço concluída.|Segurança|  
|[3355 - SecurityNegotiationProcessingFailure](../../../../../docs/framework/wcf/diagnostics/etw/3355-securitynegotiationprocessingfailure.md)|Erro|Falha no processamento da negociação de segurança.|Segurança|  
|[3356 - SecurityIdentityVerificationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3356-securityidentityverificationsuccess.md)|Detalhado|Êxito na verificação de segurança.|Segurança|  
|[3357 - SecurityIdentityVerificationFailure](../../../../../docs/framework/wcf/diagnostics/etw/3357-securityidentityverificationfailure.md)|Erro|Falha na verificação de segurança.|Segurança|  
|[3358 - PortSharingDuplicatedSocket](../../../../../docs/framework/wcf/diagnostics/etw/3358-portsharingduplicatedsocket.md)|Detalhado|Soquete duplicado para %1.|ActivationServices|  
|[3359 - SecurityImpersonationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3359-securityimpersonationsuccess.md)|Detalhado|Êxito de representação de segurança.|Segurança|  
|[3360 - SecurityImpersonationFailure](../../../../../docs/framework/wcf/diagnostics/etw/3360-securityimpersonationfailure.md)|Aviso|Falha na representação de segurança.|Segurança|  
|[3361 - HttpChannelRequestAborted](../../../../../docs/framework/wcf/diagnostics/etw/3361-httpchannelrequestaborted.md)|Aviso|Solicitação de canal HTTP anulada.|HTTP|  
|[3362 - HttpChannelResponseAborted](../../../../../docs/framework/wcf/diagnostics/etw/3362-httpchannelresponseaborted.md)|Aviso|Resposta de canal HTTP anulada.|HTTP|  
|[3363 - HttpAuthFailed](../../../../../docs/framework/wcf/diagnostics/etw/3363-httpauthfailed.md)|Aviso|Falha de autenticação HTTP.|HTTP|  
|[3364 - SharedListenerProxyRegisterStart](../../../../../docs/framework/wcf/diagnostics/etw/3364-sharedlistenerproxyregisterstart.md)|Detalhado|Registro de SharedListenerProxy iniciado para o uri '%1'.|ActivationServices|  
|[3365 - SharedListenerProxyRegisterStop](../../../../../docs/framework/wcf/diagnostics/etw/3365-sharedlistenerproxyregisterstop.md)|Detalhado|Parada de registro de SharedListenerProxy.|ActivationServices|  
|[3366 - SharedListenerProxyRegisterFailed](../../../../../docs/framework/wcf/diagnostics/etw/3366-sharedlistenerproxyregisterfailed.md)|Erro|Registro de SharedListenerProxy falhou com status '%1'.|ActivationServices|  
|[3367 - ConnectionPoolPreambleFailed](../../../../../docs/framework/wcf/diagnostics/etw/3367-connectionpoolpreamblefailed.md)|Erro|ConnectionPoolPreambleFailed.|Canal|  
|[3368 - SslOnInitiateUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3368-ssloninitiateupgrade.md)|Detalhado|SslOnAcceptUpgradeStart|Segurança|  
|[3369 - SslOnAcceptUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3369-sslonacceptupgrade.md)|Detalhado|SslOnAcceptUpgradeStop|Segurança|  
|[3370 - BinaryMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3370-binarymessageencodingstart.md)|Detalhado|BinaryMessageEncoder iniciou a codificação da mensagem.|Canal|  
|[3371 - MtomMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3371-mtommessageencodingstart.md)|Detalhado|MtomMessageEncoder iniciou a codificação da mensagem.|Canal|  
|[3372 - TextMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3372-textmessageencodingstart.md)|Detalhado|TextMessageEncoder iniciou a codificação da mensagem.|Canal|  
|[3373 - BinaryMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3373-binarymessagedecodingstart.md)|Detalhado|BinaryMessageEncoder iniciou a decodificação da mensagem.|Canal|  
|[3374 - MtomMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3374-mtommessagedecodingstart.md)|Detalhado|MtomMessageEncoder iniciou a decodificação da mensagem.|Canal|  
|[3375 - TextMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3375-textmessagedecodingstart.md)|Detalhado|TextMessageEncoder iniciou a decodificação da mensagem.|Canal|  
|[3376 - HttpResponseReceiveStart](../../../../../docs/framework/wcf/diagnostics/etw/3376-httpresponsereceivestart.md)|Informações|Transporte HTTP iniciou o recebimento de uma mensagem.|HTTP|  
|[3377 - SocketReadStop](../../../../../docs/framework/wcf/diagnostics/etw/3377-socketreadstop.md)|Detalhado|Socketid: % 1 bytes de leitura '%2' ler '%3'.|TCP|  
|[3378 - SocketAsyncReadStop](../../../../../docs/framework/wcf/diagnostics/etw/3378-socketasyncreadstop.md)|Detalhado|Socketid: % 1 bytes de leitura '%2' ler '%3'.|TCP|  
|[3379 - SocketWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3379-socketwritestart.md)|Detalhado|Socketid: % 1 bytes de gravação '%2' para '%3'.|TCP|  
|[3380 - SocketAsyncWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3380-socketasyncwritestart.md)|Detalhado|Socketid: % 1 bytes de gravação '%2' para '%3'.|TCP|  
|[3381 - SequenceAcknowledgementSent](../../../../../docs/framework/wcf/diagnostics/etw/3381-sequenceacknowledgementsent.md)|Detalhado|Confirmação de SessionId:% 1 enviada.|Canal|  
|[3382 - ClientReliableSessionReconnect](../../../../../docs/framework/wcf/diagnostics/etw/3382-clientreliablesessionreconnect.md)|Informações|A reconexão SessionId:% 1.|Canal|  
|[3383 - ReliableSessionChannelFaulted](../../../../../docs/framework/wcf/diagnostics/etw/3383-reliablesessionchannelfaulted.md)|Informações|SessionId:% 1 com defeito.|Canal|  
|[3384 - WindowsStreamSecurityOnInitiateUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3384-windowsstreamsecurityoninitiateupgrade.md)|Detalhado|Windowsstreamsecurity está iniciando a atualização de segurança.|Segurança|  
|[3385 - WindowsStreamSecurityOnAcceptUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3385-windowsstreamsecurityonacceptupgrade.md)|Detalhado|Streaming segurança aceitar a atualização do Windows.|Segurança|  
|[3386 - SocketConnectionAbort](../../../../../docs/framework/wcf/diagnostics/etw/3386-socketconnectionabort.md)|Aviso|Socketid: % 1 está sendo anulado.|TCP|  
|[3388 - HttpGetContextStart](../../../../../docs/framework/wcf/diagnostics/etw/3388-httpgetcontextstart.md)|Detalhado|HttpGetContext iniciar.|HTTP|  
|[3389 - ClientSendPreambleStart](../../../../../docs/framework/wcf/diagnostics/etw/3389-clientsendpreamblestart.md)|Detalhado|Início de Preâmbulo de envio de cliente.|Canal|  
|[3390 - ClientSendPreambleStop](../../../../../docs/framework/wcf/diagnostics/etw/3390-clientsendpreamblestop.md)|Detalhado|Parada de preâmbulo envia do cliente.|Canal|  
|[3391 - HttpMessageReceiveFailed](../../../../../docs/framework/wcf/diagnostics/etw/3391-httpmessagereceivefailed.md)|Aviso|Falha no recebimento da mensagem HTTP.|HTTP|  
|[3392 - TransactionScopeCreate](../../../../../docs/framework/wcf/diagnostics/etw/3392-transactionscopecreate.md)|Informações|TransactionScope está sendo criado com LocalIdentifier: '%1' e DistributedIdentifier: '%2'.|ServiceModel|  
|[3393 - StreamedMessageReadByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3393-streamedmessagereadbyencoder.md)|Informações|Uma mensagem transmitida foi lida pelo codificador.|Canal|  
|[3394 - StreamedMessageWrittenByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3394-streamedmessagewrittenbyencoder.md)|Informações|Uma mensagem transmitida foi gravada pelo codificador.|Canal|  
|[3395 - MessageWrittenAsynchronouslyByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3395-messagewrittenasynchronouslybyencoder.md)|Informações|Uma mensagem foi gravada de forma assíncrona pelo codificador.|Canal|  
|[3396 - BufferedAsyncWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3396-bufferedasyncwritestart.md)|Informações|Bytes de gravação de bufferid: % 1 concluída '%2' no fluxo subjacente.|Canal|  
|[3397 - BufferedAsyncWriteStop](../../../../../docs/framework/wcf/diagnostics/etw/3397-bufferedasyncwritestop.md)|Informações|Uma mensagem foi gravada de forma assíncrona pelo codificador.|Canal|  
|[3398 - PipeSharedMemoryCreated](../../../../../docs/framework/wcf/diagnostics/etw/3398-pipesharedmemorycreated.md)|Detalhado|Redirecione a memória compartilhada criada em '%1'.|Canal|  
|[3399 - NamedPipeCreated](../../../../../docs/framework/wcf/diagnostics/etw/3399-namedpipecreated.md)|Detalhado|Pipe nomeado '%1' foi criado.|Canal|  
|[3401 - SignatureVerificationStart](../../../../../docs/framework/wcf/diagnostics/etw/3401-signatureverificationstart.md)|Detalhado|Verificação de assinatura é iniciado.|Segurança|  
|[3402 - SignatureVerificationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3402-signatureverificationsuccess.md)|Detalhado|Êxito na verificação de assinatura.|Segurança|  
|[3403 - WrappedKeyDecryptionStart](../../../../../docs/framework/wcf/diagnostics/etw/3403-wrappedkeydecryptionstart.md)|Detalhado|Encapsulada iniciada de descriptografia de chave.|Segurança|  
|[3404 - WrappedKeyDecryptionSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3404-wrappedkeydecryptionsuccess.md)|Detalhado|Descriptografia de chave encapsulada bem-sucedida.|Segurança|  
|[3405 - EncryptedDataProcessingStart](../../../../../docs/framework/wcf/diagnostics/etw/3405-encrypteddataprocessingstart.md)|Detalhado|Introdução de processamento de dados criptografados.|Segurança|  
|[3406 - EncryptedDataProcessingSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3406-encrypteddataprocessingsuccess.md)|Detalhado|Processamento de dados criptografados bem-sucedido.|Segurança|  
|[3407 - HttpPipelineProcessInboundRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3407-httppipelineprocessinboundrequeststart.md)|Detalhado|Manipulador de mensagens HTTP iniciou o processamento da solicitação de entrada.|HTTP|  
|[3408 - HttpPipelineBeginProcessInboundRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3408-httppipelinebeginprocessinboundrequeststart.md)|Detalhado|Manipulador de mensagens HTTP iniciou o processamento da solicitação de entrada de forma assíncrona.|HTTP|  
|[3409 - HttpPipelineProcessInboundRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/3409-httppipelineprocessinboundrequeststop.md)|Detalhado|Manipulador de mensagens HTTP concluiu o processamento de uma solicitação de entrada.|HTTP|  
|[3410 - HttpPipelineFaulted](../../../../../docs/framework/wcf/diagnostics/etw/3410-httppipelinefaulted.md)|Aviso|Manipulador de mensagens HTTP apresentou falha.|HTTP|  
|[3411 - HttpPipelineTimeoutException](../../../../../docs/framework/wcf/diagnostics/etw/3411-httppipelinetimeoutexception.md)|Erro|Conexão WebSocket atingiu o tempo limite.|HTTP|  
|[3412 - HttpPipelineProcessResponseStart](../../../../../docs/framework/wcf/diagnostics/etw/3412-httppipelineprocessresponsestart.md)|Detalhado|Manipulador de mensagens HTTP iniciou o processamento da resposta.|HTTP|  
|[3413 - HttpPipelineBeginProcessResponseStart](../../../../../docs/framework/wcf/diagnostics/etw/3413-httppipelinebeginprocessresponsestart.md)|Detalhado|Manipulador de mensagens HTTP iniciou o processamento da resposta de forma assíncrona.|HTTP|  
|[3414 - HttpPipelineProcessResponseStop](../../../../../docs/framework/wcf/diagnostics/etw/3414-httppipelineprocessresponsestop.md)|Detalhado|Manipulador de mensagens HTTP concluiu o processamento da resposta.|HTTP|  
|[3415 - WebSocketConnectionRequestSendStart](../../../../../docs/framework/wcf/diagnostics/etw/3415-websocketconnectionrequestsendstart.md)|Detalhado|Início do envio de solicitação de conexão WebSocket a '%1'.|HTTP|  
|[3416 - WebSocketConnectionRequestSendStop](../../../../../docs/framework/wcf/diagnostics/etw/3416-websocketconnectionrequestsendstop.md)|Detalhado|Websocketid: % 1 solicitação de conexão enviada.|HTTP|  
|[3417 - WebSocketConnectionAcceptStart](../../../../../docs/framework/wcf/diagnostics/etw/3417-websocketconnectionacceptstart.md)|Detalhado|Início da aceitação da conexão WebSocket.|HTTP|  
|[3418 - WebSocketConnectionAccepted](../../../../../docs/framework/wcf/diagnostics/etw/3418-websocketconnectionaccepted.md)|Detalhado|Websocketid: % 1 conexão aceito.|HTTP|  
|[3419 - WebSocketConnectionDeclined](../../../../../docs/framework/wcf/diagnostics/etw/3419-websocketconnectiondeclined.md)|Erro|Conexão WebSocket recusada com o código de status '%1'|HTTP|  
|[3420 - WebSocketConnectionFailed](../../../../../docs/framework/wcf/diagnostics/etw/3420-websocketconnectionfailed.md)|Erro|Falha na solicitação de conexão WebSocket: '%1'|HTTP|  
|[3421 - WebSocketConnectionAborted](../../../../../docs/framework/wcf/diagnostics/etw/3421-websocketconnectionaborted.md)|Erro|Websocketid: % 1 conexão anulada.|HTTP|  
|[3422 - WebSocketAsyncWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3422-websocketasyncwritestart.md)|Detalhado|Websocketid: % 1 bytes de gravação '%2' para '%3'.|HTTP|  
|[3423 - WebSocketAsyncWriteStop](../../../../../docs/framework/wcf/diagnostics/etw/3423-websocketasyncwritestop.md)|Detalhado|Websocketid: % 1 parada de gravação assíncrona.|HTTP|  
|[3424 - WebSocketAsyncReadStart](../../../../../docs/framework/wcf/diagnostics/etw/3424-websocketasyncreadstart.md)|Detalhado|Início de websocketid: % 1 de leitura.|HTTP|  
|[3425 - WebSocketAsyncReadStop](../../../../../docs/framework/wcf/diagnostics/etw/3425-websocketasyncreadstop.md)|Detalhado|Websocketid: % 1 ler bytes de '%2' de '%3'.|HTTP|  
|[3426 - WebSocketCloseSent](../../../../../docs/framework/wcf/diagnostics/etw/3426-websocketclosesent.md)|Detalhado|Websocketid: % 1 Enviando mensagem de fechamento a '%2' com o status de fechamento '%3'.|HTTP|  
|[3427 - WebSocketCloseOutputSent](../../../../../docs/framework/wcf/diagnostics/etw/3427-websocketcloseoutputsent.md)|Detalhado|Websocketid: % 1 Enviando mensagem de fechamento saída para '%2' com o status de fechamento '%3'.|HTTP|  
|[3428 - WebSocketConnectionClosed](../../../../../docs/framework/wcf/diagnostics/etw/3428-websocketconnectionclosed.md)|Detalhado|Websocketid: % 1 conexão fechada.|HTTP|  
|[3429 - WebSocketCloseStatusReceived](../../../../../docs/framework/wcf/diagnostics/etw/3429-websocketclosestatusreceived.md)|Detalhado|Mensagem de fechamento de conexão websocketid: % 1 recebida com status '%2'.|HTTP|  
|[3430 - WebSocketUseVersionFromClientWebSocketFactory](../../../../../docs/framework/wcf/diagnostics/etw/3430-websocketuseversionfromclientwebsocketfactory.md)|Detalhado|Usando o WebSocketVersion de uma fábrica de WebSocket do cliente do tipo '%1'.|HTTP|  
|[3431 - WebSocketCreateClientWebSocketWithFactory](../../../../../docs/framework/wcf/diagnostics/etw/3431-websocketcreateclientwebsocketwithfactory.md)|Detalhado|Criando o WebSocket do cliente com uma fábrica do tipo '%1'.|HTTP|  
|[3553 - XamlServicesLoadStart](../../../../../docs/framework/wcf/diagnostics/etw/3553-xamlservicesloadstart.md)|Informações|Início xamlServicesLoad|WebHost|  
|[3554 - XamlServicesLoadStop](../../../../../docs/framework/wcf/diagnostics/etw/3554-xamlservicesloadstop.md)|Informações|Parar xamlServicesLoad|WebHost|  
|[3555 - CreateWorkflowServiceHostStart](../../../../../docs/framework/wcf/diagnostics/etw/3555-createworkflowservicehoststart.md)|Informações|Início CreateWorkflowServiceHost|WebHost|  
|[3556 - CreateWorkflowServiceHostStop](../../../../../docs/framework/wcf/diagnostics/etw/3556-createworkflowservicehoststop.md)|Informações|Parar CreateWorkflowServiceHost|WebHost|  
|[3558 - ServiceActivationStart](../../../../../docs/framework/wcf/diagnostics/etw/3558-serviceactivationstart.md)|Informações|Início de ativação de serviço|WebHost|  
|[3559 - ServiceActivationStop](../../../../../docs/framework/wcf/diagnostics/etw/3559-serviceactivationstop.md)|Informações|Ativação do serviço parar|WebHost|  
|[3560 - ServiceActivationAvailableMemory](../../../../../docs/framework/wcf/diagnostics/etw/3560-serviceactivationavailablememory.md)|Detalhado|Memória disponível (bytes): %1|Cota|  
|[3800 - RoutingServiceClosingClient](../../../../../docs/framework/wcf/diagnostics/etw/3800-routingserviceclosingclient.md)|Informações|O serviço de roteamento está fechando o cliente '%1'.|RoutingServices|  
|[3800 - RoutingServiceClosingClient](../../../../../docs/framework/wcf/diagnostics/etw/3800-routingserviceclosingclient.md)|Aviso|Cliente de serviço de roteamento '%1' apresentou falha.|RoutingServices|  
|[3802 - RoutingServiceCompletingOneWay](../../../../../docs/framework/wcf/diagnostics/etw/3802-routingservicecompletingoneway.md)|Informações|Uma mensagem unidirecional do serviço de roteamento está sendo concluída.|RoutingServices|  
|[3803 - RoutingServiceProcessingFailure](../../../../../docs/framework/wcf/diagnostics/etw/3803-routingserviceprocessingfailure.md)|Erro|O serviço de roteamento falhou ao processar uma mensagem no ponto de extremidade com endereço '%1'.|RoutingServices|  
|[3804 - RoutingServiceCreatingClientForEndpoint](../../../../../docs/framework/wcf/diagnostics/etw/3804-routingservicecreatingclientforendpoint.md)|Informações|O serviço de roteamento está criando um cliente para ponto de extremidade: '%1'.|RoutingServices|  
|[3805 - RoutingServiceDisplayConfig](../../../../../docs/framework/wcf/diagnostics/etw/3805-routingservicedisplayconfig.md)|Detalhado|O serviço de roteamento está configurado com RouteOnHeadersOnly: %1, SoapProcessingEnabled: %2, EnsureOrderedDispatch: %3.|RoutingServices|  
|[3807 - RoutingServiceCompletingTwoWay](../../../../../docs/framework/wcf/diagnostics/etw/3807-routingservicecompletingtwoway.md)|Informações|Uma mensagem de resposta de solicitação de serviço de roteamento está sendo concluída.|RoutingServices|  
|[3809 - RoutingServiceMessageRoutedToEndpoints](../../../../../docs/framework/wcf/diagnostics/etw/3809-routingservicemessageroutedtoendpoints.md)|Detalhado|O serviço de roteamento roteou uma mensagem com ID: '%1' para %2 listas de ponto de extremidade.|RoutingServices|  
|[3810 - RoutingServiceConfigurationApplied](../../../../../docs/framework/wcf/diagnostics/etw/3810-routingserviceconfigurationapplied.md)|Informações|Uma nova RoutingConfiguration foi aplicada ao serviço de roteamento.|RoutingServices|  
|[3815 - RoutingServiceProcessingMessage](../../../../../docs/framework/wcf/diagnostics/etw/3815-routingserviceprocessingmessage.md)|Informações|O serviço de roteamento está processando uma mensagem com ID: '%1', ação: '%2', URL de entrada: '%3' recebida na transação: %4.|RoutingServices|  
|[3816 - RoutingServiceTransmittingMessage](../../../../../docs/framework/wcf/diagnostics/etw/3816-routingservicetransmittingmessage.md)|Informações|O serviço de roteamento está transmitindo a mensagem com ID: '%1' [operação %2] para '%3'.|RoutingServices|  
|[3817 - RoutingServiceCommittingTransaction](../../../../../docs/framework/wcf/diagnostics/etw/3817-routingservicecommittingtransaction.md)|Informações|O serviço de roteamento está confirmando uma transação com id: '%1'.|RoutingServices|  
|[3818 - RoutingServiceDuplexCallbackException](../../../../../docs/framework/wcf/diagnostics/etw/3818-routingserviceduplexcallbackexception.md)|Erro|Componente de serviço de roteamento %1 encontrou uma exceção de retorno de chamada dúplex.|RoutingServices|  
|[3819 - RoutingServiceMovedToBackup](../../../../../docs/framework/wcf/diagnostics/etw/3819-routingservicemovedtobackup.md)|Informações|Mensagem de serviço de roteamento com ID: '%1' [operação %2] é movida para o ponto de extremidade de backup '%3'.|RoutingServices|  
|[3820 - RoutingServiceCreatingTransaction](../../../../../docs/framework/wcf/diagnostics/etw/3820-routingservicecreatingtransaction.md)|Informações|O serviço de roteamento criou uma nova Transaction com id '%1' para processar mensagens.|RoutingServices|  
|[3821 - RoutingServiceCloseFailed](../../../../../docs/framework/wcf/diagnostics/etw/3821-routingserviceclosefailed.md)|Aviso|O serviço de roteamento falhou ao fechar o cliente de saída '%1'.|RoutingServices|  
|[3822 - RoutingServiceSendingResponse](../../../../../docs/framework/wcf/diagnostics/etw/3822-routingservicesendingresponse.md)|Informações|O serviço de roteamento está retornando uma mensagem de resposta com Action '%1'.|RoutingServices|  
|[3823 - RoutingServiceSendingFaultResponse](../../../../../docs/framework/wcf/diagnostics/etw/3823-routingservicesendingfaultresponse.md)|Aviso|O serviço de roteamento está retornando uma mensagem de resposta Fault com Action '%1'.|RoutingServices|  
|[3824 - RoutingServiceCompletingReceiveContext](../../../../../docs/framework/wcf/diagnostics/etw/3824-routingservicecompletingreceivecontext.md)|Detalhado|O serviço de roteamento está chamando receivecontext. Complete para a mensagem com ID: '%1'.|RoutingServices|  
|[3825 - RoutingServiceAbandoningReceiveContext](../../../../../docs/framework/wcf/diagnostics/etw/3825-routingserviceabandoningreceivecontext.md)|Aviso|O serviço de roteamento está chamando Abandon para a mensagem com ID: '%1'.|RoutingServices|  
|[3826 - RoutingServiceUsingExistingTransaction](../../../../../docs/framework/wcf/diagnostics/etw/3826-routingserviceusingexistingtransaction.md)|Detalhado|O serviço de roteamento enviará mensagens usando a transação existente '%1'.|RoutingServices|  
|[3827 - RoutingServiceTransmitFailed](../../../../../docs/framework/wcf/diagnostics/etw/3827-routingservicetransmitfailed.md)|Aviso|O serviço de roteamento falhou ao enviar para '%1'.|RoutingServices|  
|[3828 - RoutingServiceFilterTableMatchStart](../../../../../docs/framework/wcf/diagnostics/etw/3828-routingservicefiltertablematchstart.md)|Informações|Início de correspondência de MessageFilterTable do serviço de roteamento.|RoutingServices|  
|[3829 - RoutingServiceFilterTableMatchStop](../../../../../docs/framework/wcf/diagnostics/etw/3829-routingservicefiltertablematchstop.md)|Informações|Parada de correspondência de MessageFilterTable do serviço de roteamento.|RoutingServices|  
|[3830 - RoutingServiceAbortingChannel](../../../../../docs/framework/wcf/diagnostics/etw/3830-routingserviceabortingchannel.md)|Detalhado|O serviço de roteamento está chamando abort no canal: '%1'.|RoutingServices|  
|[3831 - RoutingServiceHandledException](../../../../../docs/framework/wcf/diagnostics/etw/3831-routingservicehandledexception.md)|Detalhado|O serviço de roteamento tratou uma exceção.|RoutingServices|  
|[3832 - RoutingServiceTransmitSucceeded](../../../../../docs/framework/wcf/diagnostics/etw/3832-routingservicetransmitsucceeded.md)|Informações|O serviço de roteamento transmitiu com sucesso a mensagem com ID: ' %1 [operação %2] para '%3'.|RoutingServices|  
|[4001 - TransportListenerSessionsReceived](../../../../../docs/framework/wcf/diagnostics/etw/4001-transportlistenersessionsreceived.md)|Detalhado|Sessão de ouvinte de transporte recebida via '%1'|ActivationServices|  
|[4002 - FailFastException](../../../../../docs/framework/wcf/diagnostics/etw/4002-failfastexception.md)|Crítico|FailFastException.|ActivationServices|  
|[4003 - ServiceStartPipeError](../../../../../docs/framework/wcf/diagnostics/etw/4003-servicestartpipeerror.md)|Erro|Erro de pipe de início do serviço.|ActivationServices|  
|[4008 - DispatchSessionStart](../../../../../docs/framework/wcf/diagnostics/etw/4008-dispatchsessionstart.md)|Detalhado|Distribuição de sessão iniciada.|ActivationServices|  
|[4008 - DispatchSessionStart](../../../../../docs/framework/wcf/diagnostics/etw/4008-dispatchsessionstart.md)|Aviso|Distribuição de sessão para '%1' falhou, pois a fila pendentes sessão está cheia com '%2' itens pendentes.|ActivationServices|  
|[4011 - MessageQueueRegisterStart](../../../../../docs/framework/wcf/diagnostics/etw/4011-messagequeueregisterstart.md)|Detalhado|Iniciar o registro de fila de mensagem.|ActivationServices|  
|[4012 - MessageQueueRegisterAbort](../../../../../docs/framework/wcf/diagnostics/etw/4012-messagequeueregisterabort.md)|Erro|Registro de fila anulado com o status da mensagem: '%1' para o uri: '%2'.|ActivationServices|  
|[4013 - MessageQueueUnregisterSucceeded](../../../../../docs/framework/wcf/diagnostics/etw/4013-messagequeueunregistersucceeded.md)|Detalhado|Fila de mensagens cancelar o registro bem-sucedido para uri: '%1'.|ActivationServices|  
|[4014 - MessageQueueRegisterFailed](../../../../../docs/framework/wcf/diagnostics/etw/4014-messagequeueregisterfailed.md)|Erro|Registro de fila para o uri da mensagem: '%1' falhou com o status: '%2'.|ActivationServices|  
|[4015 - MessageQueueRegisterCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4015-messagequeueregistercompleted.md)|Informações|Registro de fila de mensagens concluído para o uri '%1'.|ActivationServices|  
|[4016 - MessageQueueDuplicatedSocketError](../../../../../docs/framework/wcf/diagnostics/etw/4016-messagequeueduplicatedsocketerror.md)|Erro|Fila de mensagens falhou ao duplicar o soquete.|ActivationServices|  
|[4019 - MessageQueueDuplicatedSocketComplete](../../../../../docs/framework/wcf/diagnostics/etw/4019-messagequeueduplicatedsocketcomplete.md)|Detalhado|MessageQueueDuplicatedSocketComplete|ActivationServices|  
|[4020 - TcpTransportListenerListeningStart](../../../../../docs/framework/wcf/diagnostics/etw/4020-tcptransportlistenerlisteningstart.md)|Detalhado|Ouvinte de transporte TCP iniciando a escuta no uri: '%1'.|ActivationServices|  
|[4021 - TcpTransportListenerListeningStop](../../../../../docs/framework/wcf/diagnostics/etw/4021-tcptransportlistenerlisteningstop.md)|Detalhado|Ouvinte de transporte TCP escutando.|ActivationServices|  
|[4022 - WebhostUnregisterProtocolFailed](../../../../../docs/framework/wcf/diagnostics/etw/4022-webhostunregisterprotocolfailed.md)|Erro|Código de erro: % 1|ActivationServices|  
|[4023 - WasCloseAllListenerChannelInstancesCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4023-wasclosealllistenerchannelinstancescompleted.md)|Informações|Fechamento WAS de todas as instâncias de canal do ouvinte concluído.|ActivationServices|  
|[4024 - WasCloseAllListenerChannelInstancesFailed](../../../../../docs/framework/wcf/diagnostics/etw/4024-wasclosealllistenerchannelinstancesfailed.md)|Erro|Código de erro: % 1|ActivationServices|  
|[4025 - OpenListenerChannelInstanceFailed](../../../../../docs/framework/wcf/diagnostics/etw/4025-openlistenerchannelinstancefailed.md)|Erro|Código de erro: % 1|ActivationServices|  
|[4026 - WasConnected](../../../../../docs/framework/wcf/diagnostics/etw/4026-wasconnected.md)|Detalhado|FOI conectado.|ActivationServices|  
|[4027 - WasDisconnected](../../../../../docs/framework/wcf/diagnostics/etw/4027-wasdisconnected.md)|Detalhado|FOI desconectado.|ActivationServices|  
|[4028 - PipeTransportListenerListeningStart](../../../../../docs/framework/wcf/diagnostics/etw/4028-pipetransportlistenerlisteningstart.md)|Detalhado|Ouvinte de transporte de pipe Iniciar em 1 de URI de escuta.|ActivationServices|  
|[4029 - PipeTransportListenerListeningStop](../../../../../docs/framework/wcf/diagnostics/etw/4029-pipetransportlistenerlisteningstop.md)|Detalhado|Parar escuta do ouvinte do transporte de pipe.|ActivationServices|  
|[4030 - DispatchSessionSuccess](../../../../../docs/framework/wcf/diagnostics/etw/4030-dispatchsessionsuccess.md)|Informações|Distribuição de sessão bem-sucedida.|ActivationServices|  
|[4031 - DispatchSessionFailed](../../../../../docs/framework/wcf/diagnostics/etw/4031-dispatchsessionfailed.md)|Erro|Falha na distribuição de sessão.|ActivationServices|  
|[4032 - WasConnectionTimedout](../../../../../docs/framework/wcf/diagnostics/etw/4032-wasconnectiontimedout.md)|Crítico|Conexão atingiu o tempo limite.|ActivationServices|  
|[4033 - RoutingTableLookupStart](../../../../../docs/framework/wcf/diagnostics/etw/4033-routingtablelookupstart.md)|Detalhado|Pesquisa de tabela de roteamento iniciada.|ActivationServices|  
|[4034 - RoutingTableLookupStop](../../../../../docs/framework/wcf/diagnostics/etw/4034-routingtablelookupstop.md)|Detalhado|Pesquisa de tabela de roteamento concluída.|ActivationServices|  
|[4035 - PendingSessionQueueRatio](../../../../../docs/framework/wcf/diagnostics/etw/4035-pendingsessionqueueratio.md)|Detalhado|Taxa de fila de sessões pendentes: %1 / %2|Cota|  
|[4600 - MessageLogEventSizeExceeded](../../../../../docs/framework/wcf/diagnostics/etw/4600-messagelogeventsizeexceeded.md)|Aviso|Mensagem não pôde ser registrada, pois ele excede o tamanho do evento ETW|WCFMessageLogging|  
|[4801 - DiscoveryClientInClientChannelFailedToClose](../../../../../docs/framework/wcf/diagnostics/etw/4801-discoveryclientinclientchannelfailedtoclose.md)|Aviso|O DiscoveryClient criado em DiscoveryClientChannel falhou ao fechar e portanto foi cancelado.|Descoberta|  
|[4802 - DiscoveryClientProtocolExceptionSuppressed](../../../../../docs/framework/wcf/diagnostics/etw/4802-discoveryclientprotocolexceptionsuppressed.md)|Informações|Uma ProtocolException foi suprimida ao fechar o DiscoveryClient. Isso pode ser porque um DiscoveryService ainda está tentando enviar respostas ao DiscoveryClient.|Descoberta|  
|[4803 - DiscoveryClientReceivedMulticastSuppression](../../../../../docs/framework/wcf/diagnostics/etw/4803-discoveryclientreceivedmulticastsuppression.md)|Informações|O DiscoveryClient recebeu uma mensagem de supressão multicast de um DiscoveryProxy.|Descoberta|  
|[4804 - DiscoveryMessageReceivedAfterOperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4804-discoverymessagereceivedafteroperationcompleted.md)|Informações|Uma mensagem %1 com messageId = '%2' foi descartada pelo DiscoveryClient porque a operação de %3 correspondente foi concluída.|Descoberta|  
|[4805 - DiscoveryMessageWithInvalidContent](../../../../../docs/framework/wcf/diagnostics/etw/4805-discoverymessagewithinvalidcontent.md)|Aviso|Uma mensagem %1 com messageId = '%2' foi descartada porque ela tinha conteúdo inválido.|Descoberta|  
|[4806 - DiscoveryMessageWithInvalidRelatesToOrOperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4806-discoverymessagewithinvalidrelatestooroperationcompleted.md)|Aviso|Uma mensagem %1 com messageId = '%2' e relatesTo = '%3' foi descartada pelo DiscoveryClient porque a operação de %4 correspondente foi concluída ou o valor relatesTo é inválido.|Descoberta|  
|[4807 - DiscoveryMessageWithInvalidReplyTo](../../../../../docs/framework/wcf/diagnostics/etw/4807-discoverymessagewithinvalidreplyto.md)|Aviso|Uma mensagem de solicitação de descoberta com messageId = '%1' foi descartada porque ela tinha um endereço ReplyTo inválido.|Descoberta|  
|[4808 - DiscoveryMessageWithNoContent](../../../../../docs/framework/wcf/diagnostics/etw/4808-discoverymessagewithnocontent.md)|Aviso|Uma mensagem %1 foi descartada porque ela não tinha nenhum conteúdo.|Descoberta|  
|[4809 - DiscoveryMessageWithNullMessageId](../../../../../docs/framework/wcf/diagnostics/etw/4809-discoverymessagewithnullmessageid.md)|Aviso|Uma mensagem %1 foi descartada porque o cabeçalho da mensagem não continha a propriedade MessageId necessária.|Descoberta|  
|[4810 - DiscoveryMessageWithNullMessageSequence](../../../../../docs/framework/wcf/diagnostics/etw/4810-discoverymessagewithnullmessagesequence.md)|Aviso|Uma mensagem %1 com messageId = '%2' foi descartada pelo DiscoveryClient porque ela não tinha a propriedade DiscoveryMessageSequence.|Descoberta|  
|[4811 - DiscoveryMessageWithNullRelatesTo](../../../../../docs/framework/wcf/diagnostics/etw/4811-discoverymessagewithnullrelatesto.md)|Aviso|Uma mensagem %1 com messageId = '%2' foi descartada pelo DiscoveryClient porque o cabeçalho da mensagem não continha a propriedade RelatesTo obrigatória.|Descoberta|  
|[4812 - DiscoveryMessageWithNullReplyTo](../../../../../docs/framework/wcf/diagnostics/etw/4812-discoverymessagewithnullreplyto.md)|Aviso|Uma mensagem de solicitação de descoberta com messageId = '%1' foi descartada porque ela não tinha um endereço ReplyTo.|Descoberta|  
|[4813 - DuplicateDiscoveryMessage](../../../../../docs/framework/wcf/diagnostics/etw/4813-duplicatediscoverymessage.md)|Aviso|Uma mensagem %1 com messageId = '%2' foi descartada porque ela era duplicada.|Descoberta|  
|[4814 - EndpointDiscoverabilityDisabled](../../../../../docs/framework/wcf/diagnostics/etw/4814-endpointdiscoverabilitydisabled.md)|Informações|A capacidade de descoberta do ponto de extremidade com EndpointAddress = '%1' e ListenUri = '%2' foi desabilitado.|Descoberta|  
|[4814 - EndpointDiscoverabilityDisabled](../../../../../docs/framework/wcf/diagnostics/etw/4814-endpointdiscoverabilitydisabled.md)|Informações|A capacidade de descoberta do ponto de extremidade com EndpointAddress = '%1' e ListenUri = '%2' foi ativado.|Descoberta|  
|[4816 - FindInitiatedInDiscoveryClientChannel](../../../../../docs/framework/wcf/diagnostics/etw/4816-findinitiatedindiscoveryclientchannel.md)|Detalhado|Uma operação Find foi iniciada no DiscoveryClientChannel para descobrir a extremidade.|Descoberta|  
|[4817 - InnerChannelCreationFailed](../../../../../docs/framework/wcf/diagnostics/etw/4817-innerchannelcreationfailed.md)|Aviso|Falha no DiscoveryClientChannel ao criar o canal com um ponto de extremidade descoberto com EndpointAddress = '%1' e Via = '%2'. O DiscoveryClientChannel agora tentará usar o ponto de extremidade descoberto disponível Avançar.|Descoberta|  
|[4818 - InnerChannelOpenFailed](../../../../../docs/framework/wcf/diagnostics/etw/4818-innerchannelopenfailed.md)|Aviso|Falha no DiscoveryClientChannel ao abrir o canal com um ponto de extremidade descoberto com EndpointAddress = '%1' e Via = '%2'. O DiscoveryClientChannel agora tentará usar o ponto de extremidade descoberto disponível Avançar.|Descoberta|  
|[4819 - InnerChannelOpenSucceeded](../../../../../docs/framework/wcf/diagnostics/etw/4819-innerchannelopensucceeded.md)|Informações|O DiscoveryClientChannel descobriu um ponto de extremidade com êxito e abriu o canal usá-lo. O cliente está conectado a um serviço usando EndpointAddress = '%1' e Via = '%2'.|Descoberta|  
|[4820 - SynchronizationContextReset](../../../../../docs/framework/wcf/diagnostics/etw/4820-synchronizationcontextreset.md)|Informações|O SynchronizationContext foi redefinido para seu valor original de %1 pelo DiscoveryClientChannel.|Descoberta|  
|[4821 - SynchronizationContextSetToNull](../../../../../docs/framework/wcf/diagnostics/etw/4821-synchronizationcontextsettonull.md)|Informações|O SynchronizationContext foi definido como nulo pelo DiscoveryClientChannel antes de iniciar a operação de localização.|Descoberta|  
|[5001 - DCSerializeWithSurrogateStart](../../../../../docs/framework/wcf/diagnostics/etw/5001-dcserializewithsurrogatestart.md)|Detalhado|Serialização de DataContract %1 com início de substitutos.|Serialização|  
|[5002 - DCSerializeWithSurrogateStop](../../../../../docs/framework/wcf/diagnostics/etw/5002-dcserializewithsurrogatestop.md)|Detalhado|Serialização de DataContract com parada de substitutos.|Serialização|  
|[5003 - DCDeserializeWithSurrogateStart](../../../../../docs/framework/wcf/diagnostics/etw/5003-dcdeserializewithsurrogatestart.md)|Detalhado|%1 com substitutos início da desserialização DataContract.|Serialização|  
|[5004 - DCDeserializeWithSurrogateStop](../../../../../docs/framework/wcf/diagnostics/etw/5004-dcdeserializewithsurrogatestop.md)|Detalhado|Desserialização DataContract com parada de substitutos.|Serialização|  
|[5005 - ImportKnownTypesStart](../../../../../docs/framework/wcf/diagnostics/etw/5005-importknowntypesstart.md)|Detalhado|ImportKnownTypes iniciar.|Serialização|  
|[5006 - ImportKnownTypesStop](../../../../../docs/framework/wcf/diagnostics/etw/5006-importknowntypesstop.md)|Detalhado|ImportKnownTypes parar.|Serialização|  
|[5007 - DCResolverResolve](../../../../../docs/framework/wcf/diagnostics/etw/5007-dcresolverresolve.md)|Detalhado|Resolução %1 início do resolvedor DataContract.|Serialização|  
|[5008 - DCGenWriterStart](../../../../../docs/framework/wcf/diagnostics/etw/5008-dcgenwriterstart.md)|Detalhado|Gravador de %1 para %2 início de geração DataContract.|Serialização|  
|[5009 - DCGenWriterStop](../../../../../docs/framework/wcf/diagnostics/etw/5009-dcgenwriterstop.md)|Detalhado|Parada de gravador de geração DataContract.|Serialização|  
|[5010 - DCGenReaderStart](../../../../../docs/framework/wcf/diagnostics/etw/5010-dcgenreaderstart.md)|Detalhado|Leitor de %1 para %2 início de geração de DataContract.|Serialização|  
|[5011 - DCGenReaderStop](../../../../../docs/framework/wcf/diagnostics/etw/5011-dcgenreaderstop.md)|Detalhado|Parada na geração DataContract.|Serialização|  
|[5012 - DCJsonGenReaderStart](../../../../../docs/framework/wcf/diagnostics/etw/5012-dcjsongenreaderstart.md)|Detalhado|Leitor %1 para %2 início de geração JSON.|Serialização|  
|[5013 - DCJsonGenReaderStop](../../../../../docs/framework/wcf/diagnostics/etw/5013-dcjsongenreaderstop.md)|Detalhado|Parada na geração do leitor JSON.|Serialização|  
|[5014 - DCJsonGenWriterStart](../../../../../docs/framework/wcf/diagnostics/etw/5014-dcjsongenwriterstart.md)|Detalhado|Gravador de %1 para %2 início de geração JSON.|Serialização|  
|[5015 - DCJsonGenWriterStop](../../../../../docs/framework/wcf/diagnostics/etw/5015-dcjsongenwriterstop.md)|Detalhado|Parada de gravador de geração JSON.|Serialização|  
|[5016 - GenXmlSerializableStart](../../../../../docs/framework/wcf/diagnostics/etw/5016-genxmlserializablestart.md)|Detalhado|Gere Xml serializável para início de '%1'.|Serialização|  
|[5017 - GenXmlSerializableStop](../../../../../docs/framework/wcf/diagnostics/etw/5017-genxmlserializablestop.md)|Detalhado|Gere parada de Xml serializável.|Serialização|  
|[5203 - JsonMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/5203-jsonmessagedecodingstart.md)|Detalhado|JsonMessageEncoder iniciou a decodificação da mensagem.|Canal|  
|[5204 - JsonMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/5204-jsonmessageencodingstart.md)|Detalhado|JsonMessageEncoder iniciou a codificação da mensagem.|Canal|  
|[5402 - TokenValidationStarted](../../../../../docs/framework/wcf/diagnostics/etw/5402-tokenvalidationstarted.md)|Detalhado|Validação de SecurityToken (o tipo '%1' e id '%2') iniciada.|Segurança|  
|[5403 - TokenValidationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5403-tokenvalidationsuccess.md)|Detalhado|Êxito na validação SecurityToken (tipo '%1' e id '%2').|Segurança|  
|[5404 - TokenValidationFailure](../../../../../docs/framework/wcf/diagnostics/etw/5404-tokenvalidationfailure.md)|Erro|Falha na validação do SecurityToken (tipo '%1' e id '%2'). %3|Segurança|  
|[5405 - GetIssuerNameSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5405-getissuernamesuccess.md)|Detalhado|Recuperação de emissor nome: % 1 de tokenid: % 2 foi bem-sucedida.|Segurança|  
|[5406 - GetIssuerNameFailure](../../../../../docs/framework/wcf/diagnostics/etw/5406-getissuernamefailure.md)|Erro|Falha na recuperação do nome do emissor de tokenid: % 1.|Segurança|  
|[5600 - FederationMessageProcessingStarted](../../../../../docs/framework/wcf/diagnostics/etw/5600-federationmessageprocessingstarted.md)|Detalhado|Processamento de mensagem de Federação iniciado.|Segurança|  
|[5601 - FederationMessageProcessingSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5601-federationmessageprocessingsuccess.md)|Detalhado|Processamento de mensagem de Federação bem-sucedido.|Segurança|  
|[5602 - FederationMessageCreationStarted](../../../../../docs/framework/wcf/diagnostics/etw/5602-federationmessagecreationstarted.md)|Detalhado|Criar mensagem de federação de postagem de formulário iniciada.|Segurança|  
|[5603 - FederationMessageCreationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5603-federationmessagecreationsuccess.md)|Detalhado|Criar mensagem de federação de postagem de formulário bem-sucedida.|Segurança|  
|[5604 - SessionCookieReadingStarted](../../../../../docs/framework/wcf/diagnostics/etw/5604-sessioncookiereadingstarted.md)|Detalhado|Leitura do token de sessão do cookie de sessão iniciada.|Segurança|  
|[5605 - SessionCookieReadingSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5605-sessioncookiereadingsuccess.md)|Detalhado|Token de sessão de leitura do cookie de sessão bem-sucedida.|Segurança|  
|[5606 - PrincipalSettingFromSessionTokenStarted](../../../../../docs/framework/wcf/diagnostics/etw/5606-principalsettingfromsessiontokenstarted.md)|Detalhado|Configuração principal do token de sessão iniciada.|Segurança|  
|[5607 - PrincipalSettingFromSessionTokenSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5607-principalsettingfromsessiontokensuccess.md)|Detalhado|Configuração principal do token de sessão bem-sucedida.|Segurança|  
|[57393 - appDomainUnload](../../../../../docs/framework/wcf/diagnostics/etw/57393-appdomainunload.md)|Informações|O descarregamento do AppDomain. AppDomain.FriendlyName %1, ProcessName %2, ProcessId %3.|Infraestrutura|  
|[57394 - HandledException](../../../../../docs/framework/wcf/diagnostics/etw/57394-handledexception.md)|Informações|Tratando uma exceção.|Infraestrutura|  
|[57395 - ShipAssertExceptionMessage](../../../../../docs/framework/wcf/diagnostics/etw/57395-shipassertexceptionmessage.md)|Erro|Ocorreu uma falha inesperada. Aplicativos não devem tentar manipular esse erro. Para fins de diagnóstico, esta mensagem em inglês está associada à falha: %1.|Infraestrutura|  
|[57396 - ThrowingException](../../../../../docs/framework/wcf/diagnostics/etw/57396-throwingexception.md)|Aviso|Gerar uma exceção. Fonte de %1.|Infraestrutura|  
|[57397 - UnhandledException](../../../../../docs/framework/wcf/diagnostics/etw/57397-unhandledexception.md)|Crítico|Exceção sem tratamento.|Infraestrutura|  
|[57399 - TraceCodeEventLogCritical](../../../../../docs/framework/wcf/diagnostics/etw/57399-tracecodeeventlogcritical.md)|Crítico|Gravado no EventLog.|Infraestrutura|  
|[57400 - TraceCodeEventLogError](../../../../../docs/framework/wcf/diagnostics/etw/57400-tracecodeeventlogerror.md)|Erro|Gravado no EventLog.|Infraestrutura|  
|[57401 - TraceCodeEventLogInfo](../../../../../docs/framework/wcf/diagnostics/etw/57401-tracecodeeventloginfo.md)|Informações|Gravado no EventLog.|Infraestrutura|  
|[57402 - TraceCodeEventLogVerbose](../../../../../docs/framework/wcf/diagnostics/etw/57402-tracecodeeventlogverbose.md)|Detalhado|Gravado no EventLog.|Infraestrutura|  
|[57403 - TraceCodeEventLogWarning](../../../../../docs/framework/wcf/diagnostics/etw/57403-tracecodeeventlogwarning.md)|Aviso|Gravado no EventLog.|Infraestrutura|  
|[57404 - HandledExceptionWarning](../../../../../docs/framework/wcf/diagnostics/etw/57404-handledexceptionwarning.md)|Aviso|Tratando uma exceção.|Infraestrutura|  
|[62326 - HttpHandlerPickedForUrl](../../../../../docs/framework/wcf/diagnostics/etw/62326-httphandlerpickedforurl.md)|Informações|O url '%1' hospeda o documento XAML com o elemento raiz de tipo '%2'. O tipo de manipulador HTTP '%3' está selecionado para atender a todas as solicitações feitas a esse url.|WebHost|
