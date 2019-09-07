---
title: <certificate>do <clientCertificate> elemento
ms.date: 03/30/2017
ms.assetid: 00297efb-a7f2-4e03-bc2b-943d545610fc
ms.openlocfilehash: d0c4ef9d3657d2dfa787feb3576beda09d1997a3
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400541"
---
# <a name="certificate-of-clientcertificate-element"></a>\<> de certificado \<do elemento de > de clientCertificate
Especifica um certificado X. 509 usado para assinar e criptografar mensagens.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> clientCertificate**](clientcertificate-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de certificado**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<certificate findValue="String"
             storeLocation = "CurrentUser/LocalMachine"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`findValue`|Uma cadeia de caracteres que contém o valor a ser procurado no repositório de certificados X. 509. O tipo contido no atributo deve atender aos requisitos do X509FindType especificado. O padrão é uma cadeia de caracteres vazia.|  
|`storeLocation`|Especifica o local do repositório de certificados X. 509 que o cliente usa para validar o certificado do servidor. Os valores válidos incluem o seguinte:<br /><br /> -LocalMachine: o repositório de certificados atribuído ao computador local.<br />-CurrentUser: o repositório de certificados atribuído ao usuário atual.<br /><br /> O padrão é LocalMachine.|  
|`storeName`|Especifica o nome do repositório de certificados X.509 a ser aberto. Os valores válidos incluem o seguinte:<br /><br /> Catálogo Repositório de certificados para outros usuários.<br />- AuthRoot: Repositório de certificados para CAs (autoridades de certificação) de terceiros.<br />- CertificationAuthority: Repositório de certificados para CAs (autoridades de certificação) intermediárias.<br />Permitida Repositório de certificados para certificados revogados.<br />Pasta Repositório de certificados para certificados pessoais.<br />Básica Repositório de certificados para autoridades de certificação raiz confiáveis (CAs).<br />TrustedPeople Repositório de certificados para pessoas e recursos diretamente confiáveis.<br />- TrustedPublisher: Repositório de certificados para editores diretamente confiáveis.<br /><br /> O padrão é My.|  
|`X509FindType`|Define o tipo de pesquisa de X.509 a ser executada. Os valores válidos incluem o seguinte:<br /><br /> -   FindByThumbPrint<br />-FindBySubjectName<br />- FindBySubjectDistinguishedName<br />- FindByIssuerName<br />- FindByIssuerDistinguishedName<br />-   FindBySerialNumber<br />- FindByTimeValid<br />-   FindByTimeNotYetValid<br />-   FindByTemplateName<br />- FindByApplicationPolicy<br />- FindByCertificatePolicy<br />- FindByExtension<br />-   FindByKeyUsage<br />-   FindBySubjectKeyIdentifier<br /><br /> O tipo contido no `findValue` atributo deve atender aos requisitos do X509FindType especificado.<br /><br /> O valor padrão é FindBySubjectDistinguishedName.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)||  
  
## <a name="remarks"></a>Comentários  
 O `<certificate>` elemento é usado quando o serviço deve ter o certificado do cliente com antecedência para se comunicar com segurança com o cliente. Isso ocorre ao usar o padrão de comunicação duplex. No padrão de solicitação/resposta mais comum, o cliente inclui seu certificado na solicitação, que o serviço usa para criptografar e assinar sua resposta para o cliente. No padrão de comunicação duplex, no entanto, o serviço não tem uma solicitação do cliente e, portanto, precisa do certificado do cliente com antecedência para proteger a mensagem para o cliente. Portanto, você deve obter o certificado do cliente em uma negociação fora de banda e especificar o certificado usando esse elemento. Para obter mais informações sobre os serviços duplex [, consulte Como: Crie um contrato](../../../wcf/feature-details/how-to-create-a-duplex-contract.md)duplex.  
  
## <a name="example"></a>Exemplo  
 O código a seguir especifica como encontrar um certificado X. 509 apropriado e um tipo de validação personalizado no `<authentication>` elemento.  
  
```xml  
<serviceBehaviors>
  <behavior name="myServiceBehavior">
    <clientCertificate>
      <certificate findValue="www.cohowinery.com"
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

- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509ClientCertificateCredentialsElement>
- [Comportamentos de segurança](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Como: Criar um serviço que empregue um validador de certificado personalizado](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [Trabalhando com certificados](../../../wcf/feature-details/working-with-certificates.md)
