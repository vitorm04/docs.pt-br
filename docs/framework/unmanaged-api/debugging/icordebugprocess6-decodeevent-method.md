---
title: Método ICorDebugProcess6::DecodeEvent
ms.date: 03/30/2017
ms.assetid: 1453bc0c-6e0d-4d5a-b176-22607f8a3e6c
ms.openlocfilehash: be30b1ff79c2aceb97eb4ad42052da7dd162f5d3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792279"
---
# <a name="icordebugprocess6decodeevent-method"></a>Método ICorDebugProcess6::DecodeEvent
Decodifica eventos de depuração gerenciados que foram encapsulados na carga de eventos de depuração de exceção nativo especialmente criado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DecodeEvent(  
        [in, length_is(countBytes), size_is(countBytes)]  const BYTE pRecord[],  
        [in] DWORD countBytes,  
        [in] CorDebugRecordFormat format,  
        [in] DWORD dwFlags,   
        [in] DWORD dwThreadId,   
        [out] ICorDebugDebugEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pRecord`  
 [in] Um ponteiro para uma matriz de bytes de um evento de depuração de exceção nativo que inclui informações sobre um evento de depuração gerenciado.  
  
 `countBytes`  
 [in] O número de elementos nas matrizes de byte `pRecord`.  
  
 `format`  
 no Um membro de enumeração [CorDebugRecordFormat](cordebugrecordformat-enumeration.md) que especifica o formato do evento de depuração não gerenciado.  
  
 `dwFlags`  
 [in] Um campo de bits que depende da arquitetura de destino e que especifica informações adicionais sobre o evento de depuração. Para sistemas Windows, ele pode ser membro da enumeração [CorDebugDecodeEventFlagsWindows](cordebugdecodeeventflagswindows-enumeration.md) .  
  
 `dwThreadId`  
 [in] O identificador de sistema operacional do thread em que a exceção foi gerada.  
  
 `ppEvent`  
 fora Um ponteiro para o endereço de um objeto [ICorDebugDebugEvent](icordebugdebugevent-interface.md) que representa um evento de depuração gerenciado decodificado.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Esse método está disponível somente com .NET Native.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugProcess6](icordebugprocess6-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
