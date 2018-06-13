---
title: AppDomainInfo
ms.date: 03/30/2017
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
ms.openlocfilehash: 7189448a930298837089cf3ac2743cb7e073ae02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486975"
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
