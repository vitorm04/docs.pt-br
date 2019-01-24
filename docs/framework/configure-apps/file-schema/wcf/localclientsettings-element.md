---
title: '&lt;localClientSettings&gt; element'
ms.date: 03/30/2017
ms.assetid: 4680ace5-f4e1-4fcb-b9d8-a4a4af5cd7ae
ms.openlocfilehash: 67e872ea44a502c5b0fcdc5c1d326aad91eaa8fa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600356"
---
# <a name="ltlocalclientsettingsgt-element"></a>&lt;localClientSettings&gt; element
Especifica as configurações de segurança de um cliente local para esta associação.  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<binding>  
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
|`cacheCookies`|Um valor booliano que especifica se o cache de cookie está habilitado. O padrão é `false`.|  
|`cookieRenewalThresholdPercentage`|Um inteiro que especifica a porcentagem máxima de cookies que podem ser renovados. Esse valor deve estar entre 0 e 100, inclusive. O padrão é 90.|  
|`detectReplays`|Um valor booliano que especifica se os ataques de reprodução contra o canal são detectados e tratados automaticamente. O padrão é `false`.|  
|`maxClockSkew`|Um <xref:System.TimeSpan> que especifica a diferença máxima de tempo entre os relógios do sistema das duas partes da comunicação. O valor padrão é "00: 05:00".<br /><br /> Quando esse valor é definido como o padrão, o receptor aceita mensagens com carimbos de data / hora de envio de hora para cima para 5 minutos mais tarde ou antes de hora em que a mensagem foi recebida. As mensagens que não passa no teste de tempo de envio são rejeitadas. Essa configuração é usada em conjunto com o `replayWindow` atributo.|  
|`maxCookieCachingTime`|Um <xref:System.TimeSpan> que especifica o tempo de vida máximo de cookies. O valor padrão é "10675199.02:48:05.4775807".|  
|`reconnectTransportOnFailure`|Um valor booliano que especifica se as conexões que usam mensagens WS-Reliable tentam se reconectar após falhas de transporte. O padrão é `true`, que significa que a tentativa de infinita tenta se reconectar. O ciclo é interrompido pelo tempo de limite de inatividade, o que faz com que o canal para lançar uma exceção quando ele não pode ser reconectado.|  
|`replayCacheSize`|Um inteiro positivo que especifica o número de nonces armazenados em cache usados para detecção de reprodução. Se esse limite for excedido, o nonce mais antigo é removido e um nonce novo é criado para a nova mensagem. O valor padrão é 500000.|  
|`replayWindow`|Um <xref:System.TimeSpan> que especifica a duração na qual nonces de mensagens individuais são válidos.<br /><br /> Após esta duração, uma mensagem enviada com o mesmo nonce como aquela enviada antes não serão aceitas. Esse atributo é usado em conjunto com o `maxClockSkew` atributo para evitar ataques de repetição. Um invasor pode reproduzir uma mensagem depois que sua janela de reprodução tiver expirado. Essa mensagem, no entanto, falharia a `maxClockSkew` teste que rejeita mensagens com carimbos de hora de envio até uma hora especificada posterior ou anterior à hora de que a mensagem foi recebida.|  
|`sessionKeyRenewalInterval`|Um <xref:System.TimeSpan> que especifica a duração após a qual o iniciador renovará a chave da sessão de segurança. O padrão é "10: 00:00".|  
|`sessionKeyRolloverInterval`|Um <xref:System.TimeSpan> que especifica o intervalo de tempo, uma chave de sessão anterior é válido nas mensagens de entrada durante uma renovação de chave. O padrão é "00:05:00".<br /><br /> Durante a renovação de chave, o cliente e o servidor sempre devem enviar mensagens usando a chave disponível mais atual. Ambas as partes aceitará mensagens de entrada protegidas com a chave de sessão anterior até que a hora da substituição expire.|  
|`timestampValidityDuration`|Um positivo <xref:System.TimeSpan> que especifica a duração em que um carimbo de data / hora é válido. O padrão é "00: 15:00".|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|Especifica as opções de segurança para uma associação personalizada.|  
|[\<secureConversationBootstrap>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|Especifica os valores padrão usados para iniciar um serviço de conversa segura.|  
  
## <a name="remarks"></a>Comentários  
 As configurações são locais no sentido de que eles não são derivadas da política de segurança do serviço de configurações.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Associações](../../../../../docs/framework/wcf/bindings.md)
- [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [Como: Criar uma associação personalizada utilizando o SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Segurança de associação personalizada](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
