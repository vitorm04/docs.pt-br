---
title: '&lt;localClientSettings&gt; element'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4680ace5-f4e1-4fcb-b9d8-a4a4af5cd7ae
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cabde7eb9dd122c2f7060b2f2e2c16f5949dc1f3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltlocalclientsettingsgt-element"></a>&lt;localClientSettings&gt; element
Especifica as configurações de segurança de um cliente local para esta associação.  
  
 \<System. ServiceModel >  
\<associações >  
\<customBinding >  
\<associação >  
\<segurança >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<security>  
   <localClientSettings cacheCookies="Boolean"  
      cookieRenewalThresholdPercentage="Integer"  
      detectReplays="Boolean"  
      maxClockSkew="TimeSpan"  
      maxCookieCachingTime="TimeSpan"  
      reconnectTransportOnFailure="Boolean"  
      replayCacheSize="Integer"  
      replayWindow="TimeSpan"  
      sessionKeyRenewalInterval="TimeSpan"  
      sessionKeyRolloverInterval="TimeSpan"  
      timestampValidityDuration="TimeSpan" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`cacheCookies`|Um valor booleano que especifica se o cache de cookie está habilitado. O padrão é `false`.|  
|`cookieRenewalThresholdPercentage`|Um inteiro que especifica o percentual máximo de cookies que podem ser renovados. Esse valor deve estar entre 0 e 100, inclusive. O padrão é 90.|  
|`detectReplays`|Um valor booleano que especifica se os ataques por repetição contra o canal são detectados e lidados automaticamente. O padrão é `false`.|  
|`maxClockSkew`|Um <xref:System.TimeSpan> que especifica a diferença máxima de tempo entre os relógios do sistema das duas partes da comunicação. O valor padrão é "00: 05:00".<br /><br /> Quando esse valor é definido como o padrão, o receptor aceita mensagens com carimbos de hora de envio para cima para 5 minutos mais tarde ou antes da hora em que a mensagem foi recebida. As mensagens que não passarem no teste de tempo de envio são rejeitadas. Essa configuração é usada em conjunto com o `replayWindow` atributo.|  
|`maxCookieCachingTime`|Um <xref:System.TimeSpan> que especifica o tempo de vida máximo de cookies. O valor padrão é "10675199.02:48:05.4775807".|  
|`reconnectTransportOnFailure`|Um valor booleano que especifica se as conexões usando mensagens WS-Reliable tentarão reconectar após falhas de transporte. O padrão é `true`, que significa a tentativa de infinita tenta se reconectar. O ciclo é interrompido pelo tempo limite de inatividade, que faz com que o canal lançar uma exceção quando ele não pode ser reconectado.|  
|`replayCacheSize`|Um inteiro positivo que especifica o número de momentos em cache usados para detecção de repetição. Se esse limite for excedido, o valor de uso único mais antigo é removido e um novo valor de uso único é criado para a nova mensagem. O valor padrão é 500000.|  
|`replayWindow`|Um <xref:System.TimeSpan> que especifica a duração em que momentos de mensagens individuais são válidos.<br /><br /> Após a duração, uma mensagem enviada com o mesmo nonce como aquela enviada antes não serão aceitas. Este atributo é usado em conjunto com o `maxClockSkew` atributo para impedir ataques de repetição. Um invasor pode repetir uma mensagem depois de sua janela de reprodução tiver expirado. Esta mensagem, no entanto, falhará a `maxClockSkew` teste que rejeita mensagens com carimbos de hora de envio até uma hora especificada posterior ou anterior à hora que a mensagem foi recebida.|  
|`sessionKeyRenewalInterval`|Um <xref:System.TimeSpan> que especifica a duração após a qual o iniciador renovará a chave da sessão de segurança. O padrão é "10: 00:00".|  
|`sessionKeyRolloverInterval`|Um <xref:System.TimeSpan> que especifica o intervalo de tempo, uma chave de sessão anterior é válido nas mensagens de entrada durante uma renovação de chave. O padrão é "00: 05:00".<br /><br /> Durante a renovação de chave, o cliente e o servidor sempre devem enviar mensagens usando a chave disponível mais recente. Ambas as partes aceitará as mensagens de entrada protegidas com a chave de sessão anterior até que o tempo de sobreposição expire.|  
|`timestampValidityDuration`|Um positivo <xref:System.TimeSpan> que especifica a duração na qual um carimbo de data / hora é válido. O padrão é "00: 15:00".|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<segurança >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|Especifica as opções de segurança para uma associação personalizada.|  
|[\<secureConversationBootstrap >](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|Especifica os valores padrão usados para iniciar um serviço de conversa segura.|  
  
## <a name="remarks"></a>Comentários  
 As configurações são locais no sentido de que eles não são derivadas da política de segurança do serviço de configurações.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalClientSettings%2A>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A>  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)  
 [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Como: criar uma associação personalizada utilizando o SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Segurança de associação personalizada](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
