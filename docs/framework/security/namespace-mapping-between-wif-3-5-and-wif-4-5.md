---
title: Mapeamento de namespace entre o WIF 3.5 e o WIF 4.5
ms.date: 03/30/2017
ms.assetid: a092d98c-444d-4336-a644-63c2e11e96c8
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: a120347d20de5b881ccb60d03da482856d9e68a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407976"
---
# <a name="namespace-mapping-between-wif-35-and-wif-45"></a>Mapeamento de namespace entre o WIF 3.5 e o WIF 4.5
Do .NET 4.5 em diante, o WIF (Windows Identity Foundation) foi totalmente integrado ao .NET Framework. Essa integração gerou alterações de nome e alguma consolidação dos namespaces do WIF e da superfície de API. Este tópico fornece algumas diretrizes e um mapeamento geral entre os namespaces do WIF 3.5 e os namespaces do WIF 4.5. Ele não se destina a apresentar a íntegra, mas em vez disso, fornecer algumas informações gerais sobre onde encontrar classes familiares do WIF 3.5 no WIF 4.5. Para obter mais informações sobre as diferenças entre o WIF 3.5 e o WIF 4.5, consulte [Novidades no Windows Identity Foundation 4.5](../../../docs/framework/security/whats-new-in-wif.md). Para obter diretrizes sobre como migrar um aplicativo criado usando o WIF 3.5 para o WIF 4.5, consulte [Diretrizes para migrar um aplicativo criado usando o WIF 3.5 para o WIF 4.5](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md).  
  
## <a name="wif-35-to-wif-45-namespace-map"></a>Mapa de namespaces do WIF 3.5 para o WIF 4.5  
 As classes do WIF, que foram coletadas sob os namespaces `Microsoft.IdentityModel` no WIF 3.5, agora são distribuídas entre os namespaces `System.Security.Claims`, `System.ServiceModel.Security` e `System.IdentityModel` no WIF 4.5. Além disso, alguns namespaces WIF 3.5 foram consolidados ou removidos inteiramente no WIF 4.5.  
  
> [!IMPORTANT]
>  Os seguintes namespaces `System.IdentityModel` contêm classes que implementam o modelo de identidade baseada em declarações do WCF: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType> e <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>. O modelo de identidade baseada em declarações do WCF é substituído pelo do WIF. Você não deve usar as classes nesses três namespaces ao criar soluções com base no WIF.  
  
 A tabela a seguir fornece informações sobre onde as classes WIF 3.5 podem ser encontrados no WIF 4.5.  
  
