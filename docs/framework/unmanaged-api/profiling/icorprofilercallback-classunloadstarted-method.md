---
title: Método ICorProfilerCallback::ClassUnloadStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadStarted
helpviewer_keywords:
- ClassUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ClassUnloadStarted method [.NET Framework profiling]
ms.assetid: bc93bead-f3a9-415c-b919-ddd3ca80facc
topic_type:
- apiref
ms.openlocfilehash: 3b729d3be84571a48cc9a770d7f06b99723c0d1f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445071"
---
# <a name="icorprofilercallbackclassunloadstarted-method"></a>Método ICorProfilerCallback::ClassUnloadStarted
Notifica o criador de perfil de que uma classe está sendo descarregada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ClassUnloadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `classId`  
 no Identifica a classe que está sendo descarregada.  
  
## <a name="remarks"></a>Comentários  
 O valor de `classId` não é válido para uma solicitação de informações após o retorno do método `ClassUnloadStarted` — essa é a última chance do criador de perfil obter informações sobre essa classe.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Método ClassUnloadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadfinished-method.md)
