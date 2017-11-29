---
title: '&lt;transporte&gt; de &lt;msmqIntegrationBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d9def7fbd0082cc7fa9d9f18388604383cb71f9b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="lttransportgt-of-ltmsmqintegrationbindinggt"></a>&lt;transporte&gt; de &lt;msmqIntegrationBinding&gt;
Define as configurações de segurança para o transporte de integração de enfileiramento de mensagens.  
  
 \<sistema. ServiceModel >  
\<associações >  
msmqIntegrationBinding  
\<associação >  
\<segurança >  
\<transporte >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<security>  
    <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
        msmqEncryptionAlgorithm="RC4Stream/AES"  
        msmqProtectionLevel="None/Sign/EncryptAndSign"  
        msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem os elementos pai de atributos e elementos filho  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|Especifica como a mensagem deve ser autenticada pelo transporte MSMQ. Se isso for definido como `None`, o valor de `msmqProtectionLevel` atributo também deve ser definido como `None`.<br /><br /> Os valores válidos incluem o seguinte:<br /><br /> -Nenhum: Nenhuma autenticação.<br />-WindowsDomain: O mecanismo de autenticação usa o Active Directory para obter o certificado x. 509 para o SID associado à mensagem. Isso é usado para verificar a ACL da fila para garantir que o usuário tem permissão para gravar na fila.<br />-O certificado: O canal obtém o certificado do repositório de certificados.<br /><br /> O valor padrão é WindowsDomain. Esse atributo é do tipo <xref:System.ServiceModel.MsmqAuthenticationMode>.|  
|`msmqEncryptionAlgorithm`|Especifica o algoritmo a ser usado para criptografia de mensagem no fio durante a transferência de mensagens entre os gerenciadores de fila de mensagem. Os valores válidos incluem o seguinte:<br /><br /> -RC4Stream<br />-AES<br /><br /> O valor padrão é RC4Stream. Esse atributo é do tipo <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.|  
|`msmqProtectionLevel`|Especifica como a mensagem é protegida no nível de transporte MSMQ. A criptografia assegura a integridade da mensagem enquanto EncryptAndSign garante a integridade da mensagem e não-repúdio; ou seja, a mensagem é realmente do remetente e o remetente é quem diz que ser.<br /><br /> -Valores válidos incluem o seguinte:<br />-Nenhum: Sem proteção.<br />-Sign: Mensagens são assinadas.<br />-EncryptAndSign: Mensagens são criptografadas e assinadas.<br /><br /> O valor padrão é o sinal. Esse atributo é do tipo ProtectionLevel.|  
|`msmqSecureHashAlgorithm`|-Especifica o algoritmo a ser usado no cálculo do resumo como parte das assinaturas. Os valores válidos incluem o seguinte:<br />-MD5<br />-SHA1<br />-SHA256<br />-SHA512<br /><br /> O valor padrão é SHA1. Esse atributo é do tipo <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<segurança >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|Define as configurações de segurança para uma associação de MSMQ.|  
  
## <a name="remarks"></a>Comentários  
 Esse elemento encapsula as configurações de segurança para o transporte de integração de enfileiramento de mensagens. As configurações são as mesmas para a integração de enfileiramento de mensagens e de transportes na fila. Ele permite que você defina o modo de autenticação, o algoritmo de criptografia, algoritmo de Hash seguro e nível de proteção.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.MsmqTransportSecurity>  
 [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)  
 [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Usando associações para configurar clientes e serviços do Windows Communication Foundation](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<associação >](../../../../../docs/framework/misc/binding.md)
