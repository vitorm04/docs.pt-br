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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: af6aab2483f0e92dc20936fe2b01e12590d99ca7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455364"
---
# <a name="icorprofilerthreadenumskip-method"></a>Método ICorProfilerThreadEnum::Skip
Avança o cursor do enumerador de sua posição atual para ignorar o número especificado de elementos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `celt`  
 [in] O número de elementos seja ignorada.  
  
## <a name="return-value"></a>Valor de retorno  
 Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`celt` elementos foram ignorados.|  
|S_FALSE|Menos de `celt` elementos foram ignorados, que indica que não existem mais elementos.|  
  
## <a name="remarks"></a>Comentários  
 A nova posição do cursor deste enumerador é (posição atual) + `celt`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
