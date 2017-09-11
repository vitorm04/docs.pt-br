---
title: "Referência de API do WIF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a027d902-9314-4bfd-b172-4e81847b1d68
caps.latest.revision: 4
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ef439ff502fc39074d36f63d139fd23e42471d42
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="wif-api-reference"></a><span data-ttu-id="725e6-102">Referência de API do WIF</span><span class="sxs-lookup"><span data-stu-id="725e6-102">WIF API Reference</span></span>
<span data-ttu-id="725e6-103">As classes do WIF (Windows Identity Foundation) foram divididas entre os seguintes assemblies: `mscorlib` (mscorlib.dll), `System.IdentityModel` (System.IdentityModel.dll), `System.IdentityModel.Services` (System.IdentityModel.Services.dll) e `System.ServiceModel` (System.ServiceModel.dll).</span><span class="sxs-lookup"><span data-stu-id="725e6-103">Windows Identity Foundation (WIF) classes are split across the following assemblies: `mscorlib` (mscorlib.dll), `System.IdentityModel` (System.IdentityModel.dll), `System.IdentityModel.Services` (System.IdentityModel.Services.dll), and `System.ServiceModel` (System.ServiceModel.dll).</span></span> <span data-ttu-id="725e6-104">Este tópico fornece links para os namespaces do WIF e breves explicações sobre as classes que cada namespace contém.</span><span class="sxs-lookup"><span data-stu-id="725e6-104">This topic provides links to the WIF namespaces and brief explanations of the classes that each namespace contains.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="725e6-105">Os seguintes namespaces `System.IdentityModel` contêm classes que implementam o modelo de identidade baseada em declarações do WCF: <xref:System.IdentityModel.Claims?displayProperty=fullName>, <xref:System.IdentityModel.Policy?displayProperty=fullName> e <xref:System.IdentityModel.Selectors?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="725e6-105">The following `System.IdentityModel` namespaces contain classes that implement the WCF claims-based identity model: <xref:System.IdentityModel.Claims?displayProperty=fullName>, <xref:System.IdentityModel.Policy?displayProperty=fullName>, and <xref:System.IdentityModel.Selectors?displayProperty=fullName>.</span></span> <span data-ttu-id="725e6-106">A partir do .NET Framework 4.5, o modelo de identidade baseada em declarações do WCF é substituído pelo WIF.</span><span class="sxs-lookup"><span data-stu-id="725e6-106">Starting with .NET Framework 4.5, the WCF claims-based identity model is superseded by WIF.</span></span> <span data-ttu-id="725e6-107">Você não deve usar as classes nesses três namespaces ao criar soluções com base no WIF.</span><span class="sxs-lookup"><span data-stu-id="725e6-107">You should not use classes in these three namespaces when building solutions based on WIF.</span></span>  
  
 <xref:System.IdentityModel?displayProperty=fullName>  
 <span data-ttu-id="725e6-108">Contém classes que representam as transformações de cookie, serviços de token de segurança e leitores de dicionário XML especializados.</span><span class="sxs-lookup"><span data-stu-id="725e6-108">Contains classes that represent cookie transforms, security token services, and specialized XML dictionary readers.</span></span>  
  
 <xref:System.IdentityModel.Configuration?displayProperty=fullName>  
 <span data-ttu-id="725e6-109">Contém classes que fornecem a configuração de aplicativos e serviços criados com o WIF (Windows Identity Foundation).</span><span class="sxs-lookup"><span data-stu-id="725e6-109">Contains classes that provide configuration for applications and services built using the Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="725e6-110">As classes deste namespace representam as configurações no elemento [\<identityConfiguration>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md).</span><span class="sxs-lookup"><span data-stu-id="725e6-110">The classes in this namespace represent settings under the [\<identityConfiguration>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span>  
  
 <xref:System.IdentityModel.Metadata?displayProperty=fullName>  
 <span data-ttu-id="725e6-111">Contém classes que representam os elementos em um documento de Metadados Federados.</span><span class="sxs-lookup"><span data-stu-id="725e6-111">Contains classes that represent elements in a Federation Metadata document.</span></span>  
  
 <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=fullName>  
 <span data-ttu-id="725e6-112">Contém classes que representam os artefatos do WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="725e6-112">Contains classes that represent WS-Trust artifacts.</span></span>  
  
 <xref:System.IdentityModel.Services?displayProperty=fullName>  
 <span data-ttu-id="725e6-113">Contém classes que são usadas nos cenários passivos do (WS-Federation).</span><span class="sxs-lookup"><span data-stu-id="725e6-113">Contains classes that are used in passive (WS-Federation) scenarios.</span></span> <span data-ttu-id="725e6-114">Também contém algumas classes que representam as configurações no elemento [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md).</span><span class="sxs-lookup"><span data-stu-id="725e6-114">Also contains some classes that represent settings under the [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) element.</span></span> <span data-ttu-id="725e6-115">As configurações nesse elemento definem a Web Services Federation para aplicativos.</span><span class="sxs-lookup"><span data-stu-id="725e6-115">Settings under this element configure WS-Federation for applications.</span></span> <span data-ttu-id="725e6-116">O namespace `System.IdentityModel.Services.Configuration` contém a maioria das classes que é usada para configurar a Web Services Federation.</span><span class="sxs-lookup"><span data-stu-id="725e6-116">The `System.IdentityModel.Services.Configuration` namespace contains most of the classes that are used to configure WS-Federation.</span></span>  
  
 <xref:System.IdentityModel.Services.Configuration?displayProperty=fullName>  
 <span data-ttu-id="725e6-117">Contém classes que fornecem a configuração para aplicativos WIF que usam o protocolo Web Services Federation.</span><span class="sxs-lookup"><span data-stu-id="725e6-117">Contains classes that provide configuration for WIF applications that use the WS-Federation protocol.</span></span> <span data-ttu-id="725e6-118">As classes deste namespace representam as configurações no elemento [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md).</span><span class="sxs-lookup"><span data-stu-id="725e6-118">The classes in this namespace represent settings under the [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) element.</span></span> <span data-ttu-id="725e6-119">O namespace `System.IdentityModel.Services` também contém algumas classes que são usadas para configurar a Web Services Federation.</span><span class="sxs-lookup"><span data-stu-id="725e6-119">The `System.IdentityModel.Services` namespace also contains some classes that are used to configure WS-Federation.</span></span>  
  
 <xref:System.IdentityModel.Services.Tokens?displayProperty=fullName>  
 <span data-ttu-id="725e6-120">Contém manipuladores de token de segurança especializados para cenários de web farm.</span><span class="sxs-lookup"><span data-stu-id="725e6-120">Contains specialized security token handlers for Web farm scenarios.</span></span>  
  
 <xref:System.IdentityModel.Tokens?displayProperty=fullName>  
 <span data-ttu-id="725e6-121">Contém classes que representam os tokens de segurança, manipuladores de token de segurança e outros artefatos de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="725e6-121">Contains classes that represent security tokens, security token handlers, and other security token artifacts.</span></span>  
  
 <xref:System.Security.Claims?displayProperty=fullName>  
 <span data-ttu-id="725e6-122">Contém classes que representam declarações, identidades baseadas em declarações, entidades de segurança baseadas em declarações e outros artefatos de modelo de identidade baseada em declarações.</span><span class="sxs-lookup"><span data-stu-id="725e6-122">Contains classes that represent claims, claims-based identities, claims-based principals, and other claims-based identity model artifacts.</span></span>  
  
 <xref:System.ServiceModel.Security?displayProperty=fullName>  
 <span data-ttu-id="725e6-123">Contém classes que representam contratos do WCF, canais, hosts de serviço e outros artefatos que são usados em cenários ativos (WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="725e6-123">Contains classes that represent WCF contracts, channels, service hosts and other artifacts that are used in active (WS-Trust) scenarios.</span></span> <span data-ttu-id="725e6-124">Este namespace também contém classes que são específicas ao WCF (Windows Communication Foundation) e que não são usadas pelo WIF.</span><span class="sxs-lookup"><span data-stu-id="725e6-124">This namespace also contains classes that are specific to Windows Communication Foundation (WCF) and that are not used by WIF.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="725e6-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="725e6-125">See Also</span></span>  
 <span data-ttu-id="725e6-126">[Referência de configuração do WIF](../../../docs/framework/security/wif-configuration-reference.md) </span><span class="sxs-lookup"><span data-stu-id="725e6-126">[WIF Configuration Reference](../../../docs/framework/security/wif-configuration-reference.md) </span></span>  
 [<span data-ttu-id="725e6-127">Mapeamento de namespace entre o WIF 3.5 e o WIF 4.5</span><span class="sxs-lookup"><span data-stu-id="725e6-127">Namespace Mapping between WIF 3.5 and WIF 4.5</span></span>](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)

