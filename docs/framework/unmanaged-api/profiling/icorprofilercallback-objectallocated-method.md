---
title: Método ICorProfilerCallback::ObjectAllocated
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectAllocated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectAllocated
helpviewer_keywords:
- ObjectAllocated method [.NET Framework profiling]
- ICorProfilerCallback::ObjectAllocated method [.NET Framework profiling]
ms.assetid: eb412622-77cc-4abd-a2cd-c910fe8edd54
topic_type:
- apiref
ms.openlocfilehash: 38d9e83e9fa0e9cd0586fb10a6fd79c29bead4a6
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866098"
---
# <a name="icorprofilercallbackobjectallocated-method"></a>Método ICorProfilerCallback::ObjectAllocated
Notifica o criador de perfil de que a memória dentro do heap foi alocada para um objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `objectId`  
 no A ID do objeto para o qual a memória foi alocada.  
  
 `classId`  
 no A ID da classe da qual o objeto é uma instância.  
  
## <a name="remarks"></a>Comentários  
 O método `ObjectedAllocated` não é chamado para alocações a partir da pilha ou da memória não gerenciada. O parâmetro `classId` pode se referir a uma classe no código gerenciado que ainda não foi carregado. O criador de perfil receberá um retorno de chamada de carga de classe para essa classe imediatamente após o retorno de chamada `ObjectAllocated`.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerCallback](icorprofilercallback-interface.md)
- [Método ClassLoadStarted](icorprofilercallback-classloadstarted-method.md)
- [Método ClassLoadFinished](icorprofilercallback-classloadfinished-method.md)
