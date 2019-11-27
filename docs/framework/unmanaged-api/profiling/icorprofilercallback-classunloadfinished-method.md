---
title: Método ICorProfilerCallback::ClassUnloadFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadFinished
helpviewer_keywords:
- ICorProfilerCallback::ClassUnloadFinished method [.NET Framework profiling]
- ClassUnloadFinished method [.NET Framework profiling]
ms.assetid: 55674b68-678a-4747-ae06-4e91519c7305
topic_type:
- apiref
ms.openlocfilehash: b78d604a28ffe01000a763f7e0dd3c1630e2c186
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435917"
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a>Método ICorProfilerCallback::ClassUnloadFinished
Notifica o criador de perfil de que uma classe concluiu o descarregamento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `classId`  
 no Identifica a classe que foi descarregada.  
  
 `hrStatus`  
 no Um HRESULT que indica se a classe foi descarregada com êxito.  
  
## <a name="remarks"></a>Comentários  
 Algumas partes do descarregamento da classe podem continuar após o retorno de chamada `ClassUnloadFinished`. Uma falha HRESULT no `hrStatus` indica uma falha. No entanto, um HRESULT de êxito em `hrStatus` indica apenas que a primeira parte do descarregamento da classe foi bem-sucedida.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Método ClassUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)
