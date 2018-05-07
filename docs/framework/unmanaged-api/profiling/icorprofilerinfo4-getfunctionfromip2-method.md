---
title: Método ICorProfilerInfo4::GetFunctionFromIP2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetFunctionFromIP2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2
helpviewer_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2 method [.NET Framework profiling]
- GetFunctionFromIP2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 46ff70f4-13e9-40a0-802a-0a40abcfc6a0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c4fe3eec4940b57001b7734c581076388f8ba0c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a>Método ICorProfilerInfo4::GetFunctionFromIP2
Um ponteiro de instrução do código gerenciado é mapeado para a versão recompilada JIT de uma função.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ip`  
 [in] O ponteiro de instrução em código gerenciado.  
  
 `pFunctionId`  
 [out] A ID de função.  
  
 `pReJitId`  
 [out] A identidade da versão recompilada JIT da função.  
  
## <a name="remarks"></a>Comentários  
 `GetFunctionFromIP2` é semelhante ao `GetFunctionFromIP`, exceto que ele obtém a ID recompilado JIT em vez da ID de função da função que contém o endereço IP especificado.  
  
> [!NOTE]
>  `GetFunctionFromIP2` pode disparar uma coleta de lixo, enquanto `GetFunctionFromIP` não.  Para obter mais informações, consulte [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
