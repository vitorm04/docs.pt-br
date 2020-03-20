---
title: <msmqTransportSecurity>
ms.date: 03/30/2017
ms.assetid: 092e911b-ab1b-4069-a26e-6134c3299e06
ms.openlocfilehash: 5899c609b3cf52c4a275ba6fb10c5826fcf37f1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153003"
---
# <a name="msmqtransportsecurity"></a>\<msmqTransportSecurity>
Especifica as configurações de segurança de transporte MSMQ para uma vinculação personalizada.  
  
[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModelo>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<vinculações>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de vinculação personalizada**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<vinculação>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegração>**](msmqintegration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<msmqTransportSecurity>**  
  
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
|`msmqAuthenticationMode`|Especifica como a mensagem deve ser autenticada pelo transporte MSMQ. Se isso for `None`definido como `msmqProtectionLevel` , o valor `None`do atributo também deve ser definido como .<br /><br /> Os valores válidos incluem os seguintes:<br /><br /> - Nenhuma: nenhuma autenticação.<br />- Windows: O mecanismo de autenticação usa o Active Directory para obter o certificado X.509 para o SID associado à mensagem. Isso é então usado para verificar a ACL da fila para garantir que o usuário tenha permissão para escrever na fila.<br />- Certificado: O canal recebe o certificado na loja de certificados.<br /><br /> O valor padrão é o Windows. Este atributo <xref:System.ServiceModel.MsmqAuthenticationMode>é do tipo .|  
|`msmqEncryptionAlgorithm`|Especifica o algoritmo a ser usado para criptografia de mensagens no fio ao transferir mensagens entre gerentes de fila de mensagens. Os valores válidos incluem os seguintes:<br /><br /> - RC4Stream<br />- AES<br /><br /> O valor padrão é RC4Stream. Este atributo <xref:System.ServiceModel.MsmqEncryptionAlgorithm>é do tipo .|  
|`msmqProtectionLevel`|Especifica como a mensagem é protegida no nível do transporte MSMQ. A criptografia garante a integridade da mensagem, enquanto o EncryptAndSign garante a integridade da mensagem e o não-repúdio; ou seja, a mensagem realmente vem do remetente e o remetente é quem eles dizem que são. Os valores válidos incluem os seguintes:<br /><br /> - Nenhuma: sem proteção.<br />- Sinal: As mensagens são assinadas.<br />- EncryptAndSign: As mensagens são criptografadas e assinadas.<br /><br /> O valor padrão é Sign. Este atributo <xref:System.Net.Security.ProtectionLevel>é do tipo .|  
|`msmqSecureHashAlgorithm`|Especifica o algoritmo a ser usado na computação da digestão como parte das assinaturas. Os valores válidos incluem os seguintes:<br /><br /> - MD5<br />- SHA1<br />- SHA256<br />- SHA512<br /><br /> O valor padrão é SHA1. Este atributo <xref:System.ServiceModel.MsmqSecureHashAlgorithm>é do tipo .<br>Devido a problemas de colisão com MD5 e SHA1, a Microsoft recomenda SHA256 ou melhor.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<msmqIntegração>](msmqintegration.md)|Especifica as configurações necessárias para interação com um remetente ou receptor de mensagens (MSMQ).|  
|[\<>msmqTransporte](msmqtransport.md)|Especifica as propriedades de comunicação de fila para um serviço WCF (Windows Communication Foundation) que usa o protocolo MSMQ nativo.|  
  
## <a name="remarks"></a>Comentários  
 Para obter mais informações sobre segurança nos transportes, consulte [Segurança de Transporte](../../../wcf/feature-details/transport-security.md).  
  
## <a name="see-also"></a>Confira também

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Filas no WCF](../../../wcf/feature-details/queues-in-wcf.md)
- [Transportes](../../../wcf/feature-details/transports.md)
- [Selecionando um transporte](../../../wcf/feature-details/choosing-a-transport.md)
- [Ligações](../../../wcf/bindings.md)
- [Estendendo associações](../../../wcf/extending/extending-bindings.md)
- [Associações personalizadas](../../../wcf/extending/custom-bindings.md)
- [\<>de vinculação personalizada](custombinding.md)
- [Segurança de transporte](../../../wcf/feature-details/transport-security.md)
