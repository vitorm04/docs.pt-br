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
ms.openlocfilehash: d229b530062d759ab270612fa70b1799acbcadbe
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448074"
---
# <a name="icorprofilercallbackmoduleattachedtoassembly-method"></a>Método ICorProfilerCallback::ModuleAttachedToAssembly
Notifica o criador de perfil de que um módulo está sendo anexado a seu assembly pai.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ModuleAttachedToAssembly(  
    [in] ModuleID   moduleId,  
    [in] AssemblyID AssemblyId);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `moduleId`  
 no A ID do módulo que está sendo anexado.  
  
 `AssemblyId`  
 no A ID do assembly pai ao qual o módulo está anexado.  
  
## <a name="remarks"></a>Comentários  
 Um módulo pode ser carregado por meio de uma tabela de endereços de importação (IAT), por meio de uma chamada para `LoadLibrary`ou por meio de uma referência de metadados. Como resultado, o carregador de Common Language Runtime (CLR) tem vários caminhos de código para determinar o assembly no qual um módulo reside. Portanto, é possível que, após [ICorProfilerCallback:: ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) seja chamado, o módulo não saiba em qual assembly ele está e obter a ID do assembly pai não é possível. O método `ModuleAttachedToAssembly` é chamado quando o módulo é anexado a seu assembly pai e sua ID de assembly pai pode ser obtida.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
