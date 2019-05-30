---
title: Interface IGCHost
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 167e2477e5185112408793e145bc5a4fabea7fc8
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66377625"
---
# <a name="igchost-interface"></a>Interface IGCHost
Fornece métodos para obter informações sobre o sistema de coleta de lixo e para controlar alguns aspectos da coleta de lixo.  
  
> [!NOTE]
>  Começando com o .NET Framework 4.5, você pode usar o [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) método para definir o tamanho de um segmento de coleta de lixo e o tamanho máximo da geração do sistema de coleta de lixo 0 para valores maior que o `DWORD` limite imposto pelo [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md) método.  
  
> [!NOTE]
>  Essa interface é somente ao especialista em uso. Isso pode afetar o desempenho de um aplicativo se usado incorretamente.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Collect](../../../../docs/framework/unmanaged-api/hosting/igchost-collect-method.md)|Força uma coleta ocorrer para a geração de determinado, independentemente do estado da coleta de lixo atual.|  
|[Método GetStats](../../../../docs/framework/unmanaged-api/hosting/igchost-getstats-method.md)|Obtém as estatísticas para o estado atual do sistema de coleta de lixo.|  
|[Método GetThreadStats](../../../../docs/framework/unmanaged-api/hosting/igchost-getthreadstats-method.md)|Obtém as estatísticas por thread para coleta de lixo.|  
|[Método SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md)|Define o tamanho do segmento e o tamanho máximo para a geração 0.|  
|[Método SetVirtualMemLimit](../../../../docs/framework/unmanaged-api/hosting/igchost-setvirtualmemlimit-method.md)|Define o tamanho máximo de memória de virtual do tempo de execução.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** GCHost.idl, GCHost.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Coclass CorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
