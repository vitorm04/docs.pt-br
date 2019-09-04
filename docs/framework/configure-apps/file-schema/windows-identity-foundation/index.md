---
title: Esquema de configuração do Windows Identity Foundation
ms.date: 03/30/2017
ms.assetid: 4d4f6d76-49a5-4bad-b345-097b2e2844e9
author: BrucePerlerMS
ms.openlocfilehash: 8dc58f3dc68ee226228056e457914c9dfa53cca5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251972"
---
# <a name="windows-identity-foundation-configuration-schema"></a><span data-ttu-id="2912e-102">Esquema de configuração do Windows Identity Foundation</span><span class="sxs-lookup"><span data-stu-id="2912e-102">Windows Identity Foundation Configuration Schema</span></span>

<span data-ttu-id="2912e-103">Os tópicos nesta seção fornecem informações sobre o esquema de configuração do WIF (Windows Identity Foundation).</span><span class="sxs-lookup"><span data-stu-id="2912e-103">The topics in this section provide information about the Windows Identity Foundation (WIF) configuration schema.</span></span> <span data-ttu-id="2912e-104">Você também pode configurar um aplicativo para usar o WIF por meio de classes expostas pela estrutura.</span><span class="sxs-lookup"><span data-stu-id="2912e-104">You can also configure an application to use WIF through classes exposed by the framework.</span></span> <span data-ttu-id="2912e-105">Essas classes são indicadas nas seções que tratam os elementos relevantes no esquema.</span><span class="sxs-lookup"><span data-stu-id="2912e-105">These classes are noted in the sections that treat relevant elements in the schema.</span></span> <span data-ttu-id="2912e-106">A seguir é mostrada a estrutura de marca XML básica exposta pelo esquema de configuração do WIF.</span><span class="sxs-lookup"><span data-stu-id="2912e-106">The following shows the basic XML tag structure exposed by the WIF configuration schema.</span></span> <span data-ttu-id="2912e-107">Os atributos são omitidos.</span><span class="sxs-lookup"><span data-stu-id="2912e-107">Attributes are omitted.</span></span> <span data-ttu-id="2912e-108">Os comentários realçados indicam os componentes principais do esquema.</span><span class="sxs-lookup"><span data-stu-id="2912e-108">Highlighted comments indicate major components of the schema.</span></span>  
  
```xml  
<configuration>  
    <system.identityModel>  
        <!-- Service Configuration -->  
        <identityConfiguration>  
            <caches>  
                <sessionSecurityTokenCache />  
                <tokenReplayCache />  
            </caches>  
      
            <certificateValidation>  
                <certificateValidator />   
            </certificateValidation>  
      
            <claimsAuthenticationManager />  
      
            <claimsAuthorizationManager>  
                <optionalConfigurationElement>  
            </claimsAuthorizationManager>  
      
            <claimTypeRequired>  
                <claimType />   
            </claimTypeRequired>  
      
            <tokenReplayDetection />  
      
            <!-- Security Token Handler Collection Configuration -->  
            <securityTokenHandlers>  
                <add>  
                    <!-- Can take an optional configuration element which can be one of  
                         the following or a custom element -->  
                    <samlSecurityTokenHandlerRequirement>  
                        <nameClaimType>  
                        <roleClaimType>   
                    </samlSecurityTokenHandlerRequirement>  
      
                    <sessionSecurityTokenHandlerRequirement />  
                    <x509SecurityTokenHandlerRequirement />  
                    <userNameSecurityTokenHandlerRequirement />  
                </add>  
                <clear />  
                <remove />  
                <securityTokenHandlerConfiguration>  
                    <audienceUris>  
                        <add>  
                        <clear>  
                        <remove>  
                    </audienceUris>  
      
                    <caches>  
                        <sessionSecurityTokenCache />  
                        <tokenReplayCache />  
                    </caches>  
      
                    <certificateValidation>  
                        <certificateValidator>   
                    </certificateValidation>  
      
                    <issuerNameRegistry>  
                        <!-- Can take an optional configuration element which can be   
                             the <trustedIssuers> element to configure a configuration-based  
                             issuer name registry or can be a custom element -->  
                        <trustedIssuers>  
                            <add>  
                            <clear>  
                            <remove>  
                        </trustedIssuers>  
                    </issuerNameRegistry>  
      
                    <issuerTokenResolver />  
                    <serviceTokenResolver />  
                    <tokenReplayDetection />  
                </securityTokenHandlerConfiguration>  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
      
    <system.identityModel.services>  
        <!-- Federation Authentication Configuration -->  
        <federatedAuthentication>  
            <cookieHandler>  
                <chunkedCookieHandler />  
                <customCookieHandler />  
            </cookieHandler>  
      
            <serviceCertificate>  
                <certificateReference>  
            </serviceCertificate>  
      
            <wsFederation />  
        </federatedAuthentication>  
    </system.identityModel.services>  
</configuration>  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="2912e-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="2912e-109">In This Section</span></span>  

<span data-ttu-id="2912e-110">[\<system.identityModel>](system-identitymodel.md) Fornece configuração para habilitar as opções do WIF nos aplicativos.</span><span class="sxs-lookup"><span data-stu-id="2912e-110">[\<system.identityModel>](system-identitymodel.md) Provides configuration for enabling WIF options in applications.</span></span>  
  
<span data-ttu-id="2912e-111">[\<system.identityModel.services>](system-identitymodel-services.md) Fornece a configuração para federação passiva usando o WIF.</span><span class="sxs-lookup"><span data-stu-id="2912e-111">[\<system.identityModel.services>](system-identitymodel-services.md) Provides configuration for passive federation using WIF.</span></span> <span data-ttu-id="2912e-112">Configura o SAM (Módulo de Autenticação de Sessão) e o WSFAM (Módulo de Autenticação Federada).</span><span class="sxs-lookup"><span data-stu-id="2912e-112">Configures the Session Authentication Module (SAM) and the Federated Authentication Module (WSFAM).</span></span>
