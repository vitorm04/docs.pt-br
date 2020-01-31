---
title: Método ICorProfilerThreadEnum::Skip
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Skip
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Skip method [.NET Framework profiling]
ms.assetid: acb8b029-4a96-4ed7-ae3c-310204e5ceea
topic_type:
- apiref
ms.openlocfilehash: b08a501f7d55fbb193afd8c297ca7725348dac76
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76860899"
---
# <a name="icorprofilerthreadenumskip-method"></a>Método ICorProfilerThreadEnum::Skip
Avança o cursor do enumerador de sua posição atual para ignorar o número especificado de elementos.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `celt`  
 no O número de elementos a serem ignorados.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`celt` elementos foram ignorados.|  
|S_FALSE|Menos de `celt` elementos foram ignorados, o que indica que não há mais elementos.|  
  
## <a name="remarks"></a>Comentários  
 A nova posição do cursor deste enumerador é (posição atual) + `celt`.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md)
- [Interfaces de criação de perfil](profiling-interfaces.md)
