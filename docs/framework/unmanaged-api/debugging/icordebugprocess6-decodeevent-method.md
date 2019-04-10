---
title: Método ICorDebugProcess6::DecodeEvent
ms.date: 03/30/2017
ms.assetid: 1453bc0c-6e0d-4d5a-b176-22607f8a3e6c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a392e236f180771a9b05526a0db569f27f6f7d8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230740"
---
# <a name="icordebugprocess6decodeevent-method"></a>Método ICorDebugProcess6::DecodeEvent
Decodifica eventos de depuração gerenciados que foram encapsulados na carga de eventos de depuração de exceção nativo especialmente criado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
 [in] Um [CorDebugRecordFormat](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md) membro de enumeração que especifica o formato do evento depuração não gerenciada.  
  
 `dwFlags`  
 [in] Um campo de bits que depende da arquitetura de destino e que especifica informações adicionais sobre o evento de depuração. Para sistemas Windows, ele pode ser um membro do [CorDebugDecodeEventFlagsWindows](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md) enumeração.  
  
 `dwThreadId`  
 [in] O identificador de sistema operacional do thread em que a exceção foi gerada.  
  
 `ppEvent`  
 [out] Um ponteiro para o endereço de um [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) objeto que representa um evento de depuração gerenciado decodificado.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Esse método só está disponível com o .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugProcess6](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
