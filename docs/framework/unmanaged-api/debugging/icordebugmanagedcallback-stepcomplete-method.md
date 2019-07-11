---
title: Método ICorDebugManagedCallback::StepComplete
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.StepComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::StepComplete
helpviewer_keywords:
- StepComplete method [.NET Framework debugging]
- ICorDebugManagedCallback::StepComplete method [.NET Framework debugging]
ms.assetid: 5e1f2c47-81df-4530-826d-96489cd68719
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c3ced50457519d62be44712386bdabce176c44e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761315"
---
# <a name="icordebugmanagedcallbackstepcomplete-method"></a>Método ICorDebugManagedCallback::StepComplete
Notifica o depurador que uma etapa foi concluída.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT StepComplete (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugStepper    *pStepper,  
    [in] CorDebugStepReason   reason  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pAppDomain`  
 [in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo que contém o segmento em que a etapa foi concluída.  
  
 `pThread`  
 [in] Um ponteiro para um objeto de ICorDebugThread que representa o thread no qual a etapa foi concluída.  
  
 `pStepper`  
 [in] Um ponteiro para um objeto de ICorDebugStepper que representa a etapa na execução do código.  
  
 `reason`  
 [in] Um valor de enumeração CorDebugStepReason que indica o resultado de uma etapa individual.  
  
## <a name="remarks"></a>Comentários  
 O seletor pode ser usado para continuar a depuração se desejado, a menos que a depuração é encerrada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
