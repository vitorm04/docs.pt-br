---
title: Enumeração EMemoryAvailable
ms.date: 03/30/2017
api_name:
- EMemoryAvailable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryAvailable
helpviewer_keywords:
- EMemoryAvailable enumeration [.NET Framework hosting]
ms.assetid: 38e72a06-dbed-473b-a59b-7e0b3ea4f2af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 139cf540617e278eeaae8a2a5acf10dd797d5d10
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429880"
---
# <a name="ememoryavailable-enumeration"></a>Enumeração EMemoryAvailable
Contém valores que indicam a quantidade de memória física livre no computador. Esses valores mapeiam logicamente para os eventos de alta e baixa memória retornado do `CreateMemoryResourceNotification` função na API do Win32.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3   
} EMemoryAvailable;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|Muita memória física está disponível.|  
|`eMemoryAvailableLow`|Há muito pouca memória física.|  
|`eMemoryAvailableNeutral`|A memória física disponível é neutra.|  
  
## <a name="remarks"></a>Comentários  
 Esse valor é passado pelo host para o common language runtime (CLR), usando uma chamada para o [Iclrmemorynotificationcallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
