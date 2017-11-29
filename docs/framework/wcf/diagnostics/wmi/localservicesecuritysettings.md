---
title: LocalServiceSecuritySettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 490aa0e5-5242-4f8d-b505-5ec6287633b4
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 74eff3a6193e6507c1049accf4c43c3ecc8d30a6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="localservicesecuritysettings"></a>LocalServiceSecuritySettings
LocalServiceSecuritySettings  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class LocalServiceSecuritySettings  
{  
  boolean DetectReplays;  
  datetime InactivityTimeout;  
  datetime IssuedCookieLifetime;  
  sint32 MaxCachedCookies;  
  datetime MaxClockSkew;  
  sint32 MaxPendingSessions;  
  sint32 MaxStatefulNegotiations;  
  datetime NegotiationTimeout;  
  boolean ReconnectTransportOnFailure;  
  sint32 ReplayCacheSize;  
  datetime ReplayWindow;  
  datetime SessionKeyRenewalInterval;  
  datetime SessionKeyRolloverInterval;  
  datetime TimestampValidityDuration;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe LocalServiceSecuritySettings não define nenhum método.  
  
## <a name="properties"></a>Propriedades  
 A classe LocalServiceSecuritySettings tem as seguintes propriedades:  
  
### <a name="detectreplays"></a>DetectReplays  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Um valor booleano que especifica se os ataques por repetição contra o canal são detectados e lidados automaticamente.  
  
### <a name="inactivitytimeout"></a>InactivityTimeout  
 Tipo de dados: datetime  
  
 Tipo de acesso: somente leitura  
  
 O número máximo de pendente sessões de segurança que o serviço oferece suporte.  
  
### <a name="issuedcookielifetime"></a>IssuedCookieLifetime  
 Tipo de dados: datetime  
  
 Tipo de acesso: somente leitura  
  
 Um TimeSpan que especifica o tempo de vida concedido a todos os novos cookies de segurança.  
  
### <a name="maxcachedcookies"></a>MaxCachedCookies  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 O número máximo de cookies que podem ser armazenados em cache.  
  
### <a name="maxclockskew"></a>MaxClockSkew  
 Tipo de dados: datetime  
  
 Tipo de acesso: somente leitura  
  
 Um TimeSpan que especifica a diferença máxima de tempo entre os relógios do sistema das duas partes da comunicação.  
  
### <a name="maxpendingsessions"></a>MaxPendingSessions  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 O número máximo de conexões pendentes no serviço.  
  
### <a name="maxstatefulnegotiations"></a>MaxStatefulNegotiations  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 O número de negociações de segurança que podem estar ativas simultaneamente.  
  
### <a name="negotiationtimeout"></a>NegotiationTimeout  
 Tipo de dados: datetime  
  
 Tipo de acesso: somente leitura  
  
 Um TimeSpan que especifica a duração máxima para a fase de negociação de segurança entre cliente e servidor.  
  
### <a name="reconnecttransportonfailure"></a>ReconnectTransportOnFailure  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Um valor booleano que especifica se as conexões usando mensagens WS-Reliable tentam se reconectar após falhas de transporte.  
  
### <a name="replaycachesize"></a>ReplayCacheSize  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 O número de momentos em cache usados para detecção de repetição.  
  
### <a name="replaywindow"></a>ReplayWindow  
 Tipo de dados: datetime  
  
 Tipo de acesso: somente leitura  
  
 Um TimeSpan que especifica a duração em que momentos de mensagens individuais são válidos.  
  
### <a name="sessionkeyrenewalinterval"></a>SessionKeyRenewalInterval  
 Tipo de dados: datetime  
  
 Tipo de acesso: somente leitura  
  
 Um TimeSpan que especifica a duração após a qual o iniciador renova a chave da sessão de segurança.  
  
### <a name="sessionkeyrolloverinterval"></a>SessionKeyRolloverInterval  
 Tipo de dados: datetime  
  
 Tipo de acesso: somente leitura  
  
 Um TimeSpan que especifica o intervalo de tempo uma chave de sessão anterior é válida nas mensagens de entrada durante uma renovação de chave.  
  
### <a name="timestampvalidityduration"></a>TimestampValidityDuration  
 Tipo de dados: datetime  
  
 Tipo de acesso: somente leitura  
  
 Um TimeSpan que especifica a duração na qual um carimbo de data / hora é válido.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido em root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
