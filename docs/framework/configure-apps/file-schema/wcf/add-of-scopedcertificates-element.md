---
title: '&lt;adicionar&gt; elemento &lt;scopedCertificates&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eff535f7eb779a69c2368f3ad815f1eb124946ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltscopedcertificatesgt-element"></a>&lt;adicionar&gt; elemento &lt;scopedCertificates&gt;
Adiciona um certificado x. 509 à coleção de certificados de escopo.  
  
 \<sistema. ServiceModel >  
\<comportamentos >  
seção endpointBehaviors  
\<comportamento >  
\<clientCredentials >  
\<serviceCertificate >  
\<scopedCertificates >  
\<Adicionar > elemento para \<scopedCertificates >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<add findValue="String"  
          storeLocation="CurrentUser/LocalMachine"  
          storeName=" CurrentUser/LocalMachine"  
          targetUri="string"  
         x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"   
/>   
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem os elementos pai de atributos e elementos filho  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|targetUri|Cadeia. Especifica o URI do serviço associado ao certificado.|  
|findValue|Cadeia. O valor a ser procurado.|  
|X509FindType|Enumeração. Um dos campos de certificado a ser pesquisado.|  
|storeLocation|Enumeração. Um dos dois locais de repositório para pesquisar.|  
|storeName|Enumeração. Um dos repositórios de sistema para pesquisar.|  
  
## <a name="findvalue-attribute"></a>findValue atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Cadeia de Caracteres|O valor depende do campo (especificado pelo atributo X509FindType) que está sendo pesquisado. Por exemplo, se você está procurando uma impressão digital, o valor deve ser uma cadeia de caracteres de números hexadecimais.|  
  
## <a name="x509findtype-attribute"></a>Atributo x509FindType  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Enumeração|Os valores incluem: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.|  
  
## <a name="storelocation-attribute"></a>storeLocation atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Enumeração|CurrentUser ou LocalMachine.|  
  
## <a name="storename-attribute"></a>Atributo da storeName  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Enumeração|Os valores incluem: catálogo de endereços, AuthRoot, CertificateAuthority, não permitidas, My, raiz, TrustedPeople e TrustedPublisher.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<scopedCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)|Representa uma coleção de certificados x. 509 fornecidos por serviços específicos (escopo) para autenticação.|  
  
## <a name="remarks"></a>Comentários  
 Esse elemento permite que o cliente configurar um certificado de serviço para uso com base na URL do serviço, que ele se comunica. Isso é especialmente útil em cenários de token emitidos onde um cliente pode se comunicar a vários serviços (o serviço end bem como serviços de token de segurança intermediário). Para associações que usam a segurança de mensagens baseada em certificado, esse certificado é usado para criptografar mensagens para o serviço e deve ser usada pelo serviço para assinar respostas ao cliente.  
  
 Se uma associação requer um certificado para o serviço e nenhum certificado específico para o serviço de que URL se encontra o ScopedCertificates, o certificado padrão é usado.  
  
 Para obter mais informações, consulte a seção "Escopo certificados" [como: criar um cliente federado](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir adiciona um certificado x. 509 a coleção.  
  
```xml  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <serviceCertificate>  
     <scopedCertificates>  
      <add targetUri="http://www.contoso.com"   
       findValue="www.Contoso.com"   
       storeLocation="LocalMachine"  
       storeName="Root"   
       x509FindType="FindByIssuerName" />  
     </scopedCertificates>  
    </serviceCertificate>  
   </clientCredentials>  
  </behavior>  
 </endpointBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>  
 [Como criar um cliente federado](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [Trabalhando com certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Protegendo clientes](../../../../../docs/framework/wcf/securing-clients.md)  
 [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
