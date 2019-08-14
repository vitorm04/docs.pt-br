---
title: ICorProfilerInfo8::GetFunctionFromIP3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetFunctionFromIP3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: f3c0a3525c87fbf39199c15a6619ff4a0d2acc42
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973846"
---
# <a name="icorprofilerinfo8getfunctionfromip3-method"></a>Método ICorProfilerInfo8:: GetFunctionFromIP3
  
  Mapeia um ponteiro de instrução de código gerenciado para uma FunctionID. Esse método funciona para métodos dinâmicos e não dinâmicos.    
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetFunctionFromIP3([in] LPCBYTE ip,
                           [out] FunctionID *functionId,
                           [out] ReJITID * pReJitId);
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ip`  
 no O ponteiro de instrução no código gerenciado.  

 `pFunctionId`  
 fora A ID da função.  
  
 `pReJitId`  
 fora A identidade da versão recompilada do JIT da função.  
  
## <a name="remarks"></a>Comentários  
 Esse método funciona para métodos dinâmicos e não dinâmicos. É um superconjunto de [GetFunctionFromIP2](icorprofilerinfo4-getfunctionfromip2-method.md), que funciona apenas para funções com metadados.
  

## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca** CorGuids.lib  
  
 **.NET Framework versões:** [! INCLUIR[net_current_v472plus](../../../../includes/net-current-v472plus.md)  
  
## <a name="see-also"></a>Consulte também
- [Interface ICorProfilerInfo8](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)

