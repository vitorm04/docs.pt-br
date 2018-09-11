---
title: Elemento &lt;peerAuthentication&gt;
ms.date: 03/30/2017
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
ms.openlocfilehash: 4fb8cc4989313afa3ef16c90b54e0feae1ccb71d
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44274366"
---
# <a name="ltpeerauthenticationgt-element"></a>Elemento &lt;peerAuthentication&gt;
Especifica as opções de autenticação para clientes ponto a ponto.  
  
 Para obter mais informações sobre a programação de peer-to-peer, consulte [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<endpointBehaviors>  
\<comportamento de >  
\<clientCredentials>  
\<par >  
\<peerAuthentication >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<peerAuthentication  
customCertificateValidatorType = "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
revocationMode="NoCheck/Online/Offline"  
trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`customCertificateValidatorType`|Cadeia de caracteres opcional. Um tipo e assembly usados para validar um tipo personalizado. Esse atributo deve ser definido quando `certificateValidationMode` é definido como `Custom`.|  
|`certifcateValidationMode`|Enumeração opcional. Especifica um dos três modos usados para validar as credenciais. Se definido como `Custom`, em seguida, um `customCertificateValidator` também deve ser fornecido. O padrão é `ChainTrust`.|  
|`revocationMode`|Enumeração opcional. Um dos modos usados para verificar por listas de certificados revogados (CRL). O padrão é `Online`.|  
|`trustedStoreLocation`|Enumeração opcional. Um dos locais de armazenamento de sistema de dois: `LocalMachine` ou `CurrentUser`. Esse valor é usado quando um certificado de serviço é negociado ao cliente. Validação é executada em relação a **pessoas confiáveis** armazenar no local de repositório especificado. O padrão é `CurrentUser`.|  
  
## <a name="customcertificatevalidatortype-attribute"></a>customCertificateValidatorType atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Cadeia de Caracteres|Especifica o nome do tipo e assembly e outros dados usados para localizar o tipo. No mínimo, um nome de namespace e tipo são necessários. Incluem informações opcionais: nome do assembly, número de versão, cultura e token de chave pública.|  
  
## <a name="certificatevalidationmode-attribute"></a>certificateValidationMode atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Enumeração|Um dos seguintes valores: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`. O padrão é `ChainTrust`.<br /><br /> Para obter mais informações, consulte [trabalhando com certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="revocationmode-attribute"></a>revocationMode atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Enumeração|Um dos seguintes valores: `NoCheck`, `Online`, `Offline`. O padrão é `Online`.<br /><br /> Para obter mais informações, consulte [trabalhando com certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Enumeração|Um dos seguintes valores: `LocalMachine` ou `CurrentUser`. O padrão é `CurrentUser`. Se o aplicativo cliente é executado sob uma conta do sistema, o certificado está normalmente abaixo `LocalMachine`. Se o aplicativo cliente está em execução em uma conta de usuário, o certificado é normalmente em `CurrentUser`.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<par >](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|Especifica uma credencial usada para autenticar o cliente para um serviço de ponto a ponto.|  
  
## <a name="remarks"></a>Comentários  
 O `<authentication>` elemento corresponde ao <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> classe. Esse elemento Especifica um validador, que é invocado durante a autenticação de vizinho para vizinhos na malha. Quando um novo par tenta estabelecer uma conexão de vizinho, ele passa seu próprio credencial para o par está respondendo. O validador do Respondente é invocado para verificar se a credencial da parte remota. Sempre que uma conexão ponto a ponto é estabelecida na malha, os pontos são autenticados mutuamente, validadores de significado em ambas as extremidades são invocados.  
  
## <a name="example"></a>Exemplo  
 O código a seguir define o modo de validação de certificado `PeerOrChainTrust`.  
  
```xml  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <peer>  
     <certificate findValue="www.contoso.com"   
                   storeLocation="LocalMachine"  
                   x509FindType="FindByIssuerName" />  
     <peerAuthentication   
          certificateValidationMode="PeerOrChainTrust" />  
     <messageSenderAuthentication certificateValidationMode="None" />  
    </peer>  
   </clientCredentials>  
  </behavior>  
</endpointBehaviors>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [Trabalhando com certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Rede ponto a ponto](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [Autenticação de mensagem de canal par](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [Autenticação personalizada de canal par](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [Protegendo aplicativos de canal par](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
