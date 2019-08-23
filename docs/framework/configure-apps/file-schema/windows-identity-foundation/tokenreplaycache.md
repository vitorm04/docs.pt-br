---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 5747a4cfa93118dd41292904b168bbef02fec415
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944070"
---
# <a name="tokenreplaycache"></a>\<tokenReplayCache>
Registra um cache de reprodução de token com um serviço ou uma coleção de manipulador de token de segurança.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<caches>  
\<tokenReplayCache>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <tokenReplayCache type=xs:string>  
      </tokenReplayCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|tipo|Um tipo que deriva da <xref:System.IdentityModel.Tokens.TokenReplayCache> classe. Para obter mais informações sobre como especificar um personalizado `type`, consulte [referências de tipo personalizado].
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<caches>](caches.md)|Registra os caches usados por um serviço ou uma coleção de manipulador de token de segurança.|  
  
## <a name="remarks"></a>Comentários  
 O cache de reprodução de token é usado para detectar tokens reproduzidos. A detecção de reprodução de token é habilitada pelo elemento de [ \<> tokenReplayDetection](tokenreplaydetection.md) , que também especifica o tempo de expiração máximo para tokens.  
  
## <a name="example"></a>Exemplo  
 O XML a seguir mostra a configuração de um cache personalizado para detectar tokens reproduzidos.  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [\<tokenReplayDetection>](tokenreplaydetection.md)
