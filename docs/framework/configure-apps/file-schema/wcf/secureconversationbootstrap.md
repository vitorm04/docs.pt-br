---
title: <secureConversationBootstrap>
ms.date: 03/30/2017
ms.assetid: 66b46f95-fa2d-4b5b-b6ce-0572ab0cdd50
ms.openlocfilehash: b3187cb51b6fd32797c9ad401c704d5f16c6f7e8
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399922"
---
# <a name="secureconversationbootstrap"></a>\<secureConversationBootstrap>
Especifica os valores padrão usados para iniciar um serviço de conversa segura.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de CustomBinding**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de segurança**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> secureConversationBootstrap**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<secureConversationBootstrap allowSerializedSigningTokenOnReply="Boolean"
                             authenticationMode="AuthenticationMode"
                             defaultAlgorithmSuite="SecurityAlgorithmSuite"
                             includeTimestamp="Boolean"
                             requireDerivedKeys="Boolean"
                             keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
                             messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"
                             messageSecurityVersion="WSSecurityJan2004/WSSecurityXXX2005"
                             requireDerivedKeys="Boolean"
                             requireSecurityContextCancellation="Boolean"
                             requireSignatureConfirmation="Boolean"
                             securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"
                             includeTimestamp="Boolean" />
```  
  
## <a name="type"></a>Tipo  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`allowSerializedSigningTokenOnReply`|Opcional. Um valor booliano que especifica se um token serializado pode ser usado na resposta. O valor padrão é `false`. Ao usar uma associação dupla, a configuração assume como `true` padrão qualquer configuração feita será ignorada.|  
|`authenticationMode`|Especifica o modo de autenticação SOAP usado entre o iniciador e o respondente.<br /><br /> O padrão é sspiNegotiated.<br /><br /> Esse atributo é do tipo <xref:System.ServiceModel.Configuration.AuthenticationMode>.|  
|`defaultAlgorithmSuite`|O conjunto de algoritmos de segurança define uma variedade de algoritmos, como canonização, resumo, keywrap, assinatura, criptografia e algoritmos de keyderivações. Cada um dos conjuntos de algoritmos de segurança define valores para esses parâmetros diferentes. A segurança baseada em mensagem é obtida usando esses algoritmos.<br /><br /> Esse atributo é usado ao trabalhar com uma plataforma diferente que opta por um conjunto de algoritmos diferente do padrão. Você deve estar ciente dos pontos fortes e fracos dos algoritmos relevantes ao fazer modificações nessa configuração. Esse atributo é do tipo <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>. O padrão é `Basic256`.|  
|`includeTimestamp`|Um valor booliano que especifica se os carimbos de data/hora são incluídos em cada mensagem. O padrão é `true`.|  
|`keyEntropyMode`|Especifica a maneira como as chaves para proteger mensagens são computadas. As chaves podem ser baseadas somente no material da chave do cliente, somente no material da chave de serviço ou em uma combinação de ambos. Os valores válidos são:<br /><br /> - ClientEntropy: A chave de sessão baseia-se no material de chave fornecido pelo cliente.<br />- ServerEntropy: A chave de sessão baseia-se no material de chave fornecido pelo serviço.<br />- CombinedEntropy: A chave de sessão baseia-se no cliente e no serviço fornecido pelo material de chave.<br /><br /> O padrão é CombinedEntropy.<br /><br /> Esse atributo é do tipo <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.|  
|`messageProtectionOrder`|Define a ordem na qual os algoritmos de segurança de nível de mensagem são aplicados à mensagem. Os valores válidos incluem o seguinte:<br /><br /> - SignBeforeEncrypt: Assine primeiro e, em seguida, criptografar.<br />-   SignBeforeEncryptAndEncryptSignature: Assinar, criptografar e criptografar assinatura.<br />-   EncryptBeforeSign: Criptografar primeiro e depois assinar.<br /><br /> SignBeforeEncryptAndEncryptSignature é o valor padrão ao usar certificados mútuos com o WS-Security 1,1.  SignBeforeEncrypt é o valor padrão com WS-Security 1,0.<br /><br /> Esse atributo é do tipo <xref:System.ServiceModel.Security.MessageProtectionOrder>.|  
|`messageSecurityVersion`|Define a versão do WS-Security que é usada. Os valores válidos incluem o seguinte:<br /><br /> -   WSSecurityJan2004<br />- WSSecurityXXX2005<br /><br /> O padrão é WSSecurityXXX2005. Esse atributo é do tipo <xref:System.ServiceModel.MessageSecurityVersion>.|  
|`requireDerivedKeys`|Um valor booliano que especifica se as chaves podem ser derivadas das chaves de prova originais. O padrão é `true`.|  
|`requireSecurityContextCancellation`|Um valor booliano que especifica se o contexto de segurança deve ser cancelado e encerrado quando não for mais necessário. O padrão é `true`.|  
|`requireSignatureConfirmation`|Um valor booliano que especifica se a confirmação de assinatura do WS-Security está habilitada. Quando definido como `true`, as assinaturas de mensagens são confirmadas pelo respondente. O padrão é `false`.<br /><br /> A confirmação de assinatura é usada para confirmar que o serviço está respondendo no reconhecimento total de uma solicitação.|  
|`securityHeaderLayout`|Especifica a ordenação dos elementos no cabeçalho de segurança. Os valores válidos são:<br /><br /> Strict. Itens são adicionados ao cabeçalho de segurança de acordo com o princípio geral de "declarar antes do uso".<br />Incerto. Os itens são adicionados ao cabeçalho de segurança em qualquer ordem que confirme para o WSS: Segurança da Mensagem SOAP.<br />- LaxWithTimestampFirst. Os itens são adicionados ao cabeçalho de segurança em qualquer ordem que confirme para o WSS: Segurança da Mensagem de SOAP, exceto pelo fato de que o primeiro elemento no cabeçalho de segurança precisa ser um elemento wsse:Timestamp.<br />- LaxWithTimestampLast. Os itens são adicionados ao cabeçalho de segurança em qualquer ordem que confirme para o WSS: Segurança da Mensagem de SOAP, exceto pelo fato de que o último elemento no cabeçalho de segurança precisa ser um elemento wsse:Timestamp.<br /><br /> O padrão é estrito.<br /><br /> Esse elemento é do tipo <xref:System.ServiceModel.Channels.SecurityHeaderLayout>.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|Especifica um token emitido atual. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>.|  
|[\<localClientSettings>](localclientsettings-element.md)|Especifica as configurações de segurança de um cliente local para esta associação. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>.|  
|[\<localServiceSettings>](localservicesettings-element.md)|Especifica as configurações de segurança de um serviço local para esta associação. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<security>](security-of-custombinding.md)|Especifica as opções de segurança para uma associação personalizada.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Associações](../../../wcf/bindings.md)
- [Estendendo associações](../../../wcf/extending/extending-bindings.md)
- [Associações personalizadas](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [Como: Criar uma associação personalizada usando o SecurityBindingElement](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Segurança de associação personalizada](../../../wcf/samples/custom-binding-security.md)
