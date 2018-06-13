---
title: Método ICorProfilerFunctionControl::SetCodegenFlags
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetCodegenFlags
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags
helpviewer_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags method [.NET Framework profiling]
- SetCodegenFlags method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: a2d5daa5-b990-4ae5-bf2a-c0862fe58bd7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 43c32d1ce4f804da8980dc0c566a77e5b076661b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459607"
---
# <a name="icorprofilerfunctioncontrolsetcodegenflags-method"></a>Método ICorProfilerFunctionControl::SetCodegenFlags
Define um ou mais sinalizadores do [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) função recompilação de enumeração para controlar a geração de código para um just-in-time (JIT).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetCodegenFlags(  
    [in] DWORD flags);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `flags`  
 [in] Um ou mais sinalizadores do [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) enumeração.  
  
## <a name="remarks"></a>Comentários  
 O criador de perfil obtém uma instância desta interface por meio de [Icorprofilercallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) retorno de chamada. `SetCodegenFlags` permite que o criador de perfil controlar a geração de código para a função recompilada. Assim como acontece com todos os outros parâmetros de recompilação JIT, os sinalizadores de geração de código se aplicam a todas as instâncias da função.  
  
 O compilador JIT considera esses sinalizadores de compilação, juntamente com outros sinalizadores especificados por outras fontes, durante a compilação de uma função.  Outras fontes incluem o depurador, sinalizadores globais definidas pelo criador de perfil na inicialização, usando o [: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) método (com os valores `COR_PRF_DISABLE_INLINING` e `COR_PRF_DISABLE_OPTIMIZATIONS`) e o criador de perfil [ : Jitinlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) retorno de chamada.  O compilador JIT dá prioridade a uma fonte que solicita o mínimo de otimização.  Por exemplo, se o criador de perfil especifica `COR_PRF_DISABLE_INLINING` na inicialização, mas não especifica `COR_PRF_CODEGEN_DISABLE_INLINING` no [: Setcodegenflags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) retorno de chamada, inlining ainda está desabilitado.  Da mesma forma, se o criador de perfil não especificar `COR_PRF_CODEGEN_DISABLE_INLINING` na `SetCodegenFlags`, mas, em seguida, desabilita inlining usando o [: Jitinlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) retorno de chamada, inlining está desabilitado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
