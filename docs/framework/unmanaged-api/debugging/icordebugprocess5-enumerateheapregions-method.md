---
title: Método ICorDebugProcess5::EnumerateHeapRegions
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHeapRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeapRegions
helpviewer_keywords:
- EnumerateHeapRegions method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeapRegions method [.NET Framework debugging]
ms.assetid: b1edba68-9c36-4f69-be9f-678ce0b33480
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d48d8e7b699f411ec45cf1b5d9810c23583b045e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocess5enumerateheapregions-method"></a>Método ICorDebugProcess5::EnumerateHeapRegions
Obtém um enumerador para os intervalos de memória de heap gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EnumerateHeapRegions(  
   [out] ICorDebugHeapSegmentEnum **ppRegions  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppRegions`  
 [out] Um ponteiro para o endereço de um [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) objeto de interface que é um enumerador para os intervalos de memória na qual os objetos residem no heap gerenciado.  
  
## <a name="remarks"></a>Comentários  
 Antes de chamar o `ICorDebugProcess5::EnumerateHeapRegions` método, você deve chamar o [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) método e examinar o valor da `areGCStructuresValid` campo retornado [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) objeto para garantir que o heap de coleta de lixo em seu estado atual é enumerável. Além disso, o `ICorDebugProcess5::EnumerateHeapRegions` método retorna `E_FAIL` se anexar muito cedo no tempo de vida do processo, antes de memória regiões são criadas.  
  
 Esse método é garantido para enumerar todas as regiões de memória que podem conter objetos gerenciados, mas não garante que os objetos gerenciados, na verdade, residam nessas regiões. O [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) objeto da coleção pode incluir regiões de memória reservada ou vazio.  
  
 O [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) objeto de interface é um enumerador padrão derivado da interface ICorDebugEnum que permite que você enumere [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) objetos. Cada [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) objeto fornece informações sobre o intervalo de memória de um segmento específico, juntamente com a geração dos objetos nesse segmento.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugProcess5](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
