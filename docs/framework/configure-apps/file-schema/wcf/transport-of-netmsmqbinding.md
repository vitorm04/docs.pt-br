---
title: <transport> de <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: cc47c01cccc931e81ba57ab37ad9e3accfaa693b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152925"
---
# <a name="transport-of-netmsmqbinding"></a>\<> de \<transporte de> netMsmqBinding
Define as configurações de segurança de transporte.  
  
[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModelo>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<vinculações>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<vinculação>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de segurança**](security-of-netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>de transporte**  
  
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
|Msmqauthenticationmode|Especifica como a mensagem deve ser autenticada pelo transporte MSMQ. Os valores válidos incluem os seguintes:<br /><br /> - Nenhuma: nenhuma autenticação.<br />- WindowsDomain: O mecanismo de autenticação usa o Active Directory para recuperar o certificado X.509 para o identificador de segurança associado à mensagem. Isso é então usado para verificar a ACL da fila para garantir que o usuário tenha permissão de gravação para a fila.<br />- Certificado: O canal recupera o certificado da loja de certificados.<br /><br /> O padrão é `WindowsDomain`.<br /><br /> Se este atributo `None`estiver `msmqProtectionLevel` definido como , `None`o atributo também deve ser definido como . Esse atributo é do tipo<xref:System.ServiceModel.MsmqAuthenticationMode>|  
|msmqEncryptionAlgorithm|Especifica o algoritmo a ser usado para criptografia de mensagens no fio ao transferir mensagens entre gerentes de fila de mensagens. Os valores válidos incluem os seguintes:<br /><br /> - RC4Stream<br />- AES<br />- O valor `RC4Stream`padrão é . Este atributo <xref:System.ServiceModel.MsmqEncryptionAlgorithm>é do tipo .|  
|Msmqprotectionlevel|Especifica a forma como as mensagens são protegidas no nível do transporte MSMQ. A criptografia garante a integridade da mensagem, enquanto assinar e criptografar garante a integridade da mensagem e o não-repúdio. Ou seja, a mensagem realmente veio do remetente e o remetente é quem eles dizem que são. Os valores válidos incluem os seguintes:<br /><br /> - Nenhuma: sem proteção.<br />- Sinal: As mensagens são assinadas.<br />- EncryptAndSign: As mensagens são criptografadas e assinadas.<br />- O `Sign`padrão é.|  
|msmqSecureHashAlgorithm|Especifica o algoritmo hash a ser usado para calcular o digerir a mensagem. Os valores válidos incluem os seguintes:<br /><br /> - MD5<br />- SHA1<br />- SHA256<br />- SHA512<br /><br /> O padrão é `SHA1`. Este atributo <xref:System.ServiceModel.MsmqSecureHashAlgorithm>é do tipo .<br>Devido a problemas de colisão com MD5 e SHA1, a Microsoft recomenda SHA256 ou melhor.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<>de segurança](security-of-netmsmqbinding.md)|Define as configurações de segurança de transporte para transportes enfileirados.|  
  
## <a name="see-also"></a>Confira também

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [Filas no WCF](../../../wcf/feature-details/queues-in-wcf.md)
- [Protegendo serviços e clientes](../../../wcf/feature-details/securing-services-and-clients.md)
- [Ligações](../../../wcf/bindings.md)
- [Configurando associações fornecidas pelo sistema](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Usando associações para configurar serviços e clientes](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<vinculação>](bindings.md)
