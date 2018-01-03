---
title: '&lt;certificado&gt; do &lt;elemento&gt; clientCertificate'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00297efb-a7f2-4e03-bc2b-943d545610fc
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0cbf4ac229d63ad1ab097e5dc2ffe76ccb144515
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcertificategt-of-ltclientcertificategt-element"></a>&lt;certificado&gt; do &lt;elemento&gt; clientCertificate
Especifica um x. 509 certificado usado para assinar e criptografar mensagens.  
  
 \<sistema. ServiceModel >  
\<comportamentos >  
\<serviceBehaviors >  
\<comportamento >  
\<serviceCredentials >  
\<clientCertificate >  
\<certificado >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<certificate findValue = "String"   
storeLocation = "CurrentUser/LocalMachine"  
storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem os elementos pai de atributos e elementos filho  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`findValue`|Uma cadeia de caracteres que contém o valor para pesquisar no repositório de certificados x. 509. O tipo contido no atributo deve satisfazer os requisitos do X509FindType especificado. O padrão é uma cadeia de caracteres vazia.|  
|`storeLocation`|Especifica o local do repositório de certificados x. 509 que o cliente usa para validar o certificado do servidor. Os valores válidos incluem o seguinte:<br /><br /> -LocalMachine: o repositório de certificados atribuído ao computador local.<br />-CurrentUser: o repositório de certificados atribuído ao usuário atual.<br /><br /> O padrão é LocalMachine.|  
|`storeName`|Especifica o nome do repositório de certificados X.509 a ser aberto. Os valores válidos incluem o seguinte:<br /><br /> -Catálogo de endereços: O repositório de certificados para outros usuários.<br />-AuthRoot: Repositório de autoridades de certificação de terceiros (ACS) do certificado.<br />-CertificationAuthority: O repositório de certificados para autoridades de certificação intermediárias (CAs).<br />-Proibido: Repositório de certificados revogados de certificados.<br />-My: Repositório de certificados pessoais do certificado.<br />-Raiz: Repositório de certificados (autoridades de certificação de raiz confiável).<br />-TrustedPeople: Repositório de certificados pessoas confiáveis diretamente e recursos.<br />-TrustedPublisher: Repositório de certificados para editores diretamente confiáveis.<br /><br /> O padrão é meu.|  
|`X509FindType`|Define o tipo de pesquisa x. 509 a ser executado. Os valores válidos incluem o seguinte:<br /><br /> -FindByThumbPrint<br />-FindBySubjectName<br />-FindBySubjectDistinguishedName<br />-FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-FindByTimeValid<br />-FindByTimeNotYetValid<br />-FindByTemplateName<br />-FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-FindByKeyUsage<br />-FindBySubjectKeyIdentifier<br /><br /> O tipo contido o `findValue` atributo deve satisfazer os requisitos do X509FindType especificado.<br /><br /> O valor padrão é FindBySubjectDistinguishedName.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)||  
  
## <a name="remarks"></a>Comentários  
 O `<certificate>` elemento é usado quando o serviço deve ter o certificado do cliente com antecedência para comunicação segura com o cliente. Isso ocorre ao usar o padrão de comunicação duplex. No padrão de solicitação/resposta mais comum, o cliente inclui o seu certificado na solicitação, o serviço usa para criptografar e assinar sua resposta ao cliente. No padrão de comunicação duplex, no entanto, o serviço não tem uma solicitação do cliente e, portanto, é necessário que o certificado do cliente com antecedência para proteger a mensagem ao cliente. Portanto você deve obter o certificado do cliente em uma negociação fora de banda e especificar o certificado usando esse elemento. Para obter mais informações sobre serviços de duplex, consulte [como: criar um contrato Duplex](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
## <a name="example"></a>Exemplo  
 O código a seguir especifica como encontrar adequados certificado x. 509 e uma validação personalizada digite o `<authentication>` elemento.  
  
```xml  
<serviceBehaviors>  
 <behavior name="myServiceBehavior">  
  <clientCertificate>  
   <certificate   
         findValue="www.cohowinery.com"   
         storeLocation="CurrentUser"   
         storeName="TrustedPeople"  
         x509FindType="FindByIssuerName" />  
   <authentication customCertificateValidatorType="MyTypes.Coho"  
    certificateValidationMode="Custom"   
    revocationMode="Offline"  
    includeWindowsGroups="false"   
    mapClientCertificateToWindowsAccount="true" />  
  </clientCertificate>  
 </behavior>  
</serviceBehaviors>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Certificate%2A>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Certificate%2A>  
 <xref:System.ServiceModel.Configuration.X509ClientCertificateCredentialsElement>  
 [Comportamentos de segurança](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Como criar um serviço que utiliza um validador de certificado personalizado](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 [Trabalhando com certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
