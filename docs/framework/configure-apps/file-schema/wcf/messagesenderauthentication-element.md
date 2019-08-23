---
title: Elemento <messageSenderAuthentication>
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: 1e63b6fa93e1abfa87c83da4b5d46f492c59b9bc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931370"
---
# <a name="messagesenderauthentication-element"></a>\<elemento de > messageSenderAuthentication
Especifica opções de autenticação para remetentes de mensagens ponto a ponto.  
  
 Para obter mais informações sobre a programação ponto a ponto, consulte [rede ponto a ponto](../../../wcf/feature-details/peer-to-peer-networking.md).  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<endpointBehaviors>  
\<> de comportamento  
\<clientCredentials>  
\<peer>  
\<messageSenderAuthentication>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`customCertificateValidatorType`|Um tipo e um assembly usados para validar um tipo personalizado. Esse atributo deve ser definido quando `certificateValidationMode` é definido como `Custom`.|  
|`certificateValidationMode`|Especifica um dos três modos usados para validar as credenciais. Se definido como `Custom`, um `customCertificateValidator` também deverá ser fornecido.|  
|`revocationMode`|Um dos modos usados para verificar se há listas de certificados revogados (CRL).|  
|`trustedStoreLocation`|Um dos dois locais de armazenamento do sistema `LocalMachine` : `CurrentUser`ou. Esse valor é usado quando um certificado de serviço é negociado para o cliente. A validação é executada no repositório de **pessoas confiáveis** no local de armazenamento especificado.|  
  
## <a name="customcertificatevalidatortype-attribute"></a>Atributo customCertificateValidatorType  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Cadeia de Caracteres|Opcional. Especifica o nome do tipo e o assembly e outros dados usados para localizar o tipo. No mínimo, um namespace e um nome de tipo são necessários. As informações opcionais incluem: nome do assembly, número de versão, cultura e token de chave pública.|  
  
## <a name="certificatevalidationmode-attribute"></a>Atributo certificateValidationMode  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Enumeração|Opcional. Um dos seguintes valores: `None` `ChainTrust`, `PeerTrust`,, `Custom`,. `PeerOrChainTrust` O padrão é `ChainTrust`. O padrão é `ChainTrust`.<br /><br /> Para obter mais informações, consulte [trabalhando com certificados](../../../wcf/feature-details/working-with-certificates.md).|  
  
## <a name="revocationmode-attribute"></a>Atributo rerevocationmode  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Enumeração|Um dos seguintes valores: `NoCheck`, `Online`, `Offline`. O padrão é `Online`.<br /><br /> Para obter mais informações, consulte [trabalhando com certificados](../../../wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>Atributo trustedStoreLocation  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Enumeração|Um dos seguintes valores: `LocalMachine` ou. `CurrentUser` O padrão é `CurrentUser`. Se o aplicativo cliente estiver sendo executado em uma conta do sistema, o certificado geralmente `LocalMachine`estará abaixo de. Se o aplicativo cliente estiver sendo executado sob uma conta de usuário, o certificado normalmente `CurrentUser`estará em. O padrão é `CurrentUser`.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|Especifica uma credencial usada para autenticar o cliente para um serviço de mesmo nível.|  
  
## <a name="remarks"></a>Comentários  
 Esse elemento deve ser configurado se a autenticação de mensagem for escolhida. Para canais de saída, cada mensagem é assinada usando o certificado fornecido pelo [ \<certificado >](certificate-element.md). Todas as mensagens, antes de serem entregues ao aplicativo, são verificadas em relação à credencial da mensagem `customCertificateValidatorType` usando o validador especificado pelo atributo desse elemento. O Validador pode aceitar ou rejeitar a credencial.  
  
## <a name="example"></a>Exemplo  
 O código a seguir define o modo de validação do `PeerOrChainTrust`remetente da mensagem como.  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
          <messageSenderAuthentication certificateValidationMode="PeerOrChainTrust" />
          <messageSenderAuthentication certificateValidationMode="None" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [Trabalhando com certificados](../../../wcf/feature-details/working-with-certificates.md)
- [Rede ponto a ponto](../../../wcf/feature-details/peer-to-peer-networking.md)
- [Autenticação de mensagem de canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [Autenticação personalizada do canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [Protegendo aplicativos de canal par](../../../wcf/feature-details/securing-peer-channel-applications.md)
