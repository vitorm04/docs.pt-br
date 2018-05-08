---
title: Método ICorProfilerCallback::ModuleAttachedToAssembly
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleAttachedToAssembly
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly
helpviewer_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly method [.NET Framework profiling]
- ModuleAttachedToAssembly method [.NET Framework profiling]
ms.assetid: b595798a-5d40-4cac-ab4f-911c61d2c5d2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e6b5281e30c48471131fa12e5106f7d0a6826e1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackmoduleattachedtoassembly-method"></a>Método ICorProfilerCallback::ModuleAttachedToAssembly
Notifica o criador de perfil que um módulo está sendo anexado ao seu assembly pai.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ModuleAttachedToAssembly(  
    [in] ModuleID   moduleId,  
    [in] AssemblyID AssemblyId);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `moduleId`  
 [in] A ID do módulo que está sendo anexado.  
  
 `AssemblyId`  
 [in] A ID do assembly pai ao qual o módulo está anexado.  
  
## <a name="remarks"></a>Comentários  
 Um módulo pode ser carregado por meio de uma tabela de endereço de importação (IAT), por meio de uma chamada para `LoadLibrary`, ou por meio de uma referência de metadados. Como resultado, o carregador de runtime (CLR) de linguagem comum tem vários caminhos de código para determinar o assembly no qual existe um módulo. Portanto, é possível que, depois [: Moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) é chamado, o módulo não sabe qual assembly está em e não é possível obter a ID do assembly pai. O `ModuleAttachedToAssembly` método é chamado quando o módulo está conectado ao seu assembly de pai e seu pai ID pode ser obtido.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
