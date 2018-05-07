---
title: Interface ICLRGCManager
ms.date: 03/30/2017
api_name:
- ICLRGCManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager
helpviewer_keywords:
- ICLRGCManager interface [.NET Framework hosting]
ms.assetid: fb511c9b-3fe4-41b0-822a-6ba4a079d1f5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 045b924033630ea98d5a532a62f1037a5972df90
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="iclrgcmanager-interface"></a>Interface ICLRGCManager
Fornece métodos que permitem que um host interagir com o sistema de coleta de lixo do common language runtime.  
  
> [!NOTE]
>  Começando com o [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], você pode usar o [Iclrgcmanager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) método para definir o tamanho de um segmento de coleta de lixo e o tamanho máximo da geração do sistema de coleta de lixo 0 como valores maiores que o `DWORD` limite imposto pelo [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) método.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Collect](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-collect-method.md)|Força uma coleta de lixo para a geração especificada.|  
|[Método GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)|Obtém um conjunto de estatísticas atuais sobre o sistema de coleta de lixo.|  
|[Método SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md)|Define o tamanho de um segmento de coleta de lixo e o tamanho máximo da geração do sistema de coleta de lixo 0.|  
  
## <a name="remarks"></a>Comentários  
 O common language runtime (CLR) implementa seu mecanismo de coleta de lixo com gerenciado <xref:System.GC> tipo. Para obter mais informações sobre o sistema de coleta de lixo, consulte [coleta de lixo](../../../../docs/standard/garbage-collection/index.md).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Gerenciamento Automático de Memória](../../../../docs/standard/automatic-memory-management.md)  
 [Estrutura COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [Interface ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [Interfaces de hospedagem CLR](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md)
