---
title: Método ICorProfilerCallback::ExceptionCatcherEnter
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCatcherEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter method [.NET Framework profiling]
- ExceptionCatcherEnter method [.NET Framework profiling]
ms.assetid: 41462329-a648-46f0-ae6d-728b94c31aa9
topic_type:
- apiref
ms.openlocfilehash: 534e0672820cc2509f32765274ad970fda69ec5d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866501"
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a>Método ICorProfilerCallback::ExceptionCatcherEnter
Notifica o criador de perfil que o controle está sendo passado para o bloco de `catch` apropriado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
## <a name="parameters"></a>Parâmetros

- `functionId`

  \[em] o identificador da função que contém o bloco de `catch`.
  
- `objectId`

  \[em] o identificador da exceção que está sendo manipulada.

## <a name="remarks"></a>Comentários  
 O método `ExceptionCatcherEnter` será chamado somente se o ponto de captura estiver no código compilado com o compilador JIT (just-in-time). Uma exceção que é capturada no código não gerenciado ou no código interno do tempo de execução não chamará essa notificação. O valor de `objectId` é passado novamente, pois uma coleta de lixo pode ter movido o objeto desde a notificação de `ExceptionThrown`.  
  
 O criador de perfil não deve bloquear em sua implementação desse método porque a pilha pode não estar em um estado que permita a coleta de lixo e, portanto, a coleta de lixo preemptiva não pode ser habilitada. Se o criador de perfil for bloqueado aqui e a coleta de lixo for tentada, o tempo de execução será bloqueado até que esse retorno de chamada seja retornado.  
  
 A implementação do criador de perfil desse método não deve chamar o código gerenciado ou, de qualquer forma, causar uma alocação de memória gerenciada.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerCallback](icorprofilercallback-interface.md)
- [Método ExceptionCatcherLeave](icorprofilercallback-exceptioncatcherleave-method.md)
