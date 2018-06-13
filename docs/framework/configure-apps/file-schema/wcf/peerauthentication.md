---
title: '&lt;peerAuthentication&gt;'
ms.date: 03/30/2017
ms.assetid: ad545e6f-f06e-4549-ac92-09d758d5c636
ms.openlocfilehash: 4d84ffc3fbca03e43c34808e03a57b015898ee07
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352448"
---
# <a name="ltpeerauthenticationgt"></a>&lt;peerAuthentication&gt;
Especifica as configurações de autenticação para um certificado de ponto a ponto usado por um nó ponto a ponto.  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<serviceBehaviors >  
\<comportamento >  
\<serviceCredentials>  
\<par >  
\<peerAuthentication>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<peerAuthentication  
      customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
      certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
      revocationMode="NoCheck/Online/Offline"  
      trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`certificateValidationMode`|Enumeração opcional. Especifica um dos três modos usados para validar credenciais. Esse atributo é do tipo <xref:System.ServiceModel.Security.X509CertificateValidationMode>. Se definido como `Custom`, em seguida, um `customCertificateValidator` também deve ser fornecido.|  
|`customCertificateValidatorType`|Cadeia de caracteres opcional. Especifica um tipo e assembly usados para validar um tipo personalizado. Esse atributo deve ser definido quando `certificateValidationMode` é definido como `Custom`. Esse atributo é do tipo <xref:System.IdentityModel.Selectors.X509CertificateValidator>. Windows Communication Foundation (WCF) fornece um par de padrão de validador de certificado que verifica o certificado de ponto a ponto em relação ao armazenamento de pessoas confiáveis. Ele também verifica se o certificado se encadeia uma raiz válido. Você pode implementar um validador personalizado para especificar um comportamento diferente e usar esse atributo para apontar para o validador personalizado.|  
|`revocationMode`|Enumeração opcional. Especifica o modo de revogação de certificado. Esse atributo é do tipo <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>. O sistema verifica se o certificado de ponto a ponto não foi revogado por procurar na lista de certificados revogados. Essa verificação pode ser executada através da verificação online ou em uma lista de revogação em cache. Verificação de revogação pode ser desativado por configuração deste atributo como NoCheck.|  
|`trustedStoreLocation`|Enumeração opcional. Especifica o local de armazenamento confiável em que o certificado de ponto a ponto é validado pelo sistema de segurança do WCF. Esse atributo é do tipo <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<par >](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|Especifica as credenciais atuais de um nó ponto a ponto.|  
  
## <a name="remarks"></a>Comentários  
 O `<authentication>` elemento corresponde à <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> classe. Este elemento Especifica um validador, que é invocado durante a autenticação de vizinho de vizinho na malha. Quando um novo par tenta estabelecer uma conexão vizinha, ele passa suas próprias credenciais para o par está respondendo. O validador do Respondente é invocado para verificar a credencial da parte remota. Sempre que uma conexão ponto a ponto é estabelecida na malha, os pontos são autenticados mutuamente, validadores significado em ambas as extremidades são invocados.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [Trabalhando com certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Rede ponto a ponto](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [Autenticação de mensagens de canal par](http://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [Autenticação personalizada de canal par](http://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [Protegendo aplicativos de canal par](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
