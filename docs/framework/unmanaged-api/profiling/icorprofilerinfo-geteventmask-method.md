---
title: "Método ICorProfilerInfo::GetEventMask"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetEventMask
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetEventMask
helpviewer_keywords:
- GetEventMask method [.NET Framework profiling]
- ICorProfilerInfo::GetEventMask method [.NET Framework profiling]
ms.assetid: ec34cc13-45a3-4695-abc3-b3347d4e6fc2
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8757298819f5ca6a534a12cec0593aed05610042
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfogeteventmask-method"></a>Método ICorProfilerInfo::GetEventMask
Obtém as categorias de eventos atuais para as quais o criador de perfil deseja receber notificações de eventos para o Common Language Runtime (CLR).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetEventMask(  
    [out] DWORD *pdwEvents);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pdwEvents`  
 [out] Um ponteiro para um valor de 4 bytes que especifica as categorias de eventos. Cada bit controla uma capacidade, um comportamento ou um tipo de evento diferente. Os bits são descritos no [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeração.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Você deve chamar o [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) método em vez desse método. Embora o `SetEventMask` método continua a dar suporte, [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) fornece funcionalidade adicional.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)  
 [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
