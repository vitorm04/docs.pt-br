---
title: Método ICorProfilerCallback::ClassLoadFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadFinished
helpviewer_keywords:
- ClassLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ClassLoadFinished method [.NET Framework profiling]
ms.assetid: 3dd80fbe-d62d-4d4d-acf8-5b7d0efe607e
topic_type:
- apiref
ms.openlocfilehash: e0ff90f99c1127b5a4626f47514ba7099b5d48af
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866592"
---
# <a name="icorprofilercallbackclassloadfinished-method"></a>Método ICorProfilerCallback::ClassLoadFinished
Notifica o criador de perfil que a conclusão do carregamento de uma classe.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ClassLoadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a>Parâmetros

- `classId`

  \[em] identifica a classe que foi carregada.

- `hrStatus`

  \[em] um HRESULT que indica se a classe foi carregada com êxito.

## <a name="remarks"></a>Comentários  
 O valor de `classId` não é válido para uma solicitação de informações até que o método `ClassLoadFinished` seja chamado.  
  
 Algumas partes do carregamento da classe podem continuar após o retorno de chamada `ClassLoadFinished`. Uma falha HRESULT no `hrStatus` indica uma falha. No entanto, um HRESULT de êxito em `hrStatus` indica apenas que a primeira parte do carregamento da classe foi bem-sucedida.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerCallback](icorprofilercallback-interface.md)
- [Método ClassLoadStarted](icorprofilercallback-classloadstarted-method.md)
