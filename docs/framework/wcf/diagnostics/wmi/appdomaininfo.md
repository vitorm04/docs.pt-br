---
title: AppDomainInfo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 76fee9673514287dd120a215fc843e4d995e68c0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="appdomaininfo"></a>AppDomainInfo
Informações de domínio de aplicativo  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class AppDomainInfo  
{  
  sint32 AppDomainId;  
  boolean IsDefault;  
  boolean LogMalformedMessages;  
  boolean LogMessagesAtServiceLevel;  
  boolean LogMessagesAtTransportLevel;  
  TraceListener MessageLoggingTraceListeners[];  
  string Name;  
  string PerformanceCounters;  
  sint32 ProcessId;  
  string ServiceConfigPath;  
  string TraceLevel;  
  TraceListener wmiTraceListeners[];  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe AppDomainInfo não define nenhum método.  
  
## <a name="properties"></a>Propriedades  
 A classe AppDomainInfo tem as seguintes propriedades:  
  
### <a name="appdomainid"></a>AppDomainId  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 A identificação do appdomain.  
  
### <a name="isdefault"></a>IsDefault  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Indica se o appdomain é o appdomain padrão.  
  
### <a name="logmalformedmessages"></a>LogMalformedMessages  
 Tipo de dados: boolean  
  
 Tipo de acesso: leitura/gravação  
  
 Um valor que especifica se as mensagens malformadas são registradas.  
  
### <a name="logmessagesatservicelevel"></a>LogMessagesAtServiceLevel  
 Tipo de dados: boolean  
  
 Tipo de acesso: leitura/gravação  
  
 Um valor que especifica se as mensagens são rastreadas no nível de serviço (antes da criptografia e transformações relacionadas de transporte).  
  
### <a name="logmessagesattransportlevel"></a>Logmessagesattransportlevel como  
 Tipo de dados: boolean  
  
 Tipo de acesso: leitura/gravação  
  
 Um valor que especifica se as mensagens são rastreadas no nível do transporte.  
  
### <a name="messageloggingtracelisteners"></a>MessageLoggingTraceListeners  
 Tipo de dados: matriz TraceListener  
  
 Tipo de acesso: somente leitura  
  
 Os ouvintes de rastreamento de coleção que ouvem a origem de rastreamento de System.Wmi.MessageLogging.  
  
### <a name="name"></a>Nome  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O nome do appdomain.  
  
### <a name="performancecounters"></a>performanceCounters  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O escopo dos contadores de desempenho ativos no appdomain.  
  
### <a name="processid"></a>ProcessId  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 O processo de identificação.  
  
### <a name="serviceconfigpath"></a>ServiceConfigPath  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O caminho para a configuração do serviço.  
  
### <a name="tracelevel"></a>TraceLevel  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: leitura/gravação  
  
 O nível de rastreamento da origem de rastreamento de System.  
  
### <a name="servicemodeltracelisteners"></a>ServiceModelTraceListeners  
 Tipo de dados: matriz TraceListener  
  
 Tipo de acesso: somente leitura  
  
 Uma coleção de ouvintes da origem de rastreamento de System. ServiceModel.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido em root\ServiceModel|
