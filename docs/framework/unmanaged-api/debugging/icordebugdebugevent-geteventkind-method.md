---
title: Método ICorDebugDebugEvent::GetEventKind
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
ms.openlocfilehash: 0c67f8bdce49b4e9200b501aaf00ae293cced7d7
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783410"
---
# <a name="icordebugdebugeventgeteventkind-method"></a>Método ICorDebugDebugEvent::GetEventKind
Indica o tipo de evento que este objeto `ICorDebugDebugEvent` representa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 pDebugEventKind  
 Um ponteiro para um membro de enumeração [CorDebugDebugEventKind](cordebugdebugeventkind-enumeration.md) que indica o tipo de evento.  
  
## <a name="remarks"></a>Comentários  
 Com base no valor de `pDebugEventKind`, você pode chamar `QueryInterface` para obter uma interface de evento de depuração mais precisa com dados adicionais.  
  
> [!NOTE]
> Esse método está disponível somente com .NET Native.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugDebugEvent](icordebugdebugevent-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
