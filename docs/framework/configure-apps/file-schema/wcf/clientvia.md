---
title: <clientVia>
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: 063dbee71a91e098e26026ea78c74642115c7955
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266657"
---
# <a name="clientvia"></a>\<clientVia>
Especifica o URI para o qual o canal de transporte deve ser criado. Para obter mais informações, consulte <xref:System.ServiceModel.Description.ClientViaBehavior>.  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<endpointBehaviors>  
\<behavior>  
\<clientVia>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`viaUri`|Uma cadeia de caracteres que especifica um URI que indica a rota que uma mensagem deve seguir.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<behavior>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Especifica um comportamento de ponto de extremidade.|  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Configuration.ClientViaElement>
- <xref:System.ServiceModel.Description.ClientViaBehavior>
