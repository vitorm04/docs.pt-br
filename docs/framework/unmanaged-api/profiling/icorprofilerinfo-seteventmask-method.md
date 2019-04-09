---
title: Método ICorProfilerInfo::SetEventMask
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetEventMask
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetEventMask
helpviewer_keywords:
- ICorProfilerInfo::SetEventMask method [.NET Framework profiling]
- SetEventMask method [.NET Framework profiling]
ms.assetid: 44bc0f56-32fa-491e-a62d-52fc96d48125
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 122a621552b49f476f219216ac0a52011c1542ec
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103942"
---
# <a name="icorprofilerinfoseteventmask-method"></a>Método ICorProfilerInfo::SetEventMask
Determina um valor que especifica os tipos de eventos dos quais o perfil deseja receber notificação do CLR (Common Language Runtime).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetEventMask(  
    [in] DWORD dwEvents);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `dwEvents`  
 [in] Um valor de 4 bytes que especifica as categorias de eventos. Cada bit controla uma capacidade, um comportamento ou um tipo de evento diferente. Os bits são descritos na [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeração.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Você deve chamar o [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) em vez deste método. Embora o `SetEventMask` método continua a ter suporte, [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) fornece funcionalidade adicional.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Método SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
