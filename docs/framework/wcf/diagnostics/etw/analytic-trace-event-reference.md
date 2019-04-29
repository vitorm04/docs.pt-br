---
title: Referência de evento de rastreamento analítico
ms.date: 03/30/2017
helpviewer_keywords:
- analytic tracing [WCF]. reference
ms.assetid: e44540cf-44a1-4efc-b965-7fbfd2131d73
ms.openlocfilehash: 0f8b4c15f2afefbc62b98dca66dcf3ccc31b1dc0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61753030"
---
# <a name="analytic-trace-event-reference"></a>Referência de evento de rastreamento analítico
A tabela a seguir define os níveis de eventos, identificadores e mensagens associadas com o rastreamento analítico do WCF.  
  
## <a name="event-reference"></a>Referência de eventos  
  
|ID do evento|Evento em nível|Mensagem de evento|Palavras-chave|  
|--------------|-----------------|-------------------|--------------|  
|[131 - BufferPoolAllocation](../../../../../docs/framework/wcf/diagnostics/etw/131-bufferpoolallocation.md)|Detalhado|Pool alocando %1 Bytes.|Infraestrutura|  
|[132 - BufferPoolChangeQuota](../../../../../docs/framework/wcf/diagnostics/etw/132-bufferpoolchangequota.md)|Detalhado|BufferPool de tamanho %1, a alteração de cota por %2.|Infraestrutura|  
|[133 - ActionItemScheduled](../../../../../docs/framework/wcf/diagnostics/etw/133-actionitemscheduled.md)|Detalhado|Thread de e/s Agendador retorno de chamada invocado.|Infraestrutura|  
|[134 - ActionItemCallbackInvoked](../../../../../docs/framework/wcf/diagnostics/etw/134-actionitemcallbackinvoked.md)|Detalhado|Thread de e/s Agendador retorno de chamada invocado.|Infraestrutura|  
|[201 - ClientMessageInspectorAfterReceiveInvoked](../../../../../docs/framework/wcf/diagnostics/etw/201-clientmessageinspectorafterreceiveinvoked.md)|Informações|O Dispatcher invocado AfterReceiveReply em um ClientMessageInspector do tipo '%1'.|Solução de problemas, ServiceModel|  
|[202 - ClientMessageInspectorBeforeSendInvoked](../../../../../docs/framework/wcf/diagnostics/etw/202-clientmessageinspectorbeforesendinvoked.md)|Informações|O Dispatcher invocado BeforeSendRequest em um ClientMessageInspector do tipo '%1'.|Solução de problemas, ServiceModel|  
|[203 - ClientParameterInspectorAfterCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/203-clientparameterinspectoraftercallinvoked.md)|Informações|O Dispatcher invocado AfterCall em um ClientParameterInspector. do tipo '%1'.|Solução de problemas, ServiceModel|  
|[204 - ClientParameterInspectorBeforeCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/204-clientparameterinspectorbeforecallinvoked.md)|Informações|O Dispatcher invocado BeforeCall em um ClientParameterInspector do tipo '%1'.|Solução de problemas, ServiceModel|  
|[205 - OperationInvoked](../../../../../docs/framework/wcf/diagnostics/etw/205-operationinvoked.md)|Informações|Objekt OperationInvoker chamado o método '%1'.|EndToEndMonitoring, solução de problemas, ServiceModel|  
|[206 - ErrorHandlerInvoked](../../../../../docs/framework/wcf/diagnostics/etw/206-errorhandlerinvoked.md)|Informações|O Dispatcher invocado um ErrorHandler do tipo '%1' com uma exceção do tipo '%3'.  ErrorHandled = = '%2'.|Solução de problemas, ServiceModel|  
|[207 - FaultProviderInvoked](../../../../../docs/framework/wcf/diagnostics/etw/207-faultproviderinvoked.md)|Informações|O Dispatcher invocado um FaultProvider do tipo '%1' com uma exceção do tipo '%2'.|Solução de problemas, ServiceModel|  
|[208 - MessageInspectorAfterReceiveInvoked](../../../../../docs/framework/wcf/diagnostics/etw/208-messageinspectorafterreceiveinvoked.md)|Informações|O Dispatcher invocado AfterReceiveReply em um MessageInspector do tipo '%1'.|Solução de problemas, ServiceModel|  
|[209 - MessageInspectorBeforeSendInvoked](../../../../../docs/framework/wcf/diagnostics/etw/209-messageinspectorbeforesendinvoked.md)|Informações|O Dispatcher invocado BeforeSendRequest em um MessageInspector do tipo '%1'.|Solução de problemas, ServiceModel|  
|[210 - MessageThrottleExceeded](../../../../../docs/framework/wcf/diagnostics/etw/210-messagethrottleexceeded.md)|Aviso|O limite de restrição '%1' de '%2' foi atingido.|HealthMonitoring, EndToEndMonitoring, solução de problemas, ServiceModel|  
|[211 - ParameterInspectorAfterCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/211-parameterinspectoraftercallinvoked.md)|Informações|O Dispatcher invocado AfterCall em um ParameterInspector do tipo '%1'.|Solução de problemas, ServiceModel|  
|[212 - ParameterInspectorBeforeCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/212-parameterinspectorbeforecallinvoked.md)|Informações|O Dispatcher invocado BeforeCall em um ParameterInspector do tipo '%1'.|Solução de problemas, ServiceModel|  
|[213 - ServiceHostStarted](../../../../../docs/framework/wcf/diagnostics/etw/213-servicehoststarted.md)|LogAlways|ServiceHost iniciado: '%1'.|HealthMonitoring, EndToEndMonitoring, solução de problemas, ServiceModel|  
|[214 - OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md)|Informações|Objekt OperationInvoker concluir a chamada para o método '%1'.  A duração da chamada de método era '%2' ms.|HealthMonitoring, EndToEndMonitoring, solução de problemas, ServiceModel|  
|[215 - MessageReceivedByTransport](../../../../../docs/framework/wcf/diagnostics/etw/215-messagereceivedbytransport.md)|Informações|O transporte recebeu uma mensagem de '%1'.|Solução de problemas, ServiceModel|  
|[216 - MessageSentByTransport](../../../../../docs/framework/wcf/diagnostics/etw/216-messagesentbytransport.md)|Informações|O transporte enviou uma mensagem para '%1'.|Solução de problemas, ServiceModel|  
|[217 - ClientOperationPrepared](../../../../../docs/framework/wcf/diagnostics/etw/217-clientoperationprepared.md)|Informações|O cliente está executando a operação '%1' definida no contrato '%2'. A mensagem será enviada para '%3'.|Solução de problemas, ServiceModel|  
|[218 - ClientOperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/218-clientoperationcompleted.md)|Informações|O cliente concluir a execução da operação '%1' definida no contrato '%2'. A mensagem foi enviada para '%3'.|Solução de problemas, ServiceModel|  
|[219 - ServiceException](../../../../../docs/framework/wcf/diagnostics/etw/219-serviceexception.md)|Erro|Houve uma exceção sem tratamento do tipo '%2' durante o processamento da mensagem.  ToString completo da exceção: %1.|HealthMonitoring, EndToEndMonitoring, solução de problemas, ServiceModel|  
|[220 - MessageSentToTransport](../../../../../docs/framework/wcf/diagnostics/etw/220-messagesenttotransport.md)|Informações|O Dispatcher enviou uma mensagem para o transporte. ID de correlação = = '%1'.|EndToEndMonitoring, solução de problemas, ServiceModel|  
|[221 - MessageReceivedFromTransport](../../../../../docs/framework/wcf/diagnostics/etw/221-messagereceivedfromtransport.md)|Informações|O Dispatcher recebeu uma mensagem de transporte. ID de correlação = = '%1'.|EndToEndMonitoring, solução de problemas, ServiceModel|  
|[222 - OperationFailed](../../../../../docs/framework/wcf/diagnostics/etw/222-operationfailed.md)|Aviso|O método '%1' gerou uma exceção sem tratamento quando chamado pelo OperationInvoker. A duração da chamada de método era '%2' ms.|HealthMonitoring, EndToEndMonitoring, solução de problemas, ServiceModel|  
|[223 - OperationFaulted](../../../../../docs/framework/wcf/diagnostics/etw/223-operationfaulted.md)|Aviso|O método '%1' gerou uma FaultException quando invocado pelo OperationInvoker. A duração da chamada de método era '%2' ms.|HealthMonitoring, EndToEndMonitoring, solução de problemas, ServiceModel|  
|[224 - MessageThrottleAtSeventyPercent](../../../../../docs/framework/wcf/diagnostics/etw/224-messagethrottleatseventypercent.md)|Aviso|O limite de restrição '%1' de '%2' é de 70%.|HealthMonitoring, EndToEndMonitoring, solução de problemas, ServiceModel|  
|[226 - IdleServicesClosed](../../../../../docs/framework/wcf/diagnostics/etw/226-idleservicesclosed.md)|LogAlways|Serviços de ociosidade %1 fora %2 total ativado serviços fechados.|HealthMonitoring WebHost|  
|[301 - UserDefinedErrorOccurred](../../../../../docs/framework/wcf/diagnostics/etw/301-userdefinederroroccurred.md)|Erro|Nome: '%1', referência: '%2', carga: %3.|UserEvents, HealthMonitoring, EndToEndMonitoring, solução de problemas, ServiceModel|  
|[302 - UserDefinedWarningOccurred](../../../../../docs/framework/wcf/diagnostics/etw/302-userdefinedwarningoccurred.md)|Aviso|Nome: '%1', referência: '%2', carga: %3.|UserEvents, HealthMonitoring, EndToEndMonitoring, solução de problemas, ServiceModel|  
|[303 - UserDefinedInformationEventOccured](../../../../../docs/framework/wcf/diagnostics/etw/303-userdefinedinformationeventoccured.md)|Informações|Nome: '%1', referência: '%2', carga: %3.|UserEvents, HealthMonitoring, EndToEndMonitoring, solução de problemas, ServiceModel|  
|[401- StopSignPostEvent](../../../../../docs/framework/wcf/diagnostics/etw/401-stopsignpostevent.md)|Informações|Limite de atividade.|Solução de problemas|  
|[402 - StartSignpostEvent](../../../../../docs/framework/wcf/diagnostics/etw/402-startsignpostevent.md)|Informações|Limite de atividade.|Solução de problemas|  
|[403 - SuspendSignpostEvent](../../../../../docs/framework/wcf/diagnostics/etw/403-suspendsignpostevent.md)|Informações|Limite de atividade.|Solução de problemas|  
|[404 - ResumeSignpostEvent](../../../../../docs/framework/wcf/diagnostics/etw/404-resumesignpostevent.md)|Informações|Limite de atividade.|Solução de problemas|  
|[451 - MessageLogInfo](../../../../../docs/framework/wcf/diagnostics/etw/451-messageloginfo.md)|Informações|%1|Troubleshooting, WCFMessageLogging|  
|[452 - MessageLogWarning](../../../../../docs/framework/wcf/diagnostics/etw/452-messagelogwarning.md)|Aviso|%1|Troubleshooting, WCFMessageLogging|  
|[499 - TransferEmitted](../../../../../docs/framework/wcf/diagnostics/etw/499-transferemitted.md)|LogAlways|Evento de transferência emitido.|Troubleshooting, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging|  
|[501 - CompilationStart](../../../../../docs/framework/wcf/diagnostics/etw/501-compilationstart.md)|Informações|Iniciar a compilação.|WebHost|  
|[502 - CompilationStop](../../../../../docs/framework/wcf/diagnostics/etw/502-compilationstop.md)|Informações|Compilação final.|WebHost|  
|[503 - ServiceHostFactoryCreationStart](../../../../../docs/framework/wcf/diagnostics/etw/503-servicehostfactorycreationstart.md)|Informações|ServiceHostFactory começar a criação.|WebHost|  
|[504 - ServiceHostFactoryCreationStop](../../../../../docs/framework/wcf/diagnostics/etw/504-servicehostfactorycreationstop.md)|Informações|Criação de end ServiceHostFactory.|WebHost|  
|[505 - CreateServiceHostStart](../../../../../docs/framework/wcf/diagnostics/etw/505-createservicehoststart.md)|Informações|Comece CreateServiceHost.|WebHost|  
|[506 - CreateServiceHostStop](../../../../../docs/framework/wcf/diagnostics/etw/506-createservicehoststop.md)|Informações|Konec CreateServiceHost.|WebHost|  
|[507 - HostedTransportConfigurationManagerConfigInitStart](../../../../../docs/framework/wcf/diagnostics/etw/507-hostedtransportconfigurationmanagerconfiginitstart.md)|Informações|Správce hostedtransportconfigurationmanager Zahájil inicializaci konfigurace.|WebHost|  
|[508 - HostedTransportConfigurationManagerConfigInitStop](../../../../../docs/framework/wcf/diagnostics/etw/508-hostedtransportconfigurationmanagerconfiginitstop.md)|Informações|Správce hostedtransportconfigurationmanager Zahájil konec inicializace konfigurace.|WebHost|  
|[509 - ServiceHostOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/509-servicehostopenstart.md)|Informações|Správce hostedtransportconfigurationmanager Zahájil konec inicializace konfigurace.|ServiceHost|  
|[510 - ServiceHostOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/510-servicehostopenstop.md)|Informações|Abrir ServiceHost concluída.|ServiceHost|  
|[513 - WebHostRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/513-webhostrequeststart.md)|Informações|Recebida solicitação com o caminho virtual '%2' do AppDomain '%1'.|WebHost|  
|[514 - WebHostRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/514-webhostrequeststop.md)|Informações|Webhostrequest – zastavení|WebHost|  
|[601 - CBAEntryRead](../../../../../docs/framework/wcf/diagnostics/etw/601-cbaentryread.md)|Detalhado|Processado relativní Adresa: '%1' Normalized endereço relativo '%2'.||  
|[602 - CBAMatchFound](../../../../../docs/framework/wcf/diagnostics/etw/602-cbamatchfound.md)|Detalhado|Solicitação de entrada corresponde a um elemento relativní Adresa com endereço '%1'.||  
|[603 - AspNetRoutingService](../../../../../docs/framework/wcf/diagnostics/etw/603-aspnetroutingservice.md)|Detalhado|Solicitação de entrada corresponde a um serviço WCF definido na rota do Asp.Net com endereço %1.|RoutingServices|  
|[604 - AspNetRoute](../../../../../docs/framework/wcf/diagnostics/etw/604-aspnetroute.md)|Detalhado|Uma nova rota Asp.Net '%1' com '%2' de serviceType e serviceHostFactoryType '%3' é adicionada.|RoutingServices|  
|[605 - IncrementBusyCount](../../../../../docs/framework/wcf/diagnostics/etw/605-incrementbusycount.md)|Detalhado|Byla volána metoda IncrementBusyCount. Fonte: %1|WebHost|  
|[606 - DecrementBusyCount](../../../../../docs/framework/wcf/diagnostics/etw/606-decrementbusycount.md)|Detalhado|Byla volána metoda DecrementBusyCount. Fonte: %1|WebHost|  
|[701 - ServiceChannelOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/701-servicechannelopenstart.md)|Detalhado|Operace servicechannelopen.|WebHost|  
|[702 - ServiceChannelOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/702-servicechannelopenstop.md)|Informações|ServiceChannelOpen concluída.|ServiceModel|  
|[703 - ServiceChannelCallStart](../../../../../docs/framework/wcf/diagnostics/etw/703-servicechannelcallstart.md)|Informações|Operace servicechannelcall.|ServiceModel|  
|[704 - ServiceChannelBeginCallStart](../../../../../docs/framework/wcf/diagnostics/etw/704-servicechannelbegincallstart.md)|Informações|Asynchronní volání kanálu ServiceChannel.|ServiceModel|  
|[706 - HttpSendMessageStart](../../../../../docs/framework/wcf/diagnostics/etw/706-httpsendmessagestart.md)|Detalhado|Início de solicitação de envio HTTP.|HTTP|  
|[707 - HttpSendStop](../../../../../docs/framework/wcf/diagnostics/etw/707-httpsendstop.md)|Detalhado|Parar de solicitação de envio HTTP.|HTTP|  
|[708 - HttpMessageReceiveStart](../../../../../docs/framework/wcf/diagnostics/etw/708-httpmessagereceivestart.md)|Detalhado|Mensagem recebida do transporte http.|HTTP|  
|[709 - DispatchMessageStart](../../../../../docs/framework/wcf/diagnostics/etw/709-dispatchmessagestart.md)|Informações|Despacho de mensagens iniciado.|ServiceModel|  
|[710 - HttpContextBeforeProcessAuthentication](../../../../../docs/framework/wcf/diagnostics/etw/710-httpcontextbeforeprocessauthentication.md)|Detalhado|Inicie a autenticação de despacho de mensagens.|ServiceModel|  
|[711 - DispatchMessageBeforeAuthorization](../../../../../docs/framework/wcf/diagnostics/etw/711-dispatchmessagebeforeauthorization.md)|Detalhado|Inicie a autorização despacho de mensagens.|ServiceModel|  
|[712 - DispatchMessageStop](../../../../../docs/framework/wcf/diagnostics/etw/712-dispatchmessagestop.md)|Informações|Conclusão da expedição da mensagem.|ServiceModel|  
|[715 - ClientChannelOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/715-clientchannelopenstart.md)|Informações|Início do ServiceChannel aberto.|ServiceModel|  
|[716 - ClientChannelOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/716-clientchannelopenstop.md)|Informações|Parar abrir do ServiceChannel.|ServiceModel|  
|[717 - HttpSendStreamedMessageStart](../../../../../docs/framework/wcf/diagnostics/etw/717-httpsendstreamedmessagestart.md)|Informações|Mensagem em fluxo de envio HTTP iniciada.|HTTP|  
|[1400 - ChannelInitializationTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1400-channelinitializationtimeout.md)|Erro|1%|ServiceModel|  
|[1401 - CloseTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1401-closetimeout.md)|Erro|1%|ServiceModel|  
|[1402 - IdleTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1402-idletimeout.md)|Erro|Chave de pool de Conexão %1: %2|ServiceModel|  
|[1403 - LeaseTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1403-leasetimeout.md)|Informações|Chave de pool de Conexão %1: %2|ServiceModel|  
|[1405 - OpenTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1405-opentimeout.md)|Erro|%1|ServiceModel|  
|[1406 - ReceiveTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1406-receivetimeout.md)|Erro|%1|ServiceModel|  
|[1407 - SendTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1407-sendtimeout.md)|Erro|%1|ServiceModel|  
|[1409 - InactivityTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1409-inactivitytimeout.md)|Informações|%1|ServiceModel|  
|[1416 - MaxReceivedMessageSizeExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1416-maxreceivedmessagesizeexceeded.md)|Erro|%1|Quota|  
|[1417 - MaxSentMessageSizeExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1417-maxsentmessagesizeexceeded.md)|Erro|%1|Quota|  
|[1418 - MaxOutboundConnectionsPerEndpointExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1418-maxoutboundconnectionsperendpointexceeded.md)|Informações|%1|Quota|  
|[1419 - MaxPendingConnectionsExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1419-maxpendingconnectionsexceeded.md)|Informações|%1|Quota|  
|[1420 - ReaderQuotaExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1420-readerquotaexceeded.md)|Erro|%1|Quota|  
|[1422 - NegotiateTokenAuthenticatorStateCacheExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1422-negotiatetokenauthenticatorstatecacheexceeded.md)|Erro|%1|Quota|  
|[1423 - NegotiateTokenAuthenticatorStateCacheRatio](../../../../../docs/framework/wcf/diagnostics/etw/1423-negotiatetokenauthenticatorstatecacheratio.md)|Detalhado|Negociar a taxa de autenticador de token do cache de estado: %1 / %2|Quota|  
|[1424 - SecuritySessionRatio](../../../../../docs/framework/wcf/diagnostics/etw/1424-securitysessionratio.md)|Detalhado|Taxa de sessão de segurança: %1 / %2|Quota|  
|[1430 - PendingConnectionsRatio](../../../../../docs/framework/wcf/diagnostics/etw/1430-pendingconnectionsratio.md)|Detalhado|Pendente da taxa de conexões: %1 / %2|Quota|  
|[1431 - ConcurrentCallsRatio](../../../../../docs/framework/wcf/diagnostics/etw/1431-concurrentcallsratio.md)|Detalhado|Taxa de sessões simultâneas: %1 / %2|Quota|  
|[1432 - ConcurrentSessionsRatio](../../../../../docs/framework/wcf/diagnostics/etw/1432-concurrentsessionsratio.md)|Detalhado|Taxa de sessões simultâneas: %1 / %2|Quota|  
|[1433 - OutboundConnectionsPerEndpointRatio](../../../../../docs/framework/wcf/diagnostics/etw/1433-outboundconnectionsperendpointratio.md)|Detalhado|Conexões de saída por taxa de ponto de extremidade: %1 / %2|Quota|  
|[1433 - OutboundConnectionsPerEndpointRatio](../../../../../docs/framework/wcf/diagnostics/etw/1433-outboundconnectionsperendpointratio.md)|Detalhado|Conexões de saída por taxa de ponto de extremidade: %1 / %2|Quota|  
|[1436 - PendingMessagesPerChannelRatio](../../../../../docs/framework/wcf/diagnostics/etw/1436-pendingmessagesperchannelratio.md)|Detalhado|Por taxa de canal de mensagens pendentes: %1 / %2|Quota|  
|[1438 - ConcurrentInstancesRatio](../../../../../docs/framework/wcf/diagnostics/etw/1438-concurrentinstancesratio.md)|Detalhado|Taxa de instâncias simultâneas: %1 / %2|Quota|  
|[1439 - PendingAcceptsAtZero](../../../../../docs/framework/wcf/diagnostics/etw/1439-pendingacceptsatzero.md)|Informações|Zero pendentes aceita para a esquerda|Quota|  
|[1441 - MaxSessionSizeReached](../../../../../docs/framework/wcf/diagnostics/etw/1441-maxsessionsizereached.md)|Aviso|1%|Quota|  
|[1442 - ReceiveRetryCountReached](../../../../../docs/framework/wcf/diagnostics/etw/1442-receiveretrycountreached.md)|Aviso|Receber a contagem de repetição atingida na mensagem com id '%1' do MSMQ|Quota|  
|[1443 - MaxRetryCyclesExceededMsmq](../../../../../docs/framework/wcf/diagnostics/etw/1443-maxretrycyclesexceededmsmq.md)|Erro|Ciclos de repetição máximo excedidos na mensagem com id '%1' do MSMQ|Quota|  
|[1445 - ReadPoolMiss](../../../../../docs/framework/wcf/diagnostics/etw/1445-readpoolmiss.md)|Detalhado|Criado novo '%1'|Quota|  
|[1446 - WritePoolMiss](../../../../../docs/framework/wcf/diagnostics/etw/1446-writepoolmiss.md)|Detalhado|Criado novo '%1'|Quota|  
|[1451 - MaxRetryCyclesExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1451-maxretrycyclesexceeded.md)|Erro|1%|Quota|  
|[3300 - ReceiveContextCompleteFailed](../../../../../docs/framework/wcf/diagnostics/etw/3300-receivecontextcompletefailed.md)|Aviso|Falha ao concluir o %1.|Canal|  
|[3301 - ReceiveContextAbandonFailed](../../../../../docs/framework/wcf/diagnostics/etw/3301-receivecontextabandonfailed.md)|Aviso|Falha ao abandonar %1.|Canal|  
|[3303 - ReceiveContextAbandonWithException](../../../../../docs/framework/wcf/diagnostics/etw/3303-receivecontextabandonwithexception.md)|Aviso|Contexto de recebimento com defeito.|ServiceModel|  
|[3303 - ReceiveContextAbandonWithException](../../../../../docs/framework/wcf/diagnostics/etw/3303-receivecontextabandonwithexception.md)|Informações|%1 foi abandonada com exceção: %2.|Canal|  
|[3305 - ClientBaseCachedChannelFactoryCount](../../../../../docs/framework/wcf/diagnostics/etw/3305-clientbasecachedchannelfactorycount.md)|Informações|Número de fábricas de canais armazenadas em cache é: '%1'.  No máximo '%2' fábricas de canais podem ser armazenado em cache.|ServiceModel|  
|[3306 - ClientBaseChannelFactoryAgedOutofCache](../../../../../docs/framework/wcf/diagnostics/etw/3306-clientbasechannelfactoryagedoutofcache.md)|Informações|Uma fábrica de canais foram envelhecer fora do cache porque o cache atingiu seu limite de '%1'.|ServiceModel|  
|[3307 - ClientBaseChannelFactoryCacheHit](../../../../../docs/framework/wcf/diagnostics/etw/3307-clientbasechannelfactorycachehit.md)|Informações|Usado a fábrica de canais correspondente encontrada no cache.|ServiceModel|  
|[3308 - ClientBaseUsingLocalChannelFactory](../../../../../docs/framework/wcf/diagnostics/etw/3308-clientbaseusinglocalchannelfactory.md)|Informações|Não usando a fábrica de canais do cache, ou seja, o cache desabilitado por exemplo.|ServiceModel|  
|[3309 - QueryCompositionExecuted](../../../../../docs/framework/wcf/diagnostics/etw/3309-querycompositionexecuted.md)|Informações|Composição de consulta usando '%1' foi executada no Uri de solicitação: '%2'.|ServiceModel|  
|[3310 - DispatchFailed](../../../../../docs/framework/wcf/diagnostics/etw/3310-dispatchfailed.md)|Erro|A operação '%1' foi despachada com erros.|ServiceModel|  
|[3311 - DispatchSuccessful](../../../../../docs/framework/wcf/diagnostics/etw/3311-dispatchsuccessful.md)|Informações|A operação '%1' foi enviada com êxito.|ServiceModel|  
|[3312 - MessageReadByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3312-messagereadbyencoder.md)|Informações|Uma mensagem com tamanho de bytes de '%1' foi lida pelo codificador.|Canal|  
|[3312 - MessageReadByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3312-messagereadbyencoder.md)|Informações|Uma mensagem com tamanho de bytes de '%1' foi gravada pelo codificador.|Canal|  
|[3314 - SessionIdleTimeout](../../../../../docs/framework/wcf/diagnostics/etw/3314-sessionidletimeout.md)|Erro|Sessão anulando ocioso canal uri: '%1'.|ServiceModel|  
|[3319 - SocketAcceptEnqueued](../../../../../docs/framework/wcf/diagnostics/etw/3319-socketacceptenqueued.md)|Detalhado|Conexão aceitar iniciado.|TCP|  
|[3320 - SocketAccepted](../../../../../docs/framework/wcf/diagnostics/etw/3320-socketaccepted.md)|Detalhado|ListenerId:% 1 aceito SocketId:% 2.|TCP|  
|[3321 - ConnectionPoolMiss](../../../../../docs/framework/wcf/diagnostics/etw/3321-connectionpoolmiss.md)|Detalhado|O pool para %1 não tem nenhuma conexão disponível e conexões de %2 ocupado.|Canal|  
|[3322 - DispatchFormatterDeserializeRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3322-dispatchformatterdeserializerequeststart.md)|Detalhado|Dispatcher ao desserializar a mensagem de solicitação.|ServiceModel|  
|[3323 - DispatchFormatterDeserializeRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/3323-dispatchformatterdeserializerequeststop.md)|Detalhado|A mensagem de solicitação de desserialização de Dispatcher concluído.|ServiceModel|  
|[3324 - DispatchFormatterSerializeReplyStart](../../../../../docs/framework/wcf/diagnostics/etw/3324-dispatchformatterserializereplystart.md)|Detalhado|Serialização de Dispatcher iniciado da mensagem de resposta.|ServiceModel|  
|[3325 - DispatchFormatterSerializeReplyStop](../../../../../docs/framework/wcf/diagnostics/etw/3325-dispatchformatterserializereplystop.md)|Detalhado|Serialização de Dispatcher concluída da mensagem de resposta.|ServiceModel|  
|[3326 - ClientFormatterSerializeRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3326-clientformatterserializerequeststart.md)|Detalhado|Serialização de solicitação do cliente é iniciado.|ServiceModel|  
|[3327 - ClientFormatterSerializeRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/3327-clientformatterserializerequeststop.md)|Detalhado|Serialização de cliente concluída da mensagem de solicitação.|ServiceModel|  
|[3328 - ClientFormatterDeserializeReplyStart](../../../../../docs/framework/wcf/diagnostics/etw/3328-clientformatterdeserializereplystart.md)|Detalhado|Cliente iniciado ao desserializar a mensagem de resposta.|ServiceModel|  
|[3329 - ClientFormatterDeserializeReplyStop](../../../../../docs/framework/wcf/diagnostics/etw/3329-clientformatterdeserializereplystop.md)|Detalhado|Cliente concluída ao desserializar a mensagem de resposta.|ServiceModel|  
|[3330 - SecurityNegotiationStart](../../../../../docs/framework/wcf/diagnostics/etw/3330-securitynegotiationstart.md)|Detalhado|Negociação de segurança é iniciado.|Segurança|  
|[3331 - SecurityNegotiationStop](../../../../../docs/framework/wcf/diagnostics/etw/3331-securitynegotiationstop.md)|Detalhado|Negociação de segurança concluída.|Segurança|  
|[3332 - SecurityTokenProviderOpened](../../../../../docs/framework/wcf/diagnostics/etw/3332-securitytokenprovideropened.md)|Detalhado|Abertura de SecurityTokenProvider concluída.|Segurança|  
|[3333 - OutgoingMessageSecured](../../../../../docs/framework/wcf/diagnostics/etw/3333-outgoingmessagesecured.md)|Detalhado|Mensagem de saída foi protegida.|Segurança|  
|[3334 - IncomingMessageVerified](../../../../../docs/framework/wcf/diagnostics/etw/3334-incomingmessageverified.md)|Detalhado|Mensagem de entrada foi verificada.|Segurança ServiceModel|  
|[3335 - GetServiceInstanceStart](../../../../../docs/framework/wcf/diagnostics/etw/3335-getserviceinstancestart.md)|Detalhado|Recuperação de instância de serviço é iniciado.|ServiceModel|  
|[3336 - GetServiceInstanceStop](../../../../../docs/framework/wcf/diagnostics/etw/3336-getserviceinstancestop.md)|Detalhado|Recuperar a instância de serviço.|ServiceModel|  
|[3337 - ChannelReceiveStart](../../../../../docs/framework/wcf/diagnostics/etw/3337-channelreceivestart.md)|Detalhado|ChannelHandlerId:% 1 - mensagem receber loop iniciado.|Canal|  
|[3338 - ChannelReceiveStop](../../../../../docs/framework/wcf/diagnostics/etw/3338-channelreceivestop.md)|Detalhado|ChannelHandlerId:% 1 - mensagem receber loop interrompido.|Canal|  
|[3339 - ChannelFactoryCreated](../../../../../docs/framework/wcf/diagnostics/etw/3339-channelfactorycreated.md)|Detalhado|ChannelFactory criado.|ServiceModel|  
|[3340 - PipeConnectionAcceptStart](../../../../../docs/framework/wcf/diagnostics/etw/3340-pipeconnectionacceptstart.md)|Detalhado|Conexão de pipe aceitar iniciado em %1.|Canal|  
|[3341 - PipeConnectionAcceptStop](../../../../../docs/framework/wcf/diagnostics/etw/3341-pipeconnectionacceptstop.md)|Detalhado|Aceita a conexão de pipe.|Canal|  
|[3342 - EstablishConnectionStart](../../../../../docs/framework/wcf/diagnostics/etw/3342-establishconnectionstart.md)|Detalhado|Estabelecimento de Conexão é iniciada para %1.|Canal|  
|[3343 - EstablishConnectionStop](../../../../../docs/framework/wcf/diagnostics/etw/3343-establishconnectionstop.md)|Detalhado|Conexão estabelecida.|Canal|  
|[3345 - SessionPreambleUnderstood](../../../../../docs/framework/wcf/diagnostics/etw/3345-sessionpreambleunderstood.md)|Detalhado|Preambule relace Pro '%1' compreendido.|Canal|  
|[3346 - ConnectionReaderSendFault](../../../../../docs/framework/wcf/diagnostics/etw/3346-connectionreadersendfault.md)|Erro|Leitor de Conexão enviar falha de '%1'.|Canal|  
|[3347 - SocketAcceptClosed](../../../../../docs/framework/wcf/diagnostics/etw/3347-socketacceptclosed.md)|Detalhado|Aceitação de soquete fechado.|TCP|  
|[3348 - ServiceHostFaulted](../../../../../docs/framework/wcf/diagnostics/etw/3348-servicehostfaulted.md)|Crítico|Host de serviço com defeito.|TCP|  
|[3349 - ListenerOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/3349-listeneropenstart.md)|Detalhado|Ouvinte de abertura para '%1'.|Canal|  
|[3350 - ListenerOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/3350-listeneropenstop.md)|Detalhado|Abrir do ouvinte foi concluído.|Canal|  
|[3351 - ServerMaxPooledConnectionsQuotaReached](../../../../../docs/framework/wcf/diagnostics/etw/3351-servermaxpooledconnectionsquotareached.md)|Detalhado|Cota de máximo de conexões em pool do servidor atingido.|Quota|  
|[3352 - TcpConnectionTimedOut](../../../../../docs/framework/wcf/diagnostics/etw/3352-tcpconnectiontimedout.md)|Erro|SocketId:% 1 para endereço remoto %2 atingiu o tempo limite.|TCP|  
|[3353 - TcpConnectionResetError](../../../../../docs/framework/wcf/diagnostics/etw/3353-tcpconnectionreseterror.md)|Aviso|SocketId:% 1 para endereço remoto %2 tinha uma conexão de redefinição de erro.|TCP|  
|[3354 - ServiceSecurityNegotiationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/3354-servicesecuritynegotiationcompleted.md)|Detalhado|Negociação de segurança do serviço concluída.|Segurança|  
|[3355 - SecurityNegotiationProcessingFailure](../../../../../docs/framework/wcf/diagnostics/etw/3355-securitynegotiationprocessingfailure.md)|Erro|Falha no processamento de negociação de segurança.|Segurança|  
|[3356 - SecurityIdentityVerificationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3356-securityidentityverificationsuccess.md)|Detalhado|Êxito na verificação de segurança.|Segurança|  
|[3357 - SecurityIdentityVerificationFailure](../../../../../docs/framework/wcf/diagnostics/etw/3357-securityidentityverificationfailure.md)|Erro|Falha na verificação de segurança.|Segurança|  
|[3358 - PortSharingDuplicatedSocket](../../../../../docs/framework/wcf/diagnostics/etw/3358-portsharingduplicatedsocket.md)|Detalhado|Byl zduplikován soket Pro %1.|ActivationServices|  
|[3359 - SecurityImpersonationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3359-securityimpersonationsuccess.md)|Detalhado|Representação de segurança foi bem-sucedida.|Segurança|  
|[3360 - SecurityImpersonationFailure](../../../../../docs/framework/wcf/diagnostics/etw/3360-securityimpersonationfailure.md)|Aviso|Falha na representação de segurança.|Segurança|  
|[3361 - HttpChannelRequestAborted](../../../../../docs/framework/wcf/diagnostics/etw/3361-httpchannelrequestaborted.md)|Aviso|Solicitação de canal de HTTP é anulada.|HTTP|  
|[3362 - HttpChannelResponseAborted](../../../../../docs/framework/wcf/diagnostics/etw/3362-httpchannelresponseaborted.md)|Aviso|Resposta de canal de HTTP é anulada.|HTTP|  
|[3363 - HttpAuthFailed](../../../../../docs/framework/wcf/diagnostics/etw/3363-httpauthfailed.md)|Aviso|Falha na autenticação HTTP.|HTTP|  
|[3364 - SharedListenerProxyRegisterStart](../../../../../docs/framework/wcf/diagnostics/etw/3364-sharedlistenerproxyregisterstart.md)|Detalhado|Registrace SharedListenerProxy iniciado para o uri '%1'.|ActivationServices|  
|[3365 - SharedListenerProxyRegisterStop](../../../../../docs/framework/wcf/diagnostics/etw/3365-sharedlistenerproxyregisterstop.md)|Detalhado|Parar de registrar SharedListenerProxy.|ActivationServices|  
|[3366 - SharedListenerProxyRegisterFailed](../../../../../docs/framework/wcf/diagnostics/etw/3366-sharedlistenerproxyregisterfailed.md)|Erro|Registre-se de SharedListenerProxy falhou com status '%1'.|ActivationServices|  
|[3367 - ConnectionPoolPreambleFailed](../../../../../docs/framework/wcf/diagnostics/etw/3367-connectionpoolpreamblefailed.md)|Erro|ConnectionPoolPreambleFailed.|Canal|  
|[3368 - SslOnInitiateUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3368-ssloninitiateupgrade.md)|Detalhado|SslOnAcceptUpgradeStart|Segurança|  
|[3369 - SslOnAcceptUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3369-sslonacceptupgrade.md)|Detalhado|SslOnAcceptUpgradeStop|Segurança|  
|[3370 - BinaryMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3370-binarymessageencodingstart.md)|Detalhado|Kodér BinaryMessageEncoder zahájil kódování zprávy.|Canal|  
|[3371 - MtomMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3371-mtommessageencodingstart.md)|Detalhado|Kodér MtomMessageEncoder zahájil kódování zprávy.|Canal|  
|[3372 - TextMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3372-textmessageencodingstart.md)|Detalhado|Kodér TextMessageEncoder zahájil kódování zprávy.|Canal|  
|[3373 - BinaryMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3373-binarymessagedecodingstart.md)|Detalhado|Kodér BinaryMessageEncoder zahájil dekódování zprávy.|Canal|  
|[3374 - MtomMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3374-mtommessagedecodingstart.md)|Detalhado|Kodér MtomMessageEncoder zahájil dekódování zprávy.|Canal|  
|[3375 - TextMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3375-textmessagedecodingstart.md)|Detalhado|Kodér TextMessageEncoder zahájil dekódování zprávy.|Canal|  
|[3376 - HttpResponseReceiveStart](../../../../../docs/framework/wcf/diagnostics/etw/3376-httpresponsereceivestart.md)|Informações|Transporte de HTTP ao receber uma mensagem.|HTTP|  
|[3377 - SocketReadStop](../../../../../docs/framework/wcf/diagnostics/etw/3377-socketreadstop.md)|Detalhado|Bytes de leitura '%2' SocketId:% 1 de leitura de '%3'.|TCP|  
|[3378 - SocketAsyncReadStop](../../../../../docs/framework/wcf/diagnostics/etw/3378-socketasyncreadstop.md)|Detalhado|Bytes de leitura '%2' SocketId:% 1 de leitura de '%3'.|TCP|  
|[3379 - SocketWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3379-socketwritestart.md)|Detalhado|SocketId:% 1 bytes de gravação '%2' para '%3'.|TCP|  
|[3380 - SocketAsyncWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3380-socketasyncwritestart.md)|Detalhado|SocketId:% 1 bytes de gravação '%2' para '%3'.|TCP|  
|[3381 - SequenceAcknowledgementSent](../../../../../docs/framework/wcf/diagnostics/etw/3381-sequenceacknowledgementsent.md)|Detalhado|Confirmação de SessionId:% 1 enviada.|Canal|  
|[3382 - ClientReliableSessionReconnect](../../../../../docs/framework/wcf/diagnostics/etw/3382-clientreliablesessionreconnect.md)|Informações|Reconectando SessionId:% 1.|Canal|  
|[3383 - ReliableSessionChannelFaulted](../../../../../docs/framework/wcf/diagnostics/etw/3383-reliablesessionchannelfaulted.md)|Informações|SessionId:% 1 com defeito.|Canal|  
|[3384 - WindowsStreamSecurityOnInitiateUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3384-windowsstreamsecurityoninitiateupgrade.md)|Detalhado|Atualização de segurança inicial WindowsStreamSecurity.|Segurança|  
|[3385 - WindowsStreamSecurityOnAcceptUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3385-windowsstreamsecurityonacceptupgrade.md)|Detalhado|Segurança em aceitar a atualização de fluxo de Windows.|Segurança|  
|[3386 - SocketConnectionAbort](../../../../../docs/framework/wcf/diagnostics/etw/3386-socketconnectionabort.md)|Aviso|SocketId:% 1 está sendo anulado.|TCP|  
|[3388 - HttpGetContextStart](../../../../../docs/framework/wcf/diagnostics/etw/3388-httpgetcontextstart.md)|Detalhado|Zahájení kontextu HttpGetContext|HTTP|  
|[3389 - ClientSendPreambleStart](../../../../../docs/framework/wcf/diagnostics/etw/3389-clientsendpreamblestart.md)|Detalhado|Cliente odesílání preambule klienta.|Canal|  
|[3390 - ClientSendPreambleStop](../../../../../docs/framework/wcf/diagnostics/etw/3390-clientsendpreamblestop.md)|Detalhado|Parar de preâmbulo envio do cliente.|Canal|  
|[3391 - HttpMessageReceiveFailed](../../../../../docs/framework/wcf/diagnostics/etw/3391-httpmessagereceivefailed.md)|Aviso|Falha de recebimento de mensagem HTTP.|HTTP|  
|[3392 - TransactionScopeCreate](../../../../../docs/framework/wcf/diagnostics/etw/3392-transactionscopecreate.md)|Informações|TransactionScope está sendo criado com LocalIdentifier: '%1' e DistributedIdentifier: '%2'.|ServiceModel|  
|[3393 - StreamedMessageReadByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3393-streamedmessagereadbyencoder.md)|Informações|Uma mensagem em fluxo foi lido pelo codificador.|Canal|  
|[3394 - StreamedMessageWrittenByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3394-streamedmessagewrittenbyencoder.md)|Informações|Uma mensagem em fluxo foi escrita pelo codificador.|Canal|  
|[3395 - MessageWrittenAsynchronouslyByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3395-messagewrittenasynchronouslybyencoder.md)|Informações|Uma mensagem foi escrita de forma assíncrona pelo codificador.|Canal|  
|[3396 - BufferedAsyncWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3396-bufferedasyncwritestart.md)|Informações|Bytes de gravação BufferId:% 1 concluída '%2' para o fluxo subjacente.|Canal|  
|[3397 - BufferedAsyncWriteStop](../../../../../docs/framework/wcf/diagnostics/etw/3397-bufferedasyncwritestop.md)|Informações|Uma mensagem foi escrita de forma assíncrona pelo codificador.|Canal|  
|[3398 - PipeSharedMemoryCreated](../../../../../docs/framework/wcf/diagnostics/etw/3398-pipesharedmemorycreated.md)|Detalhado|Redirecione a memória compartilhada criada em '%1'.|Canal|  
|[3399 - NamedPipeCreated](../../../../../docs/framework/wcf/diagnostics/etw/3399-namedpipecreated.md)|Detalhado|Pipe nomeado '%1' foi criado.|Canal|  
|[3401 - SignatureVerificationStart](../../../../../docs/framework/wcf/diagnostics/etw/3401-signatureverificationstart.md)|Detalhado|Verificação de assinatura é iniciado.|Segurança|  
|[3402 - SignatureVerificationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3402-signatureverificationsuccess.md)|Detalhado|Êxito na verificação de assinatura.|Segurança|  
|[3403 - WrappedKeyDecryptionStart](../../../../../docs/framework/wcf/diagnostics/etw/3403-wrappedkeydecryptionstart.md)|Detalhado|Encapsulado iniciada de descriptografia de chave.|Segurança|  
|[3404 - WrappedKeyDecryptionSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3404-wrappedkeydecryptionsuccess.md)|Detalhado|Descriptografia de chave encapsulada com êxito.|Segurança|  
|[3405 - EncryptedDataProcessingStart](../../../../../docs/framework/wcf/diagnostics/etw/3405-encrypteddataprocessingstart.md)|Detalhado|Criptografado de processamento de dados iniciado.|Segurança|  
|[3406 - EncryptedDataProcessingSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3406-encrypteddataprocessingsuccess.md)|Detalhado|Êxito ao processamento de dados criptografado.|Segurança|  
|[3407 - HttpPipelineProcessInboundRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3407-httppipelineprocessinboundrequeststart.md)|Detalhado|Manipulador de mensagens HTTP iniciado o processamento de solicitação de entrada.|HTTP|  
|[3408 - HttpPipelineBeginProcessInboundRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3408-httppipelinebeginprocessinboundrequeststart.md)|Detalhado|Manipulador de mensagens HTTP ao processar a solicitação de entrada de forma assíncrona.|HTTP|  
|[3409 - HttpPipelineProcessInboundRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/3409-httppipelineprocessinboundrequeststop.md)|Detalhado|Manipulador de mensagens HTTP conclui o processamento de uma solicitação de entrada.|HTTP|  
|[3410 - HttpPipelineFaulted](../../../../../docs/framework/wcf/diagnostics/etw/3410-httppipelinefaulted.md)|Aviso|Manipulador de mensagens HTTP está com defeito.|HTTP|  
|[3411 - HttpPipelineTimeoutException](../../../../../docs/framework/wcf/diagnostics/etw/3411-httppipelinetimeoutexception.md)|Erro|Tempo limite da conexão WebSocket.|HTTP|  
|[3412 - HttpPipelineProcessResponseStart](../../../../../docs/framework/wcf/diagnostics/etw/3412-httppipelineprocessresponsestart.md)|Detalhado|Manipulador de mensagens HTTP ao processar a resposta.|HTTP|  
|[3413 - HttpPipelineBeginProcessResponseStart](../../../../../docs/framework/wcf/diagnostics/etw/3413-httppipelinebeginprocessresponsestart.md)|Detalhado|Manipulador de mensagens HTTP ao processar a resposta de forma assíncrona.|HTTP|  
|[3414 - HttpPipelineProcessResponseStop](../../../../../docs/framework/wcf/diagnostics/etw/3414-httppipelineprocessresponsestop.md)|Detalhado|Manipulador de mensagens HTTP conclui o processamento de resposta.|HTTP|  
|[3415 - WebSocketConnectionRequestSendStart](../../../../../docs/framework/wcf/diagnostics/etw/3415-websocketconnectionrequestsendstart.md)|Detalhado|Solicitação de conexão de WebSocket para '%1' Enviar início.|HTTP|  
|[3416 - WebSocketConnectionRequestSendStop](../../../../../docs/framework/wcf/diagnostics/etw/3416-websocketconnectionrequestsendstop.md)|Detalhado|WebSocketId:% 1 solicitação de conexão enviada.|HTTP|  
|[3417 - WebSocketConnectionAcceptStart](../../../../../docs/framework/wcf/diagnostics/etw/3417-websocketconnectionacceptstart.md)|Detalhado|Conexão de WebSocket aceitar o início.|HTTP|  
|[3418 - WebSocketConnectionAccepted](../../../../../docs/framework/wcf/diagnostics/etw/3418-websocketconnectionaccepted.md)|Detalhado|Conexão WebSocketId:% 1 aceito.|HTTP|  
|[3419 - WebSocketConnectionDeclined](../../../../../docs/framework/wcf/diagnostics/etw/3419-websocketconnectiondeclined.md)|Erro|Conexão de WebSocket com código de status '%1'|HTTP|  
|[3420 - WebSocketConnectionFailed](../../../../../docs/framework/wcf/diagnostics/etw/3420-websocketconnectionfailed.md)|Erro|Falha na solicitação de conexão de WebSocket: '%1'|HTTP|  
|[3421 - WebSocketConnectionAborted](../../../../../docs/framework/wcf/diagnostics/etw/3421-websocketconnectionaborted.md)|Erro|WebSocketId:% 1 conexão será anulada.|HTTP|  
|[3422 - WebSocketAsyncWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3422-websocketasyncwritestart.md)|Detalhado|WebSocketId:% 1 bytes de gravação '%2' para '%3'.|HTTP|  
|[3423 - WebSocketAsyncWriteStop](../../../../../docs/framework/wcf/diagnostics/etw/3423-websocketasyncwritestop.md)|Detalhado|Parar de gravação assíncrona WebSocketId:% 1.|HTTP|  
|[3424 - WebSocketAsyncReadStart](../../../../../docs/framework/wcf/diagnostics/etw/3424-websocketasyncreadstart.md)|Detalhado|Início WebSocketId:% 1 de leitura.|HTTP|  
|[3425 - WebSocketAsyncReadStop](../../../../../docs/framework/wcf/diagnostics/etw/3425-websocketasyncreadstop.md)|Detalhado|WebSocketId:% 1 ler bytes de '%2' de '%3'.|HTTP|  
|[3426 - WebSocketCloseSent](../../../../../docs/framework/wcf/diagnostics/etw/3426-websocketclosesent.md)|Detalhado|WebSocketId:% 1 enviando fechar a mensagem para '%2' com o status de fechamento '%3'.|HTTP|  
|[3427 - WebSocketCloseOutputSent](../../../../../docs/framework/wcf/diagnostics/etw/3427-websocketcloseoutputsent.md)|Detalhado|WebSocketId:% 1 enviando fechar a mensagem de saída para '%2' com o status de fechamento '%3'.|HTTP|  
|[3428 - WebSocketConnectionClosed](../../../../../docs/framework/wcf/diagnostics/etw/3428-websocketconnectionclosed.md)|Detalhado|WebSocketId:% 1 conexão é fechada.|HTTP|  
|[3429 - WebSocketCloseStatusReceived](../../../../../docs/framework/wcf/diagnostics/etw/3429-websocketclosestatusreceived.md)|Detalhado|Conexão WebSocketId:% 1 Fechar mensagem recebida com status '%2'.|HTTP|  
|[3430 - WebSocketUseVersionFromClientWebSocketFactory](../../../../../docs/framework/wcf/diagnostics/etw/3430-websocketuseversionfromclientwebsocketfactory.md)|Detalhado|Usando o WebSocketVersion de uma fábrica de WebSocket do cliente do tipo '%1'.|HTTP|  
|[3431 - WebSocketCreateClientWebSocketWithFactory](../../../../../docs/framework/wcf/diagnostics/etw/3431-websocketcreateclientwebsocketwithfactory.md)|Detalhado|Criando o cliente WebSocket com um alocador do tipo '%1'.|HTTP|  
|[3553 - XamlServicesLoadStart](../../../../../docs/framework/wcf/diagnostics/etw/3553-xamlservicesloadstart.md)|Informações|XamlServicesLoad start|WebHost|  
|[3554 - XamlServicesLoadStop](../../../../../docs/framework/wcf/diagnostics/etw/3554-xamlservicesloadstop.md)|Informações|Xamlservicesload-Zastavení|WebHost|  
|[3555 - CreateWorkflowServiceHostStart](../../../../../docs/framework/wcf/diagnostics/etw/3555-createworkflowservicehoststart.md)|Informações|Início CreateWorkflowServiceHost|WebHost|  
|[3556 - CreateWorkflowServiceHostStop](../../../../../docs/framework/wcf/diagnostics/etw/3556-createworkflowservicehoststop.md)|Informações|Zastavení metody Createworkflowservicehost|WebHost|  
|[3558 - ServiceActivationStart](../../../../../docs/framework/wcf/diagnostics/etw/3558-serviceactivationstart.md)|Informações|Início do serviço de ativação|WebHost|  
|[3559 - ServiceActivationStop](../../../../../docs/framework/wcf/diagnostics/etw/3559-serviceactivationstop.md)|Informações|Ativação do serviço de parada|WebHost|  
|[3560 - ServiceActivationAvailableMemory](../../../../../docs/framework/wcf/diagnostics/etw/3560-serviceactivationavailablememory.md)|Detalhado|Memória disponível (bytes): %1|Quota|  
|[3800 - RoutingServiceClosingClient](../../../../../docs/framework/wcf/diagnostics/etw/3800-routingserviceclosingclient.md)|Informações|O serviço de roteamento está fechando o cliente '%1'.|RoutingServices|  
|[3800 - RoutingServiceClosingClient](../../../../../docs/framework/wcf/diagnostics/etw/3800-routingserviceclosingclient.md)|Aviso|Cliente do serviço de roteamento '%1' apresentou falha.|RoutingServices|  
|[3802 - RoutingServiceCompletingOneWay](../../../../../docs/framework/wcf/diagnostics/etw/3802-routingservicecompletingoneway.md)|Informações|Uma mensagem de uma maneira de serviço de roteamento está sendo concluída.|RoutingServices|  
|[3803 - RoutingServiceProcessingFailure](../../../../../docs/framework/wcf/diagnostics/etw/3803-routingserviceprocessingfailure.md)|Erro|O serviço de roteamento falhou ao processar uma mensagem no ponto de extremidade com o endereço '%1'.|RoutingServices|  
|[3804 - RoutingServiceCreatingClientForEndpoint](../../../../../docs/framework/wcf/diagnostics/etw/3804-routingservicecreatingclientforendpoint.md)|Informações|O serviço de roteamento é criando um cliente para o ponto de extremidade: '%1'.|RoutingServices|  
|[3805 - RoutingServiceDisplayConfig](../../../../../docs/framework/wcf/diagnostics/etw/3805-routingservicedisplayconfig.md)|Detalhado|O serviço de roteamento é configurado com RouteOnHeadersOnly: %1, SoapProcessingEnabled: %2, EnsureOrderedDispatch: %3.|RoutingServices|  
|[3807 - RoutingServiceCompletingTwoWay](../../../../../docs/framework/wcf/diagnostics/etw/3807-routingservicecompletingtwoway.md)|Informações|Uma mensagem de resposta de solicitação de serviço de roteamento está sendo concluída.|RoutingServices|  
|[3809 - RoutingServiceMessageRoutedToEndpoints](../../../../../docs/framework/wcf/diagnostics/etw/3809-routingservicemessageroutedtoendpoints.md)|Detalhado|O serviço de roteamento roteado mensagem com ID: '%1' para %2 listas de ponto de extremidade.|RoutingServices|  
|[3810 - RoutingServiceConfigurationApplied](../../../../../docs/framework/wcf/diagnostics/etw/3810-routingserviceconfigurationapplied.md)|Informações|Um novo RoutingConfiguration foi aplicada ao serviço de roteamento.|RoutingServices|  
|[3815 - RoutingServiceProcessingMessage](../../../../../docs/framework/wcf/diagnostics/etw/3815-routingserviceprocessingmessage.md)|Informações|O serviço de roteamento está processando uma mensagem com ID: '%1', ação: '%2', URL de entrada: '%3' recebido na transação: %4.|RoutingServices|  
|[3816 - RoutingServiceTransmittingMessage](../../../../../docs/framework/wcf/diagnostics/etw/3816-routingservicetransmittingmessage.md)|Informações|O serviço de roteamento está transmitindo uma mensagem com ID: '%1' [operação %2] para '%3'.|RoutingServices|  
|[3817 - RoutingServiceCommittingTransaction](../../../../../docs/framework/wcf/diagnostics/etw/3817-routingservicecommittingtransaction.md)|Informações|O serviço de roteamento está confirmando uma transação com id: '%1'.|RoutingServices|  
|[3818 - RoutingServiceDuplexCallbackException](../../../../../docs/framework/wcf/diagnostics/etw/3818-routingserviceduplexcallbackexception.md)|Erro|Componente de serviço de roteamento %1 encontrou uma exceção de retorno de chamada duplex.|RoutingServices|  
|[3819 - RoutingServiceMovedToBackup](../../../../../docs/framework/wcf/diagnostics/etw/3819-routingservicemovedtobackup.md)|Informações|Roteamento de mensagem de serviço com ID: '%1' [%2 operação] movidos para o ponto de extremidade de backup '%3'.|RoutingServices|  
|[3820 - RoutingServiceCreatingTransaction](../../../../../docs/framework/wcf/diagnostics/etw/3820-routingservicecreatingtransaction.md)|Informações|O serviço de roteamento criada uma nova transação com a id '%1' para o processamento de mensagem (NS).|RoutingServices|  
|[3821 - RoutingServiceCloseFailed](../../../../../docs/framework/wcf/diagnostics/etw/3821-routingserviceclosefailed.md)|Aviso|O serviço de roteamento falhou durante o fechamento do cliente de saída '%1'.|RoutingServices|  
|[3822 - RoutingServiceSendingResponse](../../../../../docs/framework/wcf/diagnostics/etw/3822-routingservicesendingresponse.md)|Informações|O serviço de roteamento é enviar de volta uma mensagem de resposta com ação '%1'.|RoutingServices|  
|[3823 - RoutingServiceSendingFaultResponse](../../../../../docs/framework/wcf/diagnostics/etw/3823-routingservicesendingfaultresponse.md)|Aviso|O serviço de roteamento é enviar de volta uma mensagem de resposta de falha com ação '%1'.|RoutingServices|  
|[3824 - RoutingServiceCompletingReceiveContext](../../../../../docs/framework/wcf/diagnostics/etw/3824-routingservicecompletingreceivecontext.md)|Detalhado|O serviço de roteamento está chamando Receivecontext para mensagem com ID: '%1'.|RoutingServices|  
|[3825 - RoutingServiceAbandoningReceiveContext](../../../../../docs/framework/wcf/diagnostics/etw/3825-routingserviceabandoningreceivecontext.md)|Aviso|O serviço de roteamento está chamando ReceiveContext.Abandon para mensagem com ID: '%1'.|RoutingServices|  
|[3826 - RoutingServiceUsingExistingTransaction](../../../../../docs/framework/wcf/diagnostics/etw/3826-routingserviceusingexistingtransaction.md)|Detalhado|O serviço de roteamento enviará mensagens usando a transação existente '%1'.|RoutingServices|  
|[3827 - RoutingServiceTransmitFailed](../../../../../docs/framework/wcf/diagnostics/etw/3827-routingservicetransmitfailed.md)|Aviso|O serviço de roteamento falhou ao enviar para '%1'.|RoutingServices|  
|[3828 - RoutingServiceFilterTableMatchStart](../../../../../docs/framework/wcf/diagnostics/etw/3828-routingservicefiltertablematchstart.md)|Informações|Início de correspondência de MessageFilterTable do serviço de roteamento.|RoutingServices|  
|[3829 - RoutingServiceFilterTableMatchStop](../../../../../docs/framework/wcf/diagnostics/etw/3829-routingservicefiltertablematchstop.md)|Informações|Parar de correspondência MessageFilterTable do serviço de roteamento.|RoutingServices|  
|[3830 - RoutingServiceAbortingChannel](../../../../../docs/framework/wcf/diagnostics/etw/3830-routingserviceabortingchannel.md)|Detalhado|O serviço de roteamento é chamar abort em canal: '%1'.|RoutingServices|  
|[3831 - RoutingServiceHandledException](../../../../../docs/framework/wcf/diagnostics/etw/3831-routingservicehandledexception.md)|Detalhado|O serviço de roteamento tratou a exceção.|RoutingServices|  
|[3832 - RoutingServiceTransmitSucceeded](../../../../../docs/framework/wcf/diagnostics/etw/3832-routingservicetransmitsucceeded.md)|Informações|O serviço de roteamento transmitidos com êxito a mensagem com ID: ' %1 [operação %2] para '%3'.|RoutingServices|  
|[4001 - TransportListenerSessionsReceived](../../../../../docs/framework/wcf/diagnostics/etw/4001-transportlistenersessionsreceived.md)|Detalhado|Sessão de escuta de transporte recebido com por meio de '%1'|ActivationServices|  
|[4002 - FailFastException](../../../../../docs/framework/wcf/diagnostics/etw/4002-failfastexception.md)|Crítico|FailFastException.|ActivationServices|  
|[4003 - ServiceStartPipeError](../../../../../docs/framework/wcf/diagnostics/etw/4003-servicestartpipeerror.md)|Erro|Erro de pipe de início do serviço.|ActivationServices|  
|[4008 - DispatchSessionStart](../../../../../docs/framework/wcf/diagnostics/etw/4008-dispatchsessionstart.md)|Detalhado|Bylo zahájeno odesílání relace.|ActivationServices|  
|[4008 - DispatchSessionStart](../../../../../docs/framework/wcf/diagnostics/etw/4008-dispatchsessionstart.md)|Aviso|Expedição de sessão para '%1' falhou, pois pendentes sessão fila está cheia de '%2' itens pendentes.|ActivationServices|  
|[4011 - MessageQueueRegisterStart](../../../../../docs/framework/wcf/diagnostics/etw/4011-messagequeueregisterstart.md)|Detalhado|Fila de mensagens registrar início.|ActivationServices|  
|[4012 - MessageQueueRegisterAbort](../../../../../docs/framework/wcf/diagnostics/etw/4012-messagequeueregisterabort.md)|Erro|Anulado com status de registro de fila de mensagem: '%1' para o uri: '%2'.|ActivationServices|  
|[4013 - MessageQueueUnregisterSucceeded](../../../../../docs/framework/wcf/diagnostics/etw/4013-messagequeueunregistersucceeded.md)|Detalhado|Fila de mensagens cancelar o registro com êxito para o uri: '%1'.|ActivationServices|  
|[4014 - MessageQueueRegisterFailed](../../../../../docs/framework/wcf/diagnostics/etw/4014-messagequeueregisterfailed.md)|Erro|Registro de fila para o uri da mensagem: '%1' falhou com status: '%2'.|ActivationServices|  
|[4015 - MessageQueueRegisterCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4015-messagequeueregistercompleted.md)|Informações|Registro de fila de mensagem concluído para o uri '%1'.|ActivationServices|  
|[4016 - MessageQueueDuplicatedSocketError](../../../../../docs/framework/wcf/diagnostics/etw/4016-messagequeueduplicatedsocketerror.md)|Erro|Fila de mensagens Falha na duplicação do soquete.|ActivationServices|  
|[4019 - MessageQueueDuplicatedSocketComplete](../../../../../docs/framework/wcf/diagnostics/etw/4019-messagequeueduplicatedsocketcomplete.md)|Detalhado|MessageQueueDuplicatedSocketComplete|ActivationServices|  
|[4020 - TcpTransportListenerListeningStart](../../../../../docs/framework/wcf/diagnostics/etw/4020-tcptransportlistenerlisteningstart.md)|Detalhado|Começar a escutar o uri de escuta de transporte TCP: '%1'.|ActivationServices|  
|[4021 - TcpTransportListenerListeningStop](../../../../../docs/framework/wcf/diagnostics/etw/4021-tcptransportlistenerlisteningstop.md)|Detalhado|Escuta de transporte TCP escutando.|ActivationServices|  
|[4022 - WebhostUnregisterProtocolFailed](../../../../../docs/framework/wcf/diagnostics/etw/4022-webhostunregisterprotocolfailed.md)|Erro|Código de erro: % 1|ActivationServices|  
|[4023 - WasCloseAllListenerChannelInstancesCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4023-wasclosealllistenerchannelinstancescompleted.md)|Informações|Foi fechar todas as instâncias de canal de ouvinte concluídas.|ActivationServices|  
|[4024 - WasCloseAllListenerChannelInstancesFailed](../../../../../docs/framework/wcf/diagnostics/etw/4024-wasclosealllistenerchannelinstancesfailed.md)|Erro|Código de erro: % 1|ActivationServices|  
|[4025 - OpenListenerChannelInstanceFailed](../../../../../docs/framework/wcf/diagnostics/etw/4025-openlistenerchannelinstancefailed.md)|Erro|Código de erro: % 1|ActivationServices|  
|[4026 - WasConnected](../../../../../docs/framework/wcf/diagnostics/etw/4026-wasconnected.md)|Detalhado|FOI conectado.|ActivationServices|  
|[4027 - WasDisconnected](../../../../../docs/framework/wcf/diagnostics/etw/4027-wasdisconnected.md)|Detalhado|FOI desconectada.|ActivationServices|  
|[4028 - PipeTransportListenerListeningStart](../../../../../docs/framework/wcf/diagnostics/etw/4028-pipetransportlistenerlisteningstart.md)|Detalhado|Escuta de transporte de pipe escutando início na uri:% 1.|ActivationServices|  
|[4029 - PipeTransportListenerListeningStop](../../../../../docs/framework/wcf/diagnostics/etw/4029-pipetransportlistenerlisteningstop.md)|Detalhado|Parar escuta do ouvinte do transporte de pipe.|ActivationServices|  
|[4030 - DispatchSessionSuccess](../../../../../docs/framework/wcf/diagnostics/etw/4030-dispatchsessionsuccess.md)|Informações|Expedição de sessão foi bem-sucedida.|ActivationServices|  
|[4031 - DispatchSessionFailed](../../../../../docs/framework/wcf/diagnostics/etw/4031-dispatchsessionfailed.md)|Erro|Falha de expedição de sessão.|ActivationServices|  
|[4032 - WasConnectionTimedout](../../../../../docs/framework/wcf/diagnostics/etw/4032-wasconnectiontimedout.md)|Crítico|Conexão foi atingido.|ActivationServices|  
|[4033 - RoutingTableLookupStart](../../../../../docs/framework/wcf/diagnostics/etw/4033-routingtablelookupstart.md)|Detalhado|Pesquisa de tabela de roteamento começou.|ActivationServices|  
|[4034 - RoutingTableLookupStop](../../../../../docs/framework/wcf/diagnostics/etw/4034-routingtablelookupstop.md)|Detalhado|Pesquisa concluída da tabela de roteamento.|ActivationServices|  
|[4035 - PendingSessionQueueRatio](../../../../../docs/framework/wcf/diagnostics/etw/4035-pendingsessionqueueratio.md)|Detalhado|Pendente taxa da fila de sessão: %1 / %2|Quota|  
|[4600 - MessageLogEventSizeExceeded](../../../../../docs/framework/wcf/diagnostics/etw/4600-messagelogeventsizeexceeded.md)|Aviso|Mensagem não pôde fazer logon, pois ele excede o tamanho do evento ETW|WCFMessageLogging|  
|[4801 - DiscoveryClientInClientChannelFailedToClose](../../../../../docs/framework/wcf/diagnostics/etw/4801-discoveryclientinclientchannelfailedtoclose.md)|Aviso|O DiscoveryClient criado dentro de DiscoveryClientChannel Falha ao fechar e, portanto, foi anulado.|Descoberta|  
|[4802 - DiscoveryClientProtocolExceptionSuppressed](../../../../../docs/framework/wcf/diagnostics/etw/4802-discoveryclientprotocolexceptionsuppressed.md)|Informações|Um ProtocolException foi suprimido ao fechar o DiscoveryClient. Isso pode ocorrer porque um DiscoveryService ainda está tentando enviar resposta para o DiscoveryClient.|Descoberta|  
|[4803 - DiscoveryClientReceivedMulticastSuppression](../../../../../docs/framework/wcf/diagnostics/etw/4803-discoveryclientreceivedmulticastsuppression.md)|Informações|O DiscoveryClient recebeu uma mensagem de supressão multicast de um DiscoveryProxy.|Descoberta|  
|[4804 - DiscoveryMessageReceivedAfterOperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4804-discoverymessagereceivedafteroperationcompleted.md)|Informações|Uma mensagem %1 com messageId = '%2' foi descartado pelo DiscoveryClient porque a operação %3 correspondente foi concluída.|Descoberta|  
|[4805 - DiscoveryMessageWithInvalidContent](../../../../../docs/framework/wcf/diagnostics/etw/4805-discoverymessagewithinvalidcontent.md)|Aviso|Uma mensagem %1 com messageId = '%2' foi descartada porque ela tinha conteúdo inválido.|Descoberta|  
|[4806 - DiscoveryMessageWithInvalidRelatesToOrOperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4806-discoverymessagewithinvalidrelatestooroperationcompleted.md)|Aviso|Uma mensagem %1 com messageId = '%2' e relatesTo = '%3' foi descartado pelo DiscoveryClient porque a operação %4 correspondente foi concluída ou o valor de relatesTo é inválido.|Descoberta|  
|[4807 - DiscoveryMessageWithInvalidReplyTo](../../../../../docs/framework/wcf/diagnostics/etw/4807-discoverymessagewithinvalidreplyto.md)|Aviso|Uma mensagem de solicitação de descoberta com messageId = '%1' foi ignorada porque ele tinha um endereço ReplyTo inválido.|Descoberta|  
|[4808 - DiscoveryMessageWithNoContent](../../../../../docs/framework/wcf/diagnostics/etw/4808-discoverymessagewithnocontent.md)|Aviso|Uma mensagem de %1 foi descartada porque ele não tem nenhum conteúdo.|Descoberta|  
|[4809 - DiscoveryMessageWithNullMessageId](../../../../../docs/framework/wcf/diagnostics/etw/4809-discoverymessagewithnullmessageid.md)|Aviso|Uma mensagem de %1 foi descartada porque o cabeçalho da mensagem não contém a propriedade MessageId necessária.|Descoberta|  
|[4810 - DiscoveryMessageWithNullMessageSequence](../../../../../docs/framework/wcf/diagnostics/etw/4810-discoverymessagewithnullmessagesequence.md)|Aviso|Uma mensagem %1 com messageId = '%2' foi descartado pelo DiscoveryClient porque ele não tem a propriedade DiscoveryMessageSequence.|Descoberta|  
|[4811 - DiscoveryMessageWithNullRelatesTo](../../../../../docs/framework/wcf/diagnostics/etw/4811-discoverymessagewithnullrelatesto.md)|Aviso|Uma mensagem %1 com messageId = '%2' foi descartado pelo DiscoveryClient porque o cabeçalho da mensagem não contém a propriedade RelatesTo necessária.|Descoberta|  
|[4812 - DiscoveryMessageWithNullReplyTo](../../../../../docs/framework/wcf/diagnostics/etw/4812-discoverymessagewithnullreplyto.md)|Aviso|Uma mensagem de solicitação de descoberta com messageId = '%1' foi descartada porque não tinha um endereço ReplyTo.|Descoberta|  
|[4813 - DuplicateDiscoveryMessage](../../../../../docs/framework/wcf/diagnostics/etw/4813-duplicatediscoverymessage.md)|Aviso|Uma mensagem %1 com messageId = '%2' foi descartada porque era uma duplicata.|Descoberta|  
|[4814 - EndpointDiscoverabilityDisabled](../../../../../docs/framework/wcf/diagnostics/etw/4814-endpointdiscoverabilitydisabled.md)|Informações|A capacidade de descoberta do ponto de extremidade com EndpointAddress = '%1' e ListenUri = '%2' foi desabilitado.|Descoberta|  
|[4814 - EndpointDiscoverabilityDisabled](../../../../../docs/framework/wcf/diagnostics/etw/4814-endpointdiscoverabilitydisabled.md)|Informações|A capacidade de descoberta do ponto de extremidade com EndpointAddress = '%1' e ListenUri = '%2' foi habilitado.|Descoberta|  
|[4816 - FindInitiatedInDiscoveryClientChannel](../../../../../docs/framework/wcf/diagnostics/etw/4816-findinitiatedindiscoveryclientchannel.md)|Detalhado|Uma operação de localização foi iniciada no DiscoveryClientChannel para descobrir os pontos de extremidade.|Descoberta|  
|[4817 - InnerChannelCreationFailed](../../../../../docs/framework/wcf/diagnostics/etw/4817-innerchannelcreationfailed.md)|Aviso|O DiscoveryClientChannel Falha ao criar o canal com um ponto de extremidade descoberto com EndpointAddress = '%1' e por meio de = '%2'. O DiscoveryClientChannel agora tentará usar o ponto de extremidade descoberto disponível Avançar.|Descoberta|  
|[4818 - InnerChannelOpenFailed](../../../../../docs/framework/wcf/diagnostics/etw/4818-innerchannelopenfailed.md)|Aviso|O DiscoveryClientChannel Falha ao abrir o canal com um ponto de extremidade descoberto com EndpointAddress = '%1' e por meio de = '%2'. O DiscoveryClientChannel agora tentará usar o ponto de extremidade descoberto disponível Avançar.|Descoberta|  
|[4819 - InnerChannelOpenSucceeded](../../../../../docs/framework/wcf/diagnostics/etw/4819-innerchannelopensucceeded.md)|Informações|O DiscoveryClientChannel descoberto um ponto de extremidade e abrir o canal de usá-lo com êxito. O cliente está conectado a um serviço usando o EndpointAddress = '%1' e por meio de = '%2'.|Descoberta|  
|[4820 - SynchronizationContextReset](../../../../../docs/framework/wcf/diagnostics/etw/4820-synchronizationcontextreset.md)|Informações|O SynchronizationContext foi redefinido para seu valor original de %1 por DiscoveryClientChannel.|Descoberta|  
|[4821 - SynchronizationContextSetToNull](../../../../../docs/framework/wcf/diagnostics/etw/4821-synchronizationcontextsettonull.md)|Informações|O SynchronizationContext foi definido como null por DiscoveryClientChannel antes de iniciar a operação de localização.|Descoberta|  
|[5001 - DCSerializeWithSurrogateStart](../../../../../docs/framework/wcf/diagnostics/etw/5001-dcserializewithsurrogatestart.md)|Detalhado|DataContract serializar %1 com o início de substitutos.|Serialização|  
|[5002 - DCSerializeWithSurrogateStop](../../../../../docs/framework/wcf/diagnostics/etw/5002-dcserializewithsurrogatestop.md)|Detalhado|Serializar DataContract com parada de substitutos.|Serialização|  
|[5003 - DCDeserializeWithSurrogateStart](../../../../../docs/framework/wcf/diagnostics/etw/5003-dcdeserializewithsurrogatestart.md)|Detalhado|DataContract desserializar %1 com o início de substitutos.|Serialização|  
|[5004 - DCDeserializeWithSurrogateStop](../../../../../docs/framework/wcf/diagnostics/etw/5004-dcdeserializewithsurrogatestop.md)|Detalhado|Desserializar DataContract com parada de substitutos.|Serialização|  
|[5005 - ImportKnownTypesStart](../../../../../docs/framework/wcf/diagnostics/etw/5005-importknowntypesstart.md)|Detalhado|Operace importknowntypes.|Serialização|  
|[5006 - ImportKnownTypesStop](../../../../../docs/framework/wcf/diagnostics/etw/5006-importknowntypesstop.md)|Detalhado|Parar ImportKnownTypes.|Serialização|  
|[5007 - DCResolverResolve](../../../../../docs/framework/wcf/diagnostics/etw/5007-dcresolverresolve.md)|Detalhado|Resolvedor DataContract Resolvendo %1 início.|Serialização|  
|[5008 - DCGenWriterStart](../../../../../docs/framework/wcf/diagnostics/etw/5008-dcgenwriterstart.md)|Detalhado|DataContract gerar %1 gravador para %2 início.|Serialização|  
|[5009 - DCGenWriterStop](../../../../../docs/framework/wcf/diagnostics/etw/5009-dcgenwriterstop.md)|Detalhado|DataContract gerar parar de gravador.|Serialização|  
|[5010 - DCGenReaderStart](../../../../../docs/framework/wcf/diagnostics/etw/5010-dcgenreaderstart.md)|Detalhado|DataContract gerar %1 leitor para o início de %2.|Serialização|  
|[5011 - DCGenReaderStop](../../../../../docs/framework/wcf/diagnostics/etw/5011-dcgenreaderstop.md)|Detalhado|Parar de geração do DataContract.|Serialização|  
|[5012 - DCJsonGenReaderStart](../../../../../docs/framework/wcf/diagnostics/etw/5012-dcjsongenreaderstart.md)|Detalhado|JSON gerar %1 leitor para o início de %2.|Serialização|  
|[5013 - DCJsonGenReaderStop](../../../../../docs/framework/wcf/diagnostics/etw/5013-dcjsongenreaderstop.md)|Detalhado|Parar de geração de leitor de JSON.|Serialização|  
|[5014 - DCJsonGenWriterStart](../../../../../docs/framework/wcf/diagnostics/etw/5014-dcjsongenwriterstart.md)|Detalhado|JSON gerar %1 gravador para %2 início.|Serialização|  
|[5015 - DCJsonGenWriterStop](../../../../../docs/framework/wcf/diagnostics/etw/5015-dcjsongenwriterstop.md)|Detalhado|JSON gerar parar de gravador.|Serialização|  
|[5016 - GenXmlSerializableStart](../../../../../docs/framework/wcf/diagnostics/etw/5016-genxmlserializablestart.md)|Detalhado|Gere Xml serializável para o início de '%1'.|Serialização|  
|[5017 - GenXmlSerializableStop](../../../../../docs/framework/wcf/diagnostics/etw/5017-genxmlserializablestop.md)|Detalhado|Gere Xml de parada serializável.|Serialização|  
|[5203 - JsonMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/5203-jsonmessagedecodingstart.md)|Detalhado|Kodér JsonMessageEncoder zahájil dekódování zprávy.|Canal|  
|[5204 - JsonMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/5204-jsonmessageencodingstart.md)|Detalhado|Kodér JsonMessageEncoder zahájil kódování zprávy.|Canal|  
|[5402 - TokenValidationStarted](../../../../../docs/framework/wcf/diagnostics/etw/5402-tokenvalidationstarted.md)|Detalhado|Validação de SecurityToken (o tipo '%1' e id '%2') iniciada.|Segurança|  
|[5403 - TokenValidationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5403-tokenvalidationsuccess.md)|Detalhado|Êxito na validação SecurityToken (o tipo '%1' e id '%2').|Segurança|  
|[5404 - TokenValidationFailure](../../../../../docs/framework/wcf/diagnostics/etw/5404-tokenvalidationfailure.md)|Erro|Falha na validação de SecurityToken (o tipo '%1' e id '%2'). %3|Segurança|  
|[5405 - GetIssuerNameSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5405-getissuernamesuccess.md)|Detalhado|Recuperação de emissor nome: % 1 de 2 de tokenId:% foi bem-sucedida.|Segurança|  
|[5406 - GetIssuerNameFailure](../../../../../docs/framework/wcf/diagnostics/etw/5406-getissuernamefailure.md)|Erro|Falha na recuperação do nome do emissor de tokenId:% 1.|Segurança|  
|[5600 - FederationMessageProcessingStarted](../../../../../docs/framework/wcf/diagnostics/etw/5600-federationmessageprocessingstarted.md)|Detalhado|Iniciado processamento da mensagem de Federação.|Segurança|  
|[5601 - FederationMessageProcessingSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5601-federationmessageprocessingsuccess.md)|Detalhado|Processamento de mensagens de Federação foi bem-sucedida.|Segurança|  
|[5602 - FederationMessageCreationStarted](../../../../../docs/framework/wcf/diagnostics/etw/5602-federationmessagecreationstarted.md)|Detalhado|Criando a mensagem de federação de postagem de formulário iniciado.|Segurança|  
|[5603 - FederationMessageCreationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5603-federationmessagecreationsuccess.md)|Detalhado|Êxito ao criar a mensagem de federação na postagem de formulário.|Segurança|  
|[5604 - SessionCookieReadingStarted](../../../../../docs/framework/wcf/diagnostics/etw/5604-sessioncookiereadingstarted.md)|Detalhado|Ler o token de sessão do cookie de sessão iniciada.|Segurança|  
|[5605 - SessionCookieReadingSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5605-sessioncookiereadingsuccess.md)|Detalhado|Token de sessão de leitura do cookie de sessão foi bem-sucedida.|Segurança|  
|[5606 - PrincipalSettingFromSessionTokenStarted](../../../../../docs/framework/wcf/diagnostics/etw/5606-principalsettingfromsessiontokenstarted.md)|Detalhado|Configuração de entidade do token de sessão é iniciada.|Segurança|  
|[5607 - PrincipalSettingFromSessionTokenSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5607-principalsettingfromsessiontokensuccess.md)|Detalhado|Configuração de entidade do token de sessão foi bem-sucedida.|Segurança|  
|[57393 - AppDomainUnload](../../../../../docs/framework/wcf/diagnostics/etw/57393-appdomainunload.md)|Informações|O descarregamento do AppDomain. AppDomain.FriendlyName %1, ProcessName %2, ProcessId %3.|Infraestrutura|  
|[57394 - HandledException](../../../../../docs/framework/wcf/diagnostics/etw/57394-handledexception.md)|Informações|Tratando uma exceção.|Infraestrutura|  
|[57395 - ShipAssertExceptionMessage](../../../../../docs/framework/wcf/diagnostics/etw/57395-shipassertexceptionmessage.md)|Erro|Ocorreu uma falha inesperada. Aplicativos não devem tentar tratar esse erro. Para fins de diagnóstico, essa mensagem em inglês está associada à falha: %1.|Infraestrutura|  
|[57396 - ThrowingException](../../../../../docs/framework/wcf/diagnostics/etw/57396-throwingexception.md)|Aviso|Gerar uma exceção. Fonte de %1.|Infraestrutura|  
|[57397 - UnhandledException](../../../../../docs/framework/wcf/diagnostics/etw/57397-unhandledexception.md)|Crítico|Exceção sem tratamento.|Infraestrutura|  
|[57399 - TraceCodeEventLogCritical](../../../../../docs/framework/wcf/diagnostics/etw/57399-tracecodeeventlogcritical.md)|Crítico|Zapsáno do EventLog.|Infraestrutura|  
|[57400 - TraceCodeEventLogError](../../../../../docs/framework/wcf/diagnostics/etw/57400-tracecodeeventlogerror.md)|Erro|Zapsáno do EventLog.|Infraestrutura|  
|[57401 - TraceCodeEventLogInfo](../../../../../docs/framework/wcf/diagnostics/etw/57401-tracecodeeventloginfo.md)|Informações|Zapsáno do EventLog.|Infraestrutura|  
|[57402 - TraceCodeEventLogVerbose](../../../../../docs/framework/wcf/diagnostics/etw/57402-tracecodeeventlogverbose.md)|Detalhado|Zapsáno do EventLog.|Infraestrutura|  
|[57403 - TraceCodeEventLogWarning](../../../../../docs/framework/wcf/diagnostics/etw/57403-tracecodeeventlogwarning.md)|Aviso|Zapsáno do EventLog.|Infraestrutura|  
|[57404 - HandledExceptionWarning](../../../../../docs/framework/wcf/diagnostics/etw/57404-handledexceptionwarning.md)|Aviso|Tratando uma exceção.|Infraestrutura|  
|[62326 - HttpHandlerPickedForUrl](../../../../../docs/framework/wcf/diagnostics/etw/62326-httphandlerpickedforurl.md)|Informações|O documento XAML de hosts de url '%1' com o elemento raiz de tipo '%2'. O tipo de manipulador HTTP '%3' é escolhido para atender a todas as solicitações feitas para essa url.|WebHost|
