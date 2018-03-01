---
title: Interface IGCHost
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IGCHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost
helpviewer_keywords:
- IGCHost interface [.NET Framework hosting]
ms.assetid: 9ad70ffd-6963-4ab2-8c84-3d86c3fb8deb
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 77a2cab35785aa39571d39bdd369fa26cdbcd1d2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="igchost-interface"></a>Interface IGCHost
Fornece métodos para obter informações sobre o sistema de coleta de lixo e para controlar alguns aspectos da coleta de lixo.  
  
> [!NOTE]
>  Começando com o [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], você pode usar o [Igchost2](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) método para definir o tamanho de um segmento de coleta de lixo e o tamanho máximo da geração do sistema de coleta de lixo 0 como valores maiores que o `DWORD` limite imposto pelo [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md) método.  
  
> [!NOTE]
>  Esta interface é somente ao uso especializado. Se usado incorretamente, isso poderá afetar o desempenho de um aplicativo.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Collect](../../../../docs/framework/unmanaged-api/hosting/igchost-collect-method.md)|Força uma coleta ocorra para determinada geração, independentemente do estado da coleção atual de lixo.|  
|[Método GetStats](../../../../docs/framework/unmanaged-api/hosting/igchost-getstats-method.md)|Obtém as estatísticas para o estado atual do sistema de coleta de lixo.|  
|[Método GetThreadStats](../../../../docs/framework/unmanaged-api/hosting/igchost-getthreadstats-method.md)|Obtém as estatísticas por thread de coleta de lixo.|  
|[Método SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md)|Define o tamanho do segmento e o tamanho máximo de geração 0.|  
|[Método SetVirtualMemLimit](../../../../docs/framework/unmanaged-api/hosting/igchost-setvirtualmemlimit-method.md)|Define o tamanho máximo de memória virtual do tempo de execução.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** GCHost.idl, GCHost.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Coclass CorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
