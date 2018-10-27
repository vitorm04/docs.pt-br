---
title: '&lt;secureConversationBootstrap&gt;'
ms.date: 03/30/2017
ms.assetid: 66b46f95-fa2d-4b5b-b6ce-0572ab0cdd50
ms.openlocfilehash: a1b739ac8af87340a693d88bac0a379f0c3a447a
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50046053"
---
# <a name="ltsecureconversationbootstrapgt"></a>&lt;secureConversationBootstrap&gt;
Especifica os valores padrão usados para iniciar um serviço de conversa segura.  
  
 \<system.serviceModel>  
\<associações >  
\<customBinding>  
\<associação >  
\<segurança >  
\<secureConversationBootstrap >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<secureConversationBootstrap  
   allowSerializedSigningTokenOnReply="Boolean"  
   authenticationMode="AuthenticationMode"  
   defaultAlgorithmSuite="SecurityAlgorithmSuite"  
   includeTimestamp="Boolean"  
   requireDerivedKeys="Boolean"  
   keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"   
messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"  
   messageSecurityVersion="WSSecurityJan2004/WSSecurityXXX2005"  
   requireDerivedKeys="Boolean"  
   requireSecurityContextCancellation="Boolean"  
   requireSignatureConfirmation="Boolean" >  
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
|`allowSerializedSigningTokenOnReply`|Opcional. Um valor booliano que especifica se um token serializado pode ser usado na resposta. O valor padrão é `false`. Ao usar uma associação de dupla, a configuração padrão é `true` qualquer configuração feita será ignorada.|  
|`authenticationMode`|Especifica o modo de autenticação SOAP usado entre o iniciador e o respondente.<br /><br /> O padrão é sspiNegotiated.<br /><br /> Esse atributo é do tipo <xref:System.ServiceModel.Configuration.AuthenticationMode>.|  
|`defaultAlgorithmSuite`|Pacote de algoritmos de segurança define uma variedade de algoritmos como canonização, Digest, KeyWrap, assinatura, criptografia e keyderivation. Cada um dos pacotes de algoritmo de segurança define os valores para esses parâmetros diferentes. Segurança baseada em mensagens é obtida usando esses algoritmos.<br /><br /> Este atributo é usado ao trabalhar com uma plataforma diferente que aceita para um conjunto de algoritmos diferentes do padrão. Você deve estar atento os pontos fortes e fracos dos algoritmos relevantes ao fazer modificações a essa configuração. Esse atributo é do tipo <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>. O padrão é `Basic256`.|  
|`includeTimestamp`|Um valor booliano que especifica se os carimbos de data / hora é incluídos em cada mensagem. O padrão é `true`.|  
|`keyEntropyMode`|Especifica a maneira que as chaves para proteger as mensagens são computadas. As chaves podem se basear o material de chave de cliente somente, somente o material de chave de serviço ou uma combinação de ambos. Os valores válidos são:<br /><br /> -ClientEntropy: A chave de sessão é baseada fora do cliente que forneceu o material da chave.<br />-ServerEntropy: A chave de sessão baseia-se desativar o serviço fornecido o material da chave.<br />-CombinedEntropy: A chave de sessão é baseada fora do cliente e o material para chave do serviço fornecido.<br /><br /> O padrão é CombinedEntropy.<br /><br /> Esse atributo é do tipo <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.|  
|`messageProtectionOrder`|Define a ordem na qual mensagem algoritmos de segurança em nível são aplicados à mensagem. Os valores válidos incluem o seguinte:<br /><br /> -SignBeforeEncrypt: Entrar pela primeira vez e, em seguida, criptografar.<br />-SignBeforeEncryptAndEncryptSignature: Assinar, criptografar e criptografar a assinatura.<br />-EncryptBeforeSign: Criptografar primeiro e, em seguida, entrar.<br /><br /> SignBeforeEncryptAndEncryptSignature é o valor padrão ao usar certificados mútuos com WS-Security 1.1.  SignBeforeEncrypt é o valor padrão com o WS-Security 1.0.<br /><br /> Esse atributo é do tipo <xref:System.ServiceModel.Security.MessageProtectionOrder>.|  
|`messageSecurityVersion`|Define a versão do WS-Security, o que é usado. Os valores válidos incluem o seguinte:<br /><br /> -WSSecurityJan2004<br />-WSSecurityXXX2005<br /><br /> O padrão é WSSecurityXXX2005. Esse atributo é do tipo <xref:System.ServiceModel.MessageSecurityVersion>.|  
|`requireDerivedKeys`|Um valor booliano que especifica se chaves podem ser derivadas das chaves de prova originais. O padrão é `true`.|  
|`requireSecurityContextCancellation`|Um valor booliano que especifica se contexto de segurança deve ser cancelado e encerrado quando não for mais necessário. O padrão é `true`.|  
|`requireSignatureConfirmation`|Um valor booliano que especifica se a confirmação de assinatura de WS-Security está habilitada. Quando definido como `true`, as assinaturas de mensagem são confirmadas pelo respondente. O padrão é `false`.<br /><br /> Confirmação de assinatura é usada para confirmar que o serviço está respondendo no reconhecimento total de uma solicitação.|  
|`securityHeaderLayout`|Especifica a ordenação dos elementos no cabeçalho de segurança. Os valores válidos são:<br /><br /> -Estrita. Itens são adicionados ao cabeçalho de segurança de acordo com o princípio geral de "declarar antes do uso".<br />-Incerta. Itens são adicionados ao cabeçalho de segurança em qualquer ordem que confirme para WSS: segurança de mensagem SOAP.<br />-LaxWithTimestampFirst. Itens são adicionados ao cabeçalho de segurança em qualquer ordem que confirme para WSS: segurança de mensagem SOAP, exceto pelo fato de que o primeiro elemento no cabeçalho de segurança deve ser um elemento wsse:Timestamp.<br />-LaxWithTimestampLast. Itens são adicionados ao cabeçalho de segurança em qualquer ordem que confirme para WSS: segurança de mensagem SOAP, exceto pelo fato de que o último elemento no cabeçalho de segurança deve ser um elemento wsse:Timestamp.<br /><br /> O padrão é estrito.<br /><br /> Esse elemento é do tipo <xref:System.ServiceModel.Channels.SecurityHeaderLayout>.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|Especifica um token emitido atual. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>.|  
|[\<localClientSettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)|Especifica as configurações de segurança de um cliente local para esta associação. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>.|  
|[\<localServiceSettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md)|Especifica as configurações de segurança de um serviço local para esta associação. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|Especifica as opções de segurança para uma associação personalizada.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Como criar uma associação personalizada utilizando o SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Segurança de associação personalizada](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
