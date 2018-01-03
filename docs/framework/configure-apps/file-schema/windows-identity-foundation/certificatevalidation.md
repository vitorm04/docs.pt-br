---
title: '&lt;certificateValidation&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 7a5d31bce5f71e644b40b3aa7e7c0c1c8790cab6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcertificatevalidationgt"></a>&lt;certificateValidation&gt;
Controla as configurações que manipuladores de token usam para validar certificados. Essas configurações são substituídas se um manipulador específico é configurado com seu próprio validados.  
  
 \<System. IdentityModel >  
\<identityConfiguration >  
\<certificateValidation >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation  
      certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
      revocationMode="NoCheck||Offline||Online"  
      trustedStoreLocation="CurrentLocation||LocalMachine" >  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|certificateValidationMode|Um <xref:System.ServiceModel.Security.X509CertificateValidationMode> valor que especifica o modo de validação a ser usado para o certificado x. 509. O valor padrão é "PeerOrChainTrust". Para especificar um validador personalizado, defina este atributo como "Custom" e especifique o validador usando o [ \<certificateValidator >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md) elemento. Opcional.|  
|revocationMode|Um <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> valor que especifica o modo de revogação a ser usado para o certificado x. 509. O valor padrão é "Online". Opcional.|  
|trustedStoreLocation|Um <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valor que especifica o repositório de certificados x. 509. O valor padrão é "LocalMachine". Opcional.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<certificateValidator >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md)|Especifica um tipo personalizado para validação de certificado. Esse tipo é usado somente se o `certificateValidationMode` atributo o [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) é definido como "Custom".|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Especifica as configurações de identidade de nível de serviço.|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Fornece manipuladores de token de configuração para uma coleção de segurança.|  
  
## <a name="remarks"></a>Comentários  
 Um `<certificateValidation>` elemento pode ser especificado no nível de serviço sob a `<identityConfiguration>` elemento ou em nível de coleção de manipulador de token de segurança sob o `<securityTokenHandlerConfiguration>` elemento. As configurações em uma coleção de manipulador de token substituem aquelas especificadas no serviço. Alguns manipuladores de token permitem que você especifique configurações de validação de certificado na configuração. As configurações em manipuladores de token individuais substituem as especificadas no nível de serviço e na coleção de manipulador de token de segurança.  
  
## <a name="example"></a>Exemplo  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
