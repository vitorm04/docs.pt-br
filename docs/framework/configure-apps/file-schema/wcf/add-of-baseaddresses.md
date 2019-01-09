---
title: '&lt;adicionar&gt; &lt;baseAddresses&gt;'
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: ce476c2d40758cf52eada813873d061d0e441bce
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149079"
---
# <a name="ltaddgt-of-ltbaseaddressesgt"></a>&lt;adicionar&gt; &lt;baseAddresses&gt;
Representa um elemento de configuração que especifica os endereços base usados pelo host de serviço.  
  
 \<system.ServiceModel>  
\<client>  
\<endpoint>  
\<host >  
\<baseAddresses >  
\<baseAddress >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a>Tipo  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`baseAddress`|Uma cadeia de caracteres que especifica um endereço base usado pelo host de serviço.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<baseAddresses >](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|Uma coleção de elementos `baseAddress`.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [Hospedagem](../../../../../docs/framework/wcf/feature-details/hosting.md)
