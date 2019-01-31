---
title: <msmqTransportSecurity>
ms.date: 03/30/2017
ms.assetid: 092e911b-ab1b-4069-a26e-6134c3299e06
ms.openlocfilehash: eb7ff953fcb61232fad16a99ac80cb98dbd83186
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55259963"
---
# <a name="msmqtransportsecurity"></a>\<msmqTransportSecurity>
Especifica as configurações de segurança do transporte MSMQ para uma associação personalizada.  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<binding>  
\<msmqIntegration>  
\<msmqTransportSecurity>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<msmqTransportSecurity msmqAuthenticationMode="None/Windows/Certificate"
                       msmqEncryptionAlgorithm="RC4Stream/AES"
                       msmqProtectionLevel="None/Sign/EncryptAndSign"
                       msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</msmqTransportSecurity>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|Especifica como a mensagem deve ser autenticada pelo transporte MSMQ. Se isso for definido como `None`, o valor da `msmqProtectionLevel` atributo também deve ser definido como `None`.<br /><br /> Os valores válidos incluem o seguinte:<br /><br /> -None: Nenhuma autenticação.<br />-   Windows: O mecanismo de autenticação usa o Active Directory para obter o certificado X.509 para o SID associado à mensagem. Em seguida, isso é usado para verificar a ACL da fila para garantir que o usuário tem permissão para gravar na fila.<br />-Certificado: O canal obtém o certificado do repositório de certificados.<br /><br /> O valor padrão é Windows. Esse atributo é do tipo <xref:System.ServiceModel.MsmqAuthenticationMode>.|  
|`msmqEncryptionAlgorithm`|Especifica o algoritmo a ser usado para criptografia de mensagem no fio durante a transferência de mensagens entre os gerenciadores de fila de mensagem. Os valores válidos incluem o seguinte:<br /><br /> -   RC4Stream<br />-AES<br /><br /> O valor padrão é RC4Stream. Esse atributo é do tipo <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.|  
|`msmqProtectionLevel`|Especifica como a mensagem é protegida no nível do transporte MSMQ. Criptografia assegura a integridade da mensagem enquanto EncryptAndSign garante a integridade da mensagem e não-repúdio; ou seja, a mensagem é proveniente, de fato, o remetente e o remetente é quem diz que ser. Os valores válidos incluem o seguinte:<br /><br /> -None: Sem proteção.<br />-Sinal: As mensagens são assinadas.<br />-   EncryptAndSign: As mensagens são criptografadas e assinadas.<br /><br /> O valor padrão é o sinal. Esse atributo é do tipo <xref:System.Net.Security.ProtectionLevel>.|  
|`msmqSecureHashAlgorithm`|Especifica o algoritmo a ser usado no cálculo do resumo como parte das assinaturas. Os valores válidos incluem o seguinte:<br /><br /> -   MD5<br />-   SHA1<br />-   SHA256<br />-   SHA512<br /><br /> O valor padrão é SHA1. Esse atributo é do tipo <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<msmqIntegration>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegration.md)|Especifica as configurações necessárias para interação com um remetente de enfileiramento de mensagens (MSMQ) ou o receptor.|  
|[\<msmqTransport>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqtransport.md)|Especifica as propriedades de comunicação de enfileiramento de mensagens para um serviço do Windows Communication Foundation (WCF) que usa o protocolo MSMQ nativo.|  
  
## <a name="remarks"></a>Comentários  
 Para obter mais informações sobre a segurança de transporte, consulte [segurança de transporte](../../../../../docs/framework/wcf/feature-details/transport-security.md).  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Filas no WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [Transportes](../../../../../docs/framework/wcf/feature-details/transports.md)
- [Escolhendo um transporte](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [Associações](../../../../../docs/framework/wcf/bindings.md)
- [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [Segurança de transporte](../../../../../docs/framework/wcf/feature-details/transport-security.md)
