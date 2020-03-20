---
title: <transport> de <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
ms.openlocfilehash: 1cb165fed9266307335482166116c4c1d62efe7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152951"
---
# <a name="transport-of-msmqintegrationbinding"></a>\<> de \<transporte de msmqIntegração>
Define as configurações de segurança para o transporte de integração de fila de mensagens.  
  
[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModelo>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<vinculações>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegraçãovinculando>**](msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<vinculação>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de segurança**](security-of-msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>de transporte**  
  
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
 As seções a seguir descrevem atributos, elementos da criança e elementos dos pais  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|Especifica como a mensagem deve ser autenticada pelo transporte MSMQ. Se isso for `None`definido como `msmqProtectionLevel` , o valor `None`do atributo também deve ser definido como .<br /><br /> Os valores válidos incluem os seguintes:<br /><br /> - Nenhuma: nenhuma autenticação.<br />- WindowsDomain: O mecanismo de autenticação usa o Active Directory para obter o certificado X.509 para o SID associado à mensagem. Isso é então usado para verificar a ACL da fila para garantir que o usuário tenha permissão para escrever na fila.<br />- Certificado: O canal recebe o certificado na loja de certificados.<br /><br /> O valor padrão é WindowsDomain. Este atributo <xref:System.ServiceModel.MsmqAuthenticationMode>é do tipo .|  
|`msmqEncryptionAlgorithm`|Especifica o algoritmo a ser usado para criptografia de mensagens no fio ao transferir mensagens entre gerentes de fila de mensagens. Os valores válidos incluem os seguintes:<br /><br /> - RC4Stream<br />- AES<br /><br /> O valor padrão é RC4Stream. Este atributo <xref:System.ServiceModel.MsmqEncryptionAlgorithm>é do tipo .|  
|`msmqProtectionLevel`|Especifica como a mensagem é protegida no nível do transporte MSMQ. A criptografia garante a integridade da mensagem, enquanto o EncryptAndSign garante a integridade da mensagem e o não-repúdio; ou seja, a mensagem realmente vem do remetente e o remetente é quem eles dizem que são.<br /><br /> - Os valores válidos incluem:<br />- Nenhuma: sem proteção.<br />- Sinal: As mensagens são assinadas.<br />- EncryptAndSign: As mensagens são criptografadas e assinadas.<br /><br /> O valor padrão é Sign. Este atributo é do tipo ProtectionLevel.|  
|`msmqSecureHashAlgorithm`|- Especifica o algoritmo a ser usado na computação da digestão como parte das assinaturas. Os valores válidos incluem os seguintes:<br />- MD5<br />- SHA1<br />- SHA256<br />- SHA512<br /><br /> O valor padrão é SHA1. Este atributo <xref:System.ServiceModel.MsmqSecureHashAlgorithm>é do tipo .<br>Devido a problemas de colisão com MD5 e SHA1, a Microsoft recomenda SHA256 ou melhor.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<>de segurança](security-of-basichttpbinding.md)|Define as configurações de segurança de uma vinculação MSMQ.|  
  
## <a name="remarks"></a>Comentários  
 Esse elemento encapsula as configurações de segurança para o transporte de integração de filade mensagens. As configurações são as mesmas para a integração de filas de mensagens e transportes enfileirados. Ele permite definir o modo de autenticação, algoritmo de criptografia, algoritmo hash seguro e nível de proteção.  
  
## <a name="see-also"></a>Confira também

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [Protegendo serviços e clientes](../../../wcf/feature-details/securing-services-and-clients.md)
- [Ligações](../../../wcf/bindings.md)
- [Configurando associações fornecidas pelo sistema](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Usando associações para configurar serviços e clientes](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<vinculação>](bindings.md)
