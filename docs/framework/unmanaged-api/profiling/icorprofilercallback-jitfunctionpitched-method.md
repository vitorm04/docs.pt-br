---
title: Método ICorProfilerCallback::JITFunctionPitched
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITFunctionPitched
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITFunctionPitched
helpviewer_keywords:
- JITFunctionPitched method [.NET Framework profiling]
- ICorProfilerCallback::JITFunctionPitched method [.NET Framework profiling]
ms.assetid: 116085df-7a77-404a-afac-d0557a12b986
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c8aa46e869d50fc7aa65c1d4244ad4ff71657bad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62042023"
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a>Método ICorProfilerCallback::JITFunctionPitched
Notifica o criador de perfil que uma função que tenha sido just-in-time (JIT)-compilado foi removido da memória.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `functionId`  
 [in] A ID da função que foi removida.  
  
## <a name="remarks"></a>Comentários  
 Se a função removida for chamada, o criador de perfil receberá novos eventos de compilação JIT quando a função é recompilada. Atualmente, o compilador JIT do common language runtime (CLR) não remove funções de memória, para que esse retorno de chamada não é usado atualmente e não será recebido pelo criador de perfil.  
  
 O valor de `functionId` não é válida até que a função seja recompilada. Quando a função é recompilada, os mesmos `functionId` valor será usado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
