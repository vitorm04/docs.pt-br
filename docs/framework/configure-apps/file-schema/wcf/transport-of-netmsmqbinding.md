---
title: '&lt;transporte&gt; de &lt;netMsmqBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: 1b0de5e1d581384d00c18dbefbf7b170325e2061
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43777318"
---
# <a name="lttransportgt-of-ltnetmsmqbindinggt"></a>&lt;transporte&gt; de &lt;netMsmqBinding&gt;
Define as configurações de segurança de transporte.  
  
 \<system.ServiceModel>  
\<associações >  
\<netMsmqBinding>  
\<associação >  
\<segurança >  
\<transporte >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<netMsmqBinding>  
    <binding>  
    <security>  
         <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
            msmqEncryptionAlgorithm="RC4Stream/AES"  
            msmqProtectionLevel="None/Sign/EncryptAndSign"  
            msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
    </security>  
   </binding>  
</netMsmqBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|msmqAuthenticationMode|Especifica como a mensagem deve ser autenticada pelo transporte MSMQ. Os valores válidos incluem o seguinte:<br /><br /> -None: Nenhuma autenticação.<br />-WindowsDomain: O mecanismo de autenticação usa o Active Directory para recuperar o certificado X.509 para o identificador de segurança associado à mensagem. Em seguida, isso é usado para verificar a ACL da fila para garantir que o usuário tem permissão de gravação para a fila.<br />-Certificado: O canal recupera o certificado do repositório de certificados.<br /><br /> O padrão é `WindowsDomain`.<br /><br /> Se esse atributo for definido como `None`, o `msmqProtectionLevel` atributo também deve ser definido como `None`. Esse atributo é do tipo<xref:System.ServiceModel.MsmqAuthenticationMode>|  
|msmqEncryptionAlgorithm|Especifica o algoritmo a ser usado para criptografia de mensagem no fio durante a transferência de mensagens entre os gerenciadores de fila de mensagem. Os valores válidos incluem o seguinte:<br /><br /> -RC4Stream<br />-AES<br />-O valor padrão é `RC4Stream`. Esse atributo é do tipo <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.|  
|msmqProtectionLevel|Especifica que as modo como as mensagens são protegidas no nível do transporte MSMQ. A criptografia assegura a mensagem de integridade, durante a entrada e criptografar garante a integridade da mensagem e não-repúdio. Ou seja, a mensagem foi realmente enviado do remetente e o remetente é quem diz que ser. Os valores válidos incluem o seguinte:<br /><br /> -None: Nenhuma proteção.<br />-Sinal: As mensagens são assinadas.<br />-EncryptAndSign: As mensagens são criptografadas e assinadas.<br />-O padrão é `Sign`.|  
|msmqSecureHashAlgorithm|Especifica o algoritmo de hash a ser usado para calcular o resumo da mensagem. Os valores válidos incluem o seguinte:<br /><br /> -   MD5<br />-SHA1<br />-   SHA256<br />-   SHA512<br /><br /> O padrão é `SHA1`. Esse atributo é do tipo <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|Define as configurações de segurança de transporte para transportes na fila.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>  
 <xref:System.ServiceModel.MsmqTransportSecurity>  
 [Filas no WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Usando associações para configurar clientes e serviços do Windows Communication Foundation](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<associação >](../../../../../docs/framework/misc/binding.md)
