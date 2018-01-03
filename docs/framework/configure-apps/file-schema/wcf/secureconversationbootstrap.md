---
title: '&lt;secureConversationBootstrap&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 66b46f95-fa2d-4b5b-b6ce-0572ab0cdd50
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 5cff19fc6d931f5dd391776c39f3934c8809a5ad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecureconversationbootstrapgt"></a>&lt;secureConversationBootstrap&gt;
Especifica os valores padrão usados para iniciar um serviço de conversa segura.  
  
 \<System. ServiceModel >  
\<associações >  
\<customBinding >  
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
|`allowSerializedSigningTokenOnReply`|Opcional. Um valor booleano que especifica se um token serializado pode ser usado na resposta. O valor padrão é `false`. Ao usar uma associação dupla, a configuração padrão é `true` qualquer configuração feita será ignorada.|  
|`authenticationMode`|Especifica o modo de autenticação SOAP usado entre o iniciador e respondente.<br /><br /> O padrão é sspiNegotiated.<br /><br /> Esse atributo é do tipo <xref:System.ServiceModel.Configuration.AuthenticationMode>.|  
|`defaultAlgorithmSuite`|Conjunto de algoritmos de segurança define uma variedade de algoritmos como canonização, Digest, KeyWrap, assinatura, criptografia e keyderivation. Cada um dos pacotes de algoritmo de segurança define valores para esses parâmetros diferentes. Segurança baseada em mensagem é obtida usando esses algoritmos.<br /><br /> Este atributo é usado quando se trabalha com uma plataforma diferente que aceita um conjunto de algoritmos diferentes do padrão. Você deve conhecer as vantagens e desvantagens dos algoritmos relevantes ao fazer modificações para essa configuração. Esse atributo é do tipo <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>. O padrão é `Basic256`.|  
|`includeTimestamp`|Um valor booleano que especifica se os carimbos de hora são incluídos em cada mensagem. O padrão é `true`.|  
|`keyEntropyMode`|Especifica a maneira que as chaves para mensagens de segurança são computadas. Chaves podem ser baseadas no material de chave do cliente, apenas o material de chave de serviço ou uma combinação de ambos. Os valores válidos são:<br /><br /> -ClientEntropy: A chave de sessão baseada o cliente fornecido o material de chave.<br />-ServerEntropy: A chave de sessão baseia-se desativar o serviço fornecido material de chave.<br />-CombinedEntropy: A chave de sessão é baseado em cliente e o serviço fornecido material de chave.<br /><br /> O padrão é CombinedEntropy.<br /><br /> Esse atributo é do tipo <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.|  
|`messageProtectionOrder`|Define a ordem na qual mensagem algoritmos de nível de segurança são aplicados à mensagem. Os valores válidos incluem o seguinte:<br /><br /> -SignBeforeEncrypt: Entrar pela primeira vez e, em seguida, criptografar.<br />-SignBeforeEncryptAndEncryptSignature: Assinar, criptografar e criptografar a assinatura.<br />-EncryptBeforeSign: Primeiro criptografar e assinar.<br /><br /> SignBeforeEncryptAndEncryptSignature é o valor padrão com certificados mútuos 1.1 do WS-Security.  SignBeforeEncrypt é o valor padrão com o WS-Security 1.0.<br /><br /> Esse atributo é do tipo <xref:System.ServiceModel.Security.MessageProtectionOrder>.|  
|`messageSecurityVersion`|Define a versão do WS-Security é usada. Os valores válidos incluem o seguinte:<br /><br /> -WSSecurityJan2004<br />-WSSecurityXXX2005<br /><br /> O padrão é WSSecurityXXX2005. Esse atributo é do tipo <xref:System.ServiceModel.MessageSecurityVersion>.|  
|`requireDerivedKeys`|Um valor booleano que especifica se as chaves podem ser derivadas das chaves de prova originais. O padrão é `true`.|  
|`requireSecurityContextCancellation`|Um valor booleano que especifica se o contexto de segurança deve ser cancelado e encerrado quando não é mais necessário. O padrão é `true`.|  
|`requireSignatureConfirmation`|Um valor booleano que especifica se a confirmação de assinatura de WS-Security está habilitada. Quando definido como `true`, assinaturas de mensagem são confirmadas pelo respondente. O padrão é `false`.<br /><br /> Confirmação de assinatura é usada para confirmar que o serviço está respondendo no reconhecimento completo de uma solicitação.|  
|`securityHeaderLayout`|Especifica a ordenação dos elementos no cabeçalho de segurança. Os valores válidos são:<br /><br /> -Estrito. Itens são adicionados ao cabeçalho de segurança de acordo com o princípio geral de "declarar antes do uso".<br />-Incerta. Itens são adicionados ao cabeçalho de segurança em qualquer ordem que confirmam WSS: segurança de mensagem SOAP.<br />-LaxWithTimestampFirst. Itens são adicionados ao cabeçalho de segurança em qualquer ordem que confirmam WSS: segurança de mensagem SOAP exceto que o primeiro elemento no cabeçalho de segurança deve ser um elemento wsse:Timestamp.<br />-LaxWithTimestampLast. Itens são adicionados ao cabeçalho de segurança em qualquer ordem que confirmam WSS: segurança de mensagem SOAP exceto que o último elemento no cabeçalho de segurança deve ser um elemento wsse:Timestamp.<br /><br /> O padrão é estrito.<br /><br /> Esse elemento é do tipo <xref:System.ServiceModel.Channels.SecurityHeaderLayout>.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<issuedTokenParameters >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|Especifica um token emitido atual. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>.|  
|[\<localClientSettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)|Especifica as configurações de segurança de um cliente local para esta associação. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>.|  
|[\<localServiceSettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md)|Especifica as configurações de segurança de um serviço local para esta associação. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<segurança >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|Especifica as opções de segurança para uma associação personalizada.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Como criar uma associação personalizada utilizando o SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Segurança de associação personalizada](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
