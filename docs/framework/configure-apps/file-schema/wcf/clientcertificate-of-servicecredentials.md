---
title: <clientCertificate> de <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
ms.openlocfilehash: a8a78bbfcd9dfbf6975503a845d5bb4e2d24b13d
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398131"
---
# <a name="clientcertificate-of-servicecredentials"></a>\<clientCertificate > de \<ServiceCredentials >
Define um certificado X. 509 usado para assinar e criptografar mensagens para um cliente forma um serviço em um padrão de comunicação duplex.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> clientCertificate**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<clientCertificate>
  <certificate />
  <authentication />
</clientCertificate>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<authentication>](authentication-of-clientcertificate-element.md)|Especifica as opções de autenticação para o certificado do cliente.|  
|[\<certificate>](certificate-of-clientcertificate-element.md)|Especifica o certificado a ser usado.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|Especifica as credenciais a serem usadas na autenticação do serviço e as configurações relacionadas à validação de credenciais do cliente.|  
  
## <a name="remarks"></a>Comentários  
 Esse elemento é usado quando o serviço deve ter o certificado do cliente com antecedência para se comunicar com segurança com o cliente. Isso ocorre ao usar o padrão de comunicação duplex. No padrão de solicitação/resposta mais comum, o cliente inclui seu certificado na solicitação, que o serviço usa para criptografar e assinar sua resposta para o cliente. No padrão de comunicação duplex, no entanto, o serviço não tem uma solicitação do cliente e, portanto, precisa do certificado do cliente com antecedência para proteger a mensagem para o cliente. Portanto, você deve obter o certificado do cliente em uma negociação fora de banda e especificar o certificado usando esse elemento. Para obter mais informações sobre os serviços duplex [, consulte Como: Crie um contrato](../../../wcf/feature-details/how-to-create-a-duplex-contract.md)duplex.  
  
 O conjunto de certificados neste elemento é usado para criptografar mensagens para o cliente somente para associações que são configuradas com `MutualCertificateDuplex` o modo de autenticação de segurança de mensagem.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>
- [Como: Criar um contrato duplex](../../../wcf/feature-details/how-to-create-a-duplex-contract.md)
- [Comportamentos de segurança](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Trabalhando com certificados](../../../wcf/feature-details/working-with-certificates.md)
