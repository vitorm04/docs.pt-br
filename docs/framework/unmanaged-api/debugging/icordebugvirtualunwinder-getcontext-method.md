---
title: 'Método ICorDebugVirtualUnwinder:: GetContext'
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
ms.openlocfilehash: e203db78b40bf4305316046cfcd679f3d10d1876
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396443"
---
# <a name="icordebugvirtualunwindergetcontext-method"></a>Método ICorDebugVirtualUnwinder:: GetContext
Obtém o contexto atual deste desenrolador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `contextFlags`  
 no Sinalizadores que especificam quais partes do contexto retornar (definido em WinNT. h).  
  
 `cbContextBuf`  
 no O número de bytes em `contextBuf` .  
  
 `contextSize`  
 fora Um ponteiro para o número de bytes realmente gravados no `contextBuf` .  
  
 `contextBuf`  
 fora Uma matriz de bytes que contém o contexto atual deste desenrolador.  
  
## <a name="return-value"></a>Valor retornado  
 Qualquer valor HRESULT com falha recebido por MSCorDbi é considerado fatal e fará com que as APIs do ICorDebug sejam retornadas `CORDBG_E_DATA_TARGET_ERROR` .  
  
## <a name="remarks"></a>Comentários  
 Você define o valor inicial do `contextBuf` argumento para o buffer de contexto retornado chamando o método [ICorDebugStackWalk:: GetContext](icordebugstackwalk-getcontext-method.md) .  
  
> [!NOTE]
> Esse método está disponível somente com .NET Native.  
  
 Como o desenrolamento só pode restaurar um subconjunto dos registros, como somente os registros não voláteis, o contexto pode não corresponder exatamente ao estado de registro no momento da chamada de método real.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
