---
title: '&lt;tempos limite&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 41ebd88f64b001b577342562c9c3010b307aaccc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="lttimeoutsgt"></a>&lt;tempos limite&gt;
Representa um elemento de configuração que especifica o intervalo de tempo permitido para o host de serviço abrir ou fechar.  
  
 \<sistema. ServiceModel >  
\<cliente >  
\<ponto de extremidade >  
\<host >  
\<tempos limite >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<timeOuts closeTimeout="TimeSpan"  
   openTimeout="TimeSpan" >  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`closeTimeout`|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo permitido para o host de serviço fechar.|  
|`openTimeout`|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo permitido para o host de serviço abrir.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<host >](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|Um elemento de configuração que especifica as configurações para um host de serviço.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [Hospedagem](../../../../../docs/framework/wcf/feature-details/hosting.md)
