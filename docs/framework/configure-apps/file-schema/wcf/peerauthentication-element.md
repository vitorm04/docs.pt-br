---
title: Elemento <peerAuthentication>
ms.date: 03/30/2017
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
ms.openlocfilehash: 09094c00b8faa28c37e202112251fee7cb4580be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934015"
---
# <a name="peerauthentication-element"></a>\<Elemento de > peerAuthentication
Especifica opções de autenticação para clientes ponto a ponto.  
  
 Para obter mais informações sobre a programação ponto a ponto, consulte [rede ponto a ponto](../../../wcf/feature-details/peer-to-peer-networking.md).  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<endpointBehaviors>  
\<> de comportamento  
\<clientCredentials>  
\<peer>  
\<> PeerAuthentication  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`customCertificateValidatorType`|Cadeia de caracteres opcional. Um tipo e um assembly usados para validar um tipo personalizado. Esse atributo deve ser definido quando `certificateValidationMode` é definido como `Custom`.|  
|`certificateValidationMode`|Enumeração opcional. Especifica um dos três modos usados para validar as credenciais. Se definido como `Custom`, um `customCertificateValidator` também deverá ser fornecido. O padrão é `ChainTrust`.|  
|`revocationMode`|Enumeração opcional. Um dos modos usados para verificar se há listas de certificados revogados (CRL). O padrão é `Online`.|  
|`trustedStoreLocation`|Enumeração opcional. Um dos dois locais de armazenamento do sistema `LocalMachine` : `CurrentUser`ou. Esse valor é usado quando um certificado de serviço é negociado para o cliente. A validação é executada no repositório de **pessoas confiáveis** no local de armazenamento especificado. O padrão é `CurrentUser`.|  
  
## <a name="customcertificatevalidatortype-attribute"></a>Atributo customCertificateValidatorType  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Cadeia de Caracteres|Especifica o nome do tipo e o assembly e outros dados usados para localizar o tipo. No mínimo, um namespace e um nome de tipo são necessários. As informações opcionais incluem: nome do assembly, número de versão, cultura e token de chave pública.|  
  
## <a name="certificatevalidationmode-attribute"></a>Atributo certificateValidationMode  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Enumeração|Um dos seguintes valores: `None` `ChainTrust`, `PeerTrust`,, `Custom`,. `PeerOrChainTrust` O padrão é `ChainTrust`.<br /><br /> Para obter mais informações, consulte [trabalhando com certificados](../../../wcf/feature-details/working-with-certificates.md).|  
  
## <a name="revocationmode-attribute"></a>Atributo rerevocationmode  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Enumeração|Um dos seguintes valores: `NoCheck`, `Online`, `Offline`. O padrão é `Online`.<br /><br /> Para obter mais informações, consulte [trabalhando com certificados](../../../wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>Atributo trustedStoreLocation  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Enumeração|Um dos seguintes valores: `LocalMachine` ou. `CurrentUser` O padrão é `CurrentUser`. Se o aplicativo cliente estiver sendo executado em uma conta do sistema, o certificado geralmente `LocalMachine`estará abaixo de. Se o aplicativo cliente estiver sendo executado sob uma conta de usuário, o certificado normalmente `CurrentUser`estará em.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|Especifica uma credencial usada para autenticar o cliente para um serviço de mesmo nível.|  
  
## <a name="remarks"></a>Comentários  
 O `<authentication>` elemento corresponde <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> à classe. Esse elemento especifica um validador, que é invocado durante a autenticação de vizinho para vizinho na malha. Quando um novo par tenta estabelecer uma conexão vizinha, ele passa sua própria credencial para o par de resposta. O validador do respondente é chamado para verificar a credencial da parte remota. Sempre que uma conexão de mesmo nível é estabelecida na malha, ambos os pares são mutuamente autenticados, o que significa que os validadores em ambas as extremidades são invocados.  
  
## <a name="example"></a>Exemplo  
 O código a seguir define o modo de validação `PeerOrChainTrust`de certificado como.  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
          <peerAuthentication certificateValidationMode="PeerOrChainTrust" />
          <messageSenderAuthentication certificateValidationMode="None" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [Trabalhando com certificados](../../../wcf/feature-details/working-with-certificates.md)
- [Rede ponto a ponto](../../../wcf/feature-details/peer-to-peer-networking.md)
- [Autenticação de mensagem de canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [Autenticação personalizada do canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [Protegendo aplicativos de canal par](../../../wcf/feature-details/securing-peer-channel-applications.md)