|**Namespace do WIF 3.5**|**Namespace do WIF 4.5**|**Comentários**|  
|-|-|-|  
|`Microsoft.IdentityModel`|<xref:System.IdentityModel?displayProperty=nameWithType>|- A maioria das classes que representam constantes não são implementadas.<br />- As classes que são usadas para criar serviços de token de segurança foram movidas de `Microsoft.IdentityModel.SecurityTokenService` para <xref:System.IdentityModel?displayProperty=nameWithType>.<br />- As classes em `Microsoft.IdentityModel.Threading` foram movidas para <xref:System.IdentityModel?displayProperty=nameWithType>.<br />- As classes `ExceptionMapper` e `MruSecurityTokenCache` não são implementadas.|  
|`Microsoft.IdentityModel.Claims`|<xref:System.Security.Claims?displayProperty=nameWithType>|- As interfaces `IClaimsPrincipal` e `IClaimsIdentity` não são implementadas em WIF 4.5. Em vez disso, <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType> e <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> agora são as classes base das quais derivam a maioria das classes de identidade e de entidade de segurança do .NET. Isso significa que não há necessidade de classes de identidade e de entidade de segurança de declarações especializadas como `Microsoft.IdentityModel.Claims.WindowsClaimsPrincipal` e `Microsoft.IdentityModel.Claims.WindowsClaimsIdentity` no WIF 4.5, use <xref:System.Security.Principal.WindowsPrincipal?displayProperty=nameWithType> e <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> em vez disso. O mesmo é verdadeiro para as outras classes de identidade e de entidade de segurança de declarações especializadas que existiam no WIF 3.5.<br />- A classe `Microsoft.IdentityModel.Claims.ClaimsCollection` não é implementada no WIF 4.5. Em vez disso, coleções de declarações são expostas como coleções enumeráveis do tipo <xref:System.Security.Claims.Claim?displayProperty=nameWithType>.<br />-   <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType> e <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> fornecem métodos que agora dão suporte total a LINQ.|  
|`Microsoft.IdentityModel.Configuration`|<xref:System.IdentityModel.Configuration?displayProperty=nameWithType>|Alguns elementos e classes sofreram alterações de nome e algumas foram removidas no WIF 4.5; por exemplo, `Microsoft.IdentityModel.Configuraiton.ServiceConfiguration` agora é <xref:System.IdentityModel.Configuration.IdentityConfiguration?displayProperty=nameWithType>.|  
|`Microsoft.IdentityModel.Protocols`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Protocols.WSFederation`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Protocols.WSFederation.Metadata`|<xref:System.IdentityModel.Metadata?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Protocols.WSIdentity`|Não implementado no WIF 4.5|No WIF 3.5, continha classes para dar suporte a CardSpace, não implementado no WIF 4.5.|  
|`Microsoft.IdentityModel.Protocols.WSTrust`|Divididos entre os namespaces <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType> e <xref:System.ServiceModel.Security?displayProperty=nameWithType>.|Classes que representam artefatos WS-Trust estão no namespace <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>; por exemplo, a classe <xref:System.IdentityModel.Protocols.WSTrust.RequestSecurityToken>. Classes que representam contratos de serviço WCF, hosts de serviço e canais que habilitam um serviço WCF a se comunicar usando o protocolo WS-Trust estão no namespace <xref:System.ServiceModel.Security?displayProperty=nameWithType>, por exemplo, a classe <xref:System.ServiceModel.Security.WSTrustServiceHost>.|  
|`Microsoft.IdentityModel.Protocols.WSTrust.Bindings`|Não implementado no WIF 4.5|-|  
|`Microsoft.IdentityModel.Protocols.XmlEncryption`|Não implementado no WIF 4.5|Continha classes representando as constantes de criptografia XML no WIF 3.5. Constantes não são implementadas no WIF 4.5.|  
|`Microsoft.IdentityModel.Protocols.XmlSignature`|<xref:System.IdentityModel?displayProperty=nameWithType>|A classe `EnvelopingSignature` e as classes que representam constantes não são implementadas.|  
|`Microsoft.IdentityModel.SecurityTokenService`|Divididos entre os namespaces <xref:System.IdentityModel?displayProperty=nameWithType>, <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType> e <xref:System.IdentityModel.Tokens?displayProperty=nameWithType>.|-|  
|`Microsoft.IdentityModel.Threading`|<xref:System.IdentityModel?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Tokens`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Tokens.Saml11`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Tokens.Saml2`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Web`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Web.Configuration`|<xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>|Classes que fornecem a configuração para cenários passivos (Web Services Federation) foram em grande parte movidas para <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>; no entanto, algumas dessas classes estão em <xref:System.IdentityModel.Services?displayProperty=nameWithType>.|  
|`Microsoft.IdentityModel.Web.Controls`|Não implementado no WIF 4.5|As classes em `Microsoft.IdentityModel.Web.Controls` implementadas no Controle de Entrada Passivo Federado, que não existe no WIF 4.5.|  
|`Microsoft.IdentityModel.WindowsTokenService`|Não implementado no WIF 4.5|-|  
  
## <a name="see-also"></a>Consulte também  
 [Novidades no Windows Identity Foundation 4.5](../../../docs/framework/security/whats-new-in-wif.md)  
 [Diretrizes para migrar um aplicativo criado usando o WIF 3.5 para o WIF 4.5](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md)
