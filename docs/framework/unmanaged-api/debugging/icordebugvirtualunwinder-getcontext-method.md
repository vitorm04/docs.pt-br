---
title: "Método ICorDebugVirtualUnwinder::GetContext"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 45a914005e84d33b39d72fce96679e275b921d3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvirtualunwindergetcontext-method"></a>Método ICorDebugVirtualUnwinder::GetContext
Obtém o contexto atual deste unwinder.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `contextFlags`  
 [in] Sinalizadores que especificam quais partes do contexto para retornar (definido em Winnt. H).  
  
 `cbContextBuf`  
 [in] O número de bytes em `contextBuf`.  
  
 `contextSize`  
 [out] Um ponteiro para o número de bytes gravados `contextBuf`.  
  
 `contextBuf`  
 [out] Uma matriz de bytes que contém o contexto atual deste unwinder.  
  
## <a name="return-value"></a>Valor de retorno  
 Qualquer falha valor HRESULT recebida pelo mscordbi é considerado fatal e fará com que ICorDebug APIs retornar `CORDBG_E_DATA_TARGET_ERROR`.  
  
## <a name="remarks"></a>Comentários  
 Definir o valor inicial do `contextBuf` argumento para o buffer de contexto retornado ao chamar o [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) método.  
  
> [!NOTE]
>  Esse método só está disponível com o .NET Native.  
  
 Porque o desenrolamento pode apenas restaurar um subconjunto de registros, como não volátil registra somente, o contexto pode não corresponder exatamente o estado do registro no momento da chamada do método real.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [Interfaces de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
