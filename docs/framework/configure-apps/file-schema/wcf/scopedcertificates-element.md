---
title: <scopedCertificates> Elemento
ms.date: 03/30/2017
ms.assetid: c7b6fc35-d4b2-4c18-98bd-83e09591f1d3
ms.openlocfilehash: 73e78a6ca27ed45e1eadc7121987b75f79bc6aa5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59145194"
---
# <a name="scopedcertificates-element"></a>\<scopedCertificates > elemento
Representa uma coleção de certificados X.509 fornecidos por serviços específicos (escopo) para autenticação. Essa coleção é normalmente usada para especificar os certificados de serviço para serviços de Token de segurança em um cenário federado.  
  
 \<system.ServiceModel>  
\<comportamentos >  
seção endpointBehaviors  
\<behavior>  
\<clientCredentials>  
\<serviceCertificate>  
\<scopedCertificates > elemento  
\<Adicionar > elemento para \<scopedCertificates >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<scopedCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       targetUri="string"
       x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</scopedCertificates>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md)|Adiciona um certificado X.509 à coleção de certificados de escopo.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<serviceCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|Especifica um certificado a ser usado ao autenticar um serviço para o cliente.|  
  
## <a name="remarks"></a>Comentários  
 Essa coleção permite que o cliente configurar os certificados de serviço para usar com base na URL do serviço comunica-se com. Isso é especialmente útil em cenários de token emitidos em que um cliente pode estar se comunicando a vários serviços (o serviço end como serviços de token de segurança intermediário). Para associações que usam a segurança de mensagem baseada em certificado, esse certificado é usado para criptografar mensagens para o serviço e deve ser usado pelo serviço para assinar respostas ao cliente.  
  
 Se uma associação requer um certificado para o serviço e nenhum certificado específico para o serviço de que URL for encontrado no ScopedCertificates, o certificado padrão é usado.  
  
 Para obter mais informações, consulte a seção "Certificados no escopo" de [como: Criar um cliente federado](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir especifica um certificado de serviço para o cliente a ser usado ao se comunicar com pontos de extremidade cujo nome de domínio é `http://www.contoso.com` através do protocolo HTTP.  
  
```xml  
<serviceCertificate>
  <scopedCertificates>
    <add targetUri="http://www.contoso.com"
         findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="Root"
         x509FindType="FindByIssuerName" />
  </scopedCertificates>
</serviceCertificate>
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [Trabalhando com certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Como: criar um cliente federado](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md)
- [Protegendo clientes](../../../../../docs/framework/wcf/securing-clients.md)
- [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
