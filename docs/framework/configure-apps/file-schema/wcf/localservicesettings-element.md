---
title: elemento &lt;localServiceSettings&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0658549c-3f65-46dd-8c5c-9895441ed734
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1e251c226484788b7ebc059cd68caf1f3c150c62
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltlocalservicesettingsgt-element"></a>elemento &lt;localServiceSettings&gt;
Especifica as configurações de segurança de um serviço local para esta associação.  
  
 \<System. ServiceModel >  
\<associações >  
\<customBinding >  
\<associação >  
\<segurança >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<security>  
   <localServiceSettings detectReplays="Boolean"  
      inactivityTimeout="TimeSpan"  
      issuedCookieLifeTime="TimeSpan"  
      maxCachedCookies="Integer"   
      maxClockSkew="TimeSpan"   
      maxPendingSessions="Integer"  
      maxStatefulNegotiations="Integer"  
      negotiationTimeout="TimeSpan"  
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
|`detectReplays`|Um valor booleano que especifica se os ataques por repetição contra o canal são detectados e lidados automaticamente. O padrão é `false`.|  
|`inactivityTimeout`|Um positivo <xref:System.TimeSpan> que especifica a duração da inatividade o canal espera antes de expirar. O padrão é "01: 00:00".|  
|`issuedCookieLifeTime`|Um <xref:System.TimeSpan> que especifica o tempo de vida concedido a todos os novos cookies de segurança. Os cookies que excederem sua vida útil são reciclados e precisam ser negociados novamente. O valor padrão é "10: 00:00".|  
|`maxCachedCookies`|Um inteiro positivo que especifica o número máximo de cookies que podem ser armazenados em cache. O padrão é 1000.|  
|`maxClockSkew`|Um <xref:System.TimeSpan> que especifica a diferença máxima de tempo entre os relógios do sistema das duas partes da comunicação. O valor padrão é "00: 05:00".<br /><br /> Quando esse valor é definido como o padrão, o receptor aceita mensagens com carimbos de hora de envio para cima para 5 minutos mais tarde ou antes da hora em que a mensagem foi recebida. As mensagens que não passarem no teste de tempo de envio são rejeitadas. Essa configuração é usada em conjunto com o `replayWindow` atributo.|  
|`maxPendingSessions`|Um inteiro positivo que especifica o número máximo de pendente sessões de segurança que o serviço oferece suporte. Quando esse limite for atingido, todos os clientes novos recebem falhas de SOAP. O valor padrão é 1000.|  
|`maxStatefulNegotiations`|Um inteiro positivo que especifica o número de negociações de segurança que podem estar ativas simultaneamente. Sessões de negociação ultrapassem o limite serão enfileiradas e só podem ser concluídas quando um espaço abaixo do limite torna-se disponível. O valor padrão é 1024.|  
|`negotiationTimeout`|Um <xref:System.TimeSpan> que especifica o tempo de vida da política de segurança usado por canal. Quando o tempo expirar, o canal nova negociação será iniciada com o cliente para uma nova política de segurança. O valor padrão é "00: 02:00".|  
|`reconnectTransportOnFailure`|Um valor booleano que especifica se as conexões usando mensagens WS-Reliable tentarão reconectar após falhas de transporte. O padrão é `true`, que significa a tentativa de infinita tenta se reconectar. O ciclo é interrompido pelo tempo limite de inatividade, que faz com que o canal lançar uma exceção quando ele não pode ser reconectado.|  
|`replayCacheSize`|Um inteiro positivo que especifica o número de momentos em cache usados para detecção de repetição. Se esse limite for excedido, o valor de uso único mais antigo é removido e um novo valor de uso único é criado para a nova mensagem. O valor padrão é 500000.|  
|`replayWindow`|Um <xref:System.TimeSpan> que especifica a duração em que momentos de mensagens individuais são válidos.<br /><br /> Após a duração, uma mensagem enviada com o mesmo nonce como aquela enviada antes não serão aceitas. Este atributo é usado em conjunto com o `maxClockSkew` atributo para impedir ataques de repetição. Um invasor pode repetir uma mensagem depois de sua janela de reprodução tiver expirado. Esta mensagem, no entanto, falhará a `maxClockSkew` teste que rejeita mensagens com carimbos de hora de envio até uma hora especificada posterior ou anterior à hora que a mensagem foi recebida.|  
|`sessionKeyRenewalInterval`|Um <xref:System.TimeSpan> que especifica a duração após a qual o iniciador renovará a chave da sessão de segurança. O padrão é "10: 00:00".|  
|`sessionKeyRolloverInterval`|Um <xref:System.TimeSpan> que especifica o intervalo de tempo, uma chave de sessão anterior é válido nas mensagens de entrada durante uma renovação de chave. O padrão é "00: 05:00".<br /><br /> Durante a renovação de chave, o cliente e o servidor sempre devem enviar mensagens usando a chave disponível mais recente. Ambas as partes aceitará as mensagens de entrada protegidas com a chave de sessão anterior até que o tempo de sobreposição expire.|  
|`timestampValidityDuration`|Um positivo <xref:System.TimeSpan> que especifica a duração na qual um carimbo de data / hora é válido. O padrão é "00: 15:00".|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<segurança >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|Especifica as opções de segurança para uma associação personalizada.|  
|[\<secureConversationBootstrap >](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|Especifica os valores padrão usados para iniciar um serviço de conversa segura.|  
  
## <a name="remarks"></a>Comentários  
 As configurações são locais porque eles não são publicados como parte da política de segurança do serviço e não afetam a associação do cliente.  
  
 Os seguintes atributos do `localServiceSecuritySettings` elemento pode ajudar a reduzir o ataque de segurança uma negação de serviço (DOS):  
  
-   `maxCachedCookies`: controla o número máximo de SecurityContextTokens limitada de tempo que são armazenados em cache pelo servidor depois de fazer negociação SPNEGO ou SSL.  
  
-   `issuedCookieLifetime`: controla o tempo de vida do SecurityContextTokens emitidos pelo servidor após a negociação SPNEGO ou SSL. O servidor armazena em cache o SecurityContextTokens para esse período de tempo.  
  
-   `maxPendingSessions`: controla o número máximo de conversas seguras que são estabelecidas no servidor, mas para que nenhum aplicativo de mensagens foram processado. Essa cota impede que os clientes estabelecendo conversas seguras no serviço, causando o serviço manter o estado para cada cliente, mas nunca usá-los.  
  
-   `inactivityTimeout`: controla o tempo máximo que o serviço mantém uma conversa segura ativo sem nunca receber uma mensagem de aplicativo. Essa cota impede que os clientes estabelecendo conversas seguras no serviço, causando o serviço manter o estado para cada cliente, mas nunca usá-los.  
  
 Em uma sessão de conversa segura, observe que tanto `inactivityTimeout` e `receiveTimeout` atributos na associação de afetam o tempo limite da sessão. O menor dos dois determina quando o tempo limite seja excedido.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalServiceSettings%2A>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)  
 [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Como: criar uma associação personalizada utilizando o SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Segurança de associação personalizada](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
