---
title: AppDomainInfo
ms.date: 03/30/2017
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
ms.openlocfilehash: 0b7f8aadbd9a9dfcdd33fc65be3a5a41ea95f5be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61964249"
---
# <a name="appdomaininfo"></a>AppDomainInfo
Informações de domínio de aplicativo  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp
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
 A classe AppDomainInfo não define quaisquer métodos.  
  
## <a name="properties"></a>Propriedades  
 A classe AppDomainInfo tem as seguintes propriedades:  
  
### <a name="appdomainid"></a>AppDomainId  
 Tipo de dados: sint32  
  
 Tipo de acesso: Somente leitura  
  
 A Id do appdomain.  
  
### <a name="isdefault"></a>IsDefault  
 Tipo de dados: boolean  
  
 Tipo de acesso: Somente leitura  
  
 Indica se o appdomain é o appdomain padrão.  
  
### <a name="logmalformedmessages"></a>LogMalformedMessages  
 Tipo de dados: boolean  
  
 Tipo de acesso: Leitura/gravação  
  
 Um valor que especifica se mensagens malformadas são registradas.  
  
### <a name="logmessagesatservicelevel"></a>LogMessagesAtServiceLevel  
 Tipo de dados: boolean  
  
 Tipo de acesso: Leitura/gravação  
  
 Um valor que especifica se as mensagens são rastreadas no nível de serviço (antes da criptografia e transformações de transporte).  
  
### <a name="logmessagesattransportlevel"></a>LogMessagesAtTransportLevel  
 Tipo de dados: boolean  
  
 Tipo de acesso: Leitura/gravação  
  
 Um valor que especifica se as mensagens são rastreadas no nível do transporte.  
  
### <a name="messageloggingtracelisteners"></a>MessageLoggingTraceListeners  
 Tipo de dados: Matriz de TraceListener  
  
 Tipo de acesso: Somente leitura  
  
 Os ouvintes de rastreamento da coleção que escutam à origem de rastreamento System.Wmi.MessageLogging.  
  
### <a name="name"></a>Nome  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 O nome do appdomain.  
  
### <a name="performancecounters"></a>PerformanceCounters  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 O escopo dos contadores de desempenho do Active Directory no appdomain.  
  
### <a name="processid"></a>ProcessId  
 Tipo de dados: sint32  
  
 Tipo de acesso: Somente leitura  
  
 O processo de identificação.  
  
### <a name="serviceconfigpath"></a>ServiceConfigPath  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 O caminho para a configuração do serviço.  
  
### <a name="tracelevel"></a>TraceLevel  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Leitura/gravação  
  
 O nível de rastreamento da origem de rastreamento de System.  
  
### <a name="servicemodeltracelisteners"></a>ServiceModelTraceListeners  
 Tipo de dados: Matriz de TraceListener  
  
 Tipo de acesso: Somente leitura  
  
 Uma coleção de ouvintes da origem de rastreamento de System. ServiceModel.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido no root\ServiceModel|
