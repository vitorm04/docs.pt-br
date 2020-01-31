---
title: 'Método ICorDebugVirtualUnwinder:: GetContext'
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
ms.openlocfilehash: ff5e5bdd66ec44a0931b51212f07485718507576
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790841"
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
 no O número de bytes em `contextBuf`.  
  
 `contextSize`  
 fora Um ponteiro para o número de bytes realmente gravados em `contextBuf`.  
  
 `contextBuf`  
 fora Uma matriz de bytes que contém o contexto atual deste desenrolador.  
  
## <a name="return-value"></a>Valor de retorno  
 Qualquer valor HRESULT com falha recebido por MSCorDbi é considerado fatal e fará com que as APIs do ICorDebug retornem `CORDBG_E_DATA_TARGET_ERROR`.  
  
## <a name="remarks"></a>Comentários  
 Você define o valor inicial do argumento `contextBuf` para o buffer de contexto retornado chamando o método [ICorDebugStackWalk:: GetContext](icordebugstackwalk-getcontext-method.md) .  
  
> [!NOTE]
> Esse método está disponível somente com .NET Native.  
  
 Como o desenrolamento só pode restaurar um subconjunto dos registros, como somente os registros não voláteis, o contexto pode não corresponder exatamente ao estado de registro no momento da chamada de método real.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
