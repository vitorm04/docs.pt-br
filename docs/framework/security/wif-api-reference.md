---
title: "Referência de API do WIF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a027d902-9314-4bfd-b172-4e81847b1d68
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: e3209ac32314e2ac3f4e3e1920991ed29f956832
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="wif-api-reference"></a>Referência de API do WIF
As classes do WIF (Windows Identity Foundation) foram divididas entre os seguintes assemblies: `mscorlib` (mscorlib.dll), `System.IdentityModel` (System.IdentityModel.dll), `System.IdentityModel.Services` (System.IdentityModel.Services.dll) e `System.ServiceModel` (System.ServiceModel.dll). Este tópico fornece links para os namespaces do WIF e breves explicações sobre as classes que cada namespace contém.  
  
> [!IMPORTANT]
>  Os seguintes namespaces `System.IdentityModel` contêm classes que implementam o modelo de identidade baseada em declarações do WCF: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType> e <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>. A partir do .NET Framework 4.5, o modelo de identidade baseada em declarações do WCF é substituído pelo WIF. Você não deve usar as classes nesses três namespaces ao criar soluções com base no WIF.  
  
 <xref:System.IdentityModel?displayProperty=nameWithType>  
 Contém classes que representam as transformações de cookie, serviços de token de segurança e leitores de dicionário XML especializados.  
  
 <xref:System.IdentityModel.Configuration?displayProperty=nameWithType>  
 Contém classes que fornecem a configuração de aplicativos e serviços criados com o WIF (Windows Identity Foundation). As classes deste namespace representam as configurações no elemento [\<identityConfiguration>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md).  
  
 <xref:System.IdentityModel.Metadata?displayProperty=nameWithType>  
 Contém classes que representam os elementos em um documento de Metadados Federados.  
  
 <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>  
 Contém classes que representam os artefatos do WS-Trust.  
  
 <xref:System.IdentityModel.Services?displayProperty=nameWithType>  
 Contém classes que são usadas nos cenários passivos do (WS-Federation). Também contém algumas classes que representam as configurações no elemento [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md). As configurações nesse elemento definem a Web Services Federation para aplicativos. O namespace `System.IdentityModel.Services.Configuration` contém a maioria das classes que é usada para configurar a Web Services Federation.  
  
 <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>  
 Contém classes que fornecem a configuração para aplicativos WIF que usam o protocolo Web Services Federation. As classes deste namespace representam as configurações no elemento [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md). O namespace `System.IdentityModel.Services` também contém algumas classes que são usadas para configurar a Web Services Federation.  
  
 <xref:System.IdentityModel.Services.Tokens?displayProperty=nameWithType>  
 Contém manipuladores de token de segurança especializados para cenários de web farm.  
  
 <xref:System.IdentityModel.Tokens?displayProperty=nameWithType>  
 Contém classes que representam os tokens de segurança, manipuladores de token de segurança e outros artefatos de token de segurança.  
  
 <xref:System.Security.Claims?displayProperty=nameWithType>  
 Contém classes que representam declarações, identidades baseadas em declarações, entidades de segurança baseadas em declarações e outros artefatos de modelo de identidade baseada em declarações.  
  
 <xref:System.ServiceModel.Security?displayProperty=nameWithType>  
 Contém classes que representam contratos do WCF, canais, hosts de serviço e outros artefatos que são usados em cenários ativos (WS-Trust). Este namespace também contém classes que são específicas ao WCF (Windows Communication Foundation) e que não são usadas pelo WIF.  
  
## <a name="see-also"></a>Consulte também  
 [Referência de configuração do WIF](../../../docs/framework/security/wif-configuration-reference.md)  
 [Mapeamento de namespace entre o WIF 3.5 e o WIF 4.5](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)
