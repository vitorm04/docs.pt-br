---
title: '&lt;host&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bded8d718259bf4fc84bfe790db069a77fc2a703
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="lthostgt"></a>&lt;host&gt;
Especifica configurações para um host de serviço.  
  
 \<sistema. ServiceModel >  
\<Serviços >  
\<serviço >  
\<host >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<host>  
      <baseAddresses>  
         <baseAddress baseAddress="string" />  
      </baseAddresses>  
      <timeOuts closeTimeout="TimeSpan"  
         openTimeout="TimeSpan" >  
</host>  
```  
  
## <a name="type"></a>Tipo  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<baseAddresses >](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|Uma coleção de `baseAddress` elementos que especifica os endereços base usados pelo host de serviço.|  
|[\<tempos limite >](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|Um elemento de configuração que especifica o intervalo de tempo permitido para o host de serviço abrir ou fechar.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<serviço >](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|Especifica as configurações para um [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] serviço.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [Hospedagem](../../../../../docs/framework/wcf/feature-details/hosting.md)
