---
title: '&lt;certificateValidator&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 98112b3f13ff0b8e4be50f158ce40b048b213248
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcertificatevalidatorgt"></a>&lt;certificateValidator&gt;
Especifica um tipo personalizado para validação de certificado. Esse tipo é usado somente se o `certificateValidationMode` atributo o [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) é definido como "Custom".  
  
 \<System. IdentityModel >  
\<identityConfiguration >  
\<certificateValidation >  
\<certificateValidator >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation>  
      <certificateValidator type=xs:string>  
      </certificateValidator>  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|tipo|Especifica um tipo personalizado que deriva de <xref:System.IdentityModel.Selectors.X509CertificateValidator> classe. Definir o `certificateValidationMode` atributo do [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) "Custom" para usar esse tipo de elemento. Para obter mais informações sobre como especificar o `type` de atributo, consulte [referências de tipo personalizado](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md). Opcional.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|Controla as configurações que manipuladores de token usam para validar certificados.|  
  
## <a name="example"></a>Exemplo  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```
