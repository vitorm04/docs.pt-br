---
title: '&lt;claimTypeRequired&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 491277e39b29d7c3e0a0d69ec8745b2c6718a91e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltclaimtyperequiredgt"></a>&lt;claimTypeRequired&gt;
Especifica o conjunto de declarações necessárias para tokens de segurança de entrada.  
  
 \<System. IdentityModel >  
\<identityConfiguration >  
\<claimTypeRequired >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 Nenhum  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<claimType >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtype.md)|Especifica uma única declaração opcional ou obrigatórias para tokens de segurança de entrada.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Especifica as configurações de identidade de nível de serviço.|
