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
ms.openlocfilehash: 55463985a7ac93bf0ec3cda92f91f8a326f92406
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410557"
---
# <a name="ememoryavailable-enumeration"></a>Enumeração EMemoryAvailable
Contém valores que indicam a quantidade de memória física livre no computador. Esses valores são mapeados logicamente para os eventos de alta e baixa memória retornado do `CreateMemoryResourceNotification` função na API do Windows.  
  
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
|`eMemoryAvailableLow`|Muito pouca memória física está disponível.|  
|`eMemoryAvailableNeutral`|A memória física disponível é neutra.|  
  
## <a name="remarks"></a>Comentários  
 Esse valor é passado pelo host para o common language runtime (CLR) pelo uso de uma chamada para o [iclrmemorynotificationcallback:: Onmemorynotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Enumerações de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
