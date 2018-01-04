---
title: "Método ICorProfilerCallback4::ReJITError"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4.ReJITError
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4::ReJITError
helpviewer_keywords:
- ReJITError method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITError method [.NET Framework profiling]
ms.assetid: d7888aa9-dfaa-420f-9f99-e06ab35ca482
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c746d0f7a6be96f95f1a051e22de0ad1bd2d2269
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback4rejiterror-method"></a>Método ICorProfilerCallback4::ReJITError
Notifica o criador de perfil que o compilador just-in-time (JIT) encontrou um erro no processo de recompilação.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `moduleID`  
 [in] O `ModuleID` no qual foi feita a tentativa de recompilação com falha.  
  
 `methodId`  
 [in] O `MethodDef` do método no qual foi feita a tentativa de recompilação com falha.  
  
 `functionId`  
 [in] A instância de função que está sendo recompilada ou marcada para recompilação. Esse valor pode ser `NULL` se a falha ocorreu em uma base por método em vez de uma base por instanciação (por exemplo, se o criador de perfil especificado um token de metadados inválido para o método a ser recompilado).  
  
 `hrStatus`  
 [in] Um HRESULT que indica a natureza da falha. Consulte a seção Status HRESULTS para obter uma lista de valores.  
  
## <a name="return-value"></a>Valor de retorno  
 Os valores retornados desse retorno de chamada são ignorados.  
  
## <a name="status-hresults"></a>Status HRESULTS  
  
|Matriz de status de HRESULT|Descrição|  
|--------------------------|-----------------|  
|E_INVALIDARG|O `moduleID` ou `methodDef` token é `NULL`.|  
|CORPROF_E_DATAINCOMPLETE|O módulo ainda não foi totalmente carregado ou ele está sendo descarregado.|  
|CORPROF_E_MODULE_IS_DYNAMIC|O módulo especificado foi gerado dinamicamente (por exemplo, `Reflection.Emit`) e, portanto, não é suportado por este método.|  
|CORPROF_E_FUNCTION_IS_COLLECTIBLE|O método é instanciado em um assembly de coleção e, portanto, não é capaz de ser recompilado. Observe que os tipos e funções definidas em um contexto de reflexão não (por exemplo, `List<MyCollectibleStruct>`) pode ser instanciado em um assembly de coleção.|  
|E_OUTOFMEMORY|O CLR ficou sem memória ao tentar marcar o método especificado para recompilação de JIT.|  
|Outros|O sistema operacional retornou uma falha de fora do controle do CLR. Por exemplo, se uma chamada do sistema para alterar a proteção de acesso de uma página de memória falhar, o erro do sistema operacional é exibido.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [Interface ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
