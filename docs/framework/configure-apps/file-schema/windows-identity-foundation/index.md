---
title: Esquema de configuração do Windows Identity Foundation
ms.date: 03/30/2017
ms.assetid: 4d4f6d76-49a5-4bad-b345-097b2e2844e9
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 8881339a5dcf21df17e7200847fc46854ead17e3
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43468437"
---
# <a name="windows-identity-foundation-configuration-schema"></a><span data-ttu-id="ae7f4-102">Esquema de configuração do Windows Identity Foundation</span><span class="sxs-lookup"><span data-stu-id="ae7f4-102">Windows Identity Foundation Configuration Schema</span></span>
<span data-ttu-id="ae7f4-103">Os tópicos nesta seção fornecem informações sobre o esquema de configuração do WIF (Windows Identity Foundation).</span><span class="sxs-lookup"><span data-stu-id="ae7f4-103">The topics in this section provide information about the Windows Identity Foundation (WIF) configuration schema.</span></span> <span data-ttu-id="ae7f4-104">Você também pode configurar um aplicativo para usar o WIF por meio de classes expostas pela estrutura.</span><span class="sxs-lookup"><span data-stu-id="ae7f4-104">You can also configure an application to use WIF through classes exposed by the framework,.</span></span> <span data-ttu-id="ae7f4-105">Essas classes são indicadas nas seções que tratam os elementos relevantes no esquema.</span><span class="sxs-lookup"><span data-stu-id="ae7f4-105">These classes are noted in the sections that treat relevant elements in the schema.</span></span> <span data-ttu-id="ae7f4-106">A seguir é mostrada a estrutura de marca XML básica exposta pelo esquema de configuração do WIF.</span><span class="sxs-lookup"><span data-stu-id="ae7f4-106">The following shows the basic XML tag structure exposed by the WIF configuration schema.</span></span> <span data-ttu-id="ae7f4-107">Os atributos são omitidos.</span><span class="sxs-lookup"><span data-stu-id="ae7f4-107">Attributes are omitted.</span></span> <span data-ttu-id="ae7f4-108">Os comentários realçados indicam os componentes principais do esquema.</span><span class="sxs-lookup"><span data-stu-id="ae7f4-108">Highlighted comments indicate major components of the schema.</span></span>  
  
```xml  
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
```  
  
## <a name="in-this-section"></a><span data-ttu-id="ae7f4-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="ae7f4-109">In This Section</span></span>  
 <span data-ttu-id="ae7f4-110">[\<system.identityModel>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) Fornece configuração para habilitar as opções do WIF nos aplicativos.</span><span class="sxs-lookup"><span data-stu-id="ae7f4-110">[\<system.identityModel>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) Provides configuration for enabling WIF options in applications.</span></span>  
  
 <span data-ttu-id="ae7f4-111">[\<system.identityModel.services>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) Fornece a configuração para federação passiva usando o WIF.</span><span class="sxs-lookup"><span data-stu-id="ae7f4-111">[\<system.identityModel.services>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) Provides configuration for passive federation using WIF.</span></span> <span data-ttu-id="ae7f4-112">Configura o SAM (Módulo de Autenticação de Sessão) e o WSFAM (Módulo de Autenticação Federada).</span><span class="sxs-lookup"><span data-stu-id="ae7f4-112">Configures the Session Authentication Module (SAM) and the Federated Authentication Module (WSFAM).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ae7f4-113">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="ae7f4-113">Related Sections</span></span>  
 <span data-ttu-id="ae7f4-114">[Configuração, administração e gerenciamento](https://msdn.microsoft.com/library/1e03c389-de2c-4096-aaff-86b087e1bea0) Descreve como configurar e gerenciar serviços e aplicativos do WIF.</span><span class="sxs-lookup"><span data-stu-id="ae7f4-114">[Configuration, Administration, And Management](https://msdn.microsoft.com/library/1e03c389-de2c-4096-aaff-86b087e1bea0) Describes how to configure and manage WIF applications and services.</span></span>
