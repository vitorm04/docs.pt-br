---
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: 3f3d79d3567c1714a79423b7767ce3f454b9d52d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152782"
---
# <a name="certificatevalidator"></a>\<> do validador de certificados
Especifica um tipo personalizado para validação de certificado. Esse tipo só é `certificateValidationMode` usado se o atributo do [ \<elemento validar>certificado](certificatevalidation.md) estiver definido como "Personalizado".  
  
[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de configuração de identidade**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de validação de certificados**](certificatevalidation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>do validador de certificados**  
  
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
|type|Especifica um tipo personalizado que <xref:System.IdentityModel.Selectors.X509CertificateValidator> deriva da classe. Defina `certificateValidationMode` o atributo do [ \<certificadoValidação>](certificatevalidation.md) elemento como "Personalizado" para usar esse tipo. Para obter mais informações `type` sobre como especificar o atributo, consulte [Referências de tipo personalizadas](../windows-workflow-foundation/index.md). Opcional.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<>de validação de certificados](certificatevalidation.md)|Controla as configurações que os manipuladores de tokens usam para validar certificados.|  
  
## <a name="example"></a>Exemplo  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />
</certificateValidation>
```
