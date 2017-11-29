---
title: Interface ICorProfilerFunctionControl
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerFunctionControl
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerFunctionControl
helpviewer_keywords: ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 4e3d3141-4662-4166-8f05-bc857c1b4216
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 09a0a839c9cd69c7926c19cceffc56ee928f2f02
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerfunctioncontrol-interface"></a>Interface ICorProfilerFunctionControl
Fornece métodos que permitem a um criador de perfis de código se comunicar com o tempo de execução de linguagem comum (CLR) para controlar como o compilador JIT deve gerar código ao recompilar um método específico.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md)|Define um ou mais sinalizadores do [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) função recompilação de enumeração para controlar a geração de código para um just-in-time (JIT).|  
|[Método SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilfunctionbody-method.md)|Substitui o corpo CIL (Common Intermediate Language) do método.|  
|[Método SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md)|Define um mapa de códigos para a função especificada usando as entradas de mapa Common Intermediate Language (CIL) especificadas.|  
  
## <a name="remarks"></a>Comentários  
 A interface de `ICorProfilerFunctionControl` fornece métodos para controlar a geração de código para uma única função recompilada. O criador de perfil obtém uma instância desta interface por meio de [Icorprofilercallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) retorno de chamada. Cada instância do `ICorProfilerFunctionControl` controla todas as instâncias de uma função.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Método EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)
