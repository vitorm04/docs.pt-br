---
title: "Método ICorDebugDataTarget2::CreateVirtualUnwinder"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bffbf95fc38cba6f311e0641b35e2696bd34099
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a>Método ICorDebugDataTarget2::CreateVirtualUnwinder
Cria um novo unwinder de pilha que inicia o desenrolamento de um contexto inicial (que não é necessariamente folha de um thread).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CreateVirtualUnwinder(  
    [in] DWORD nativeThreadID,  
    [in] ULONG32 contextFlags,  
    [in] ULONG32 cbContext,  
    [in, size_is(cbContext)] BYTE initialContext[],  
    [out] ICorDebugVirtualUnwinder ** ppUnwinder);  
};  
```  
  
#### <a name="parameters"></a>Parâmetros  
 nativeThreadID  
 [in] O ID de thread nativo do thread cuja pilha será desenrolada.  
  
 contextFlags  
 [in] Sinalizadores que especificam quais partes do contexto são definidos em `initialContext`.  
  
 cbContext  
 [in] O tamanho do `initialContext`.  
  
 initialContext  
 [in] Os dados no contexto.  
  
 ppUnwinder  
 [out] Um ponteiro para o endereço de um objeto de interface ICorDebugVirtualUnwinder.  
  
## <a name="return-value"></a>Valor de retorno  
 `S_OK` se bem-sucedido. Qualquer outro `HRESULT` indica uma falha. Qualquer falha `HRESULT` recebidas pelo mscordbi é considerado fatal e faz com que [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) métodos para retornar `CORDBG_E_DATA_TARGET_ERROR`.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Esse método só está disponível com o .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugDataTarget2](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
