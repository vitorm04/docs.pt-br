---
title: Método ICorDebugVirtualUnwinder::GetContext
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3125fd5081e68237714bcb10f760b73ce7509f6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119217"
---
# <a name="icordebugvirtualunwindergetcontext-method"></a>Método ICorDebugVirtualUnwinder::GetContext
Obtém o contexto atual deste desenrolador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `contextFlags`  
 [in] Sinalizadores que especificam quais partes do contexto para retornar (definidos em Winnt. H).  
  
 `cbContextBuf`  
 [in] O número de bytes em `contextBuf`.  
  
 `contextSize`  
 [out] Um ponteiro para o número de bytes realmente gravados `contextBuf`.  
  
 `contextBuf`  
 [out] Uma matriz de bytes que contém o contexto atual deste desenrolador.  
  
## <a name="return-value"></a>Valor de retorno  
 Qualquer valor HRESULT recebida pelo mscordbi com falha é considerada fatal e fará com que as APIs de ICorDebug retornar `CORDBG_E_DATA_TARGET_ERROR`.  
  
## <a name="remarks"></a>Comentários  
 Você define o valor inicial do `contextBuf` argumento para o buffer de contexto retornado ao chamar o [icordebugstackwalk:: GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) método.  
  
> [!NOTE]
>  Esse método só está disponível com o .NET Native.  
  
 Porque desenrolamento maio apenas restaurar um subconjunto de registros, como não-volátil registra somente, o contexto pode não coincidir com o estado de registro no momento da chamada do método real.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
