---
title: Método ICorDebugDataTarget2::CreateVirtualUnwinder
ms.date: 03/30/2017
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c8befed8bc810344b2a3344212a6a4a854300e3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164652"
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
  
## <a name="parameters"></a>Parâmetros  
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
 `S_OK` Se for bem-sucedido. Qualquer outro `HRESULT` indica uma falha. Qualquer falha `HRESULT` recebida pelo mscordbi é considerada fatal e faz com que [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) métodos para retornar `CORDBG_E_DATA_TARGET_ERROR`.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Esse método só está disponível com o .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugDataTarget2](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
