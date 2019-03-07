---
title: Método ICorDebugManagedCallback2::FunctionRemapOpportunity
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.FunctionRemapOpportunity
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::FunctionRemapOpportunity
helpviewer_keywords:
- FunctionRemapOpportunity method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapOpportunity method [.NET Framework debugging]
ms.assetid: 0d6471bc-ad9b-4b1d-a307-c10443918863
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4ab6dac8302d4e03f5d8adad1267f209f131c00
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476471"
---
# <a name="icordebugmanagedcallback2functionremapopportunity-method"></a>Método ICorDebugManagedCallback2::FunctionRemapOpportunity
Notifica o depurador para que a execução de código atingiu um ponto de sequência em uma versão mais antiga de uma função editada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT FunctionRemapOpportunity (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pOldFunction,  
    [in] ICorDebugFunction    *pNewFunction,  
    [in] ULONG32              oldILOffset  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pAppDomain`  
 [in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo que contém a função editada.  
  
 `pThread`  
 [in] Um ponteiro para um objeto de ICorDebugThread que representa o thread no qual o remapeamento de ponto de interrupção foi encontrado.  
  
 `pOldFunction`  
 [in] Um ponteiro para um objeto ICorDebugFunction que representa a versão da função que está sendo executado no thread.  
  
 `pNewFunction`  
 [in] Um ponteiro para um objeto de ICorDebugFunction que representa a versão mais recente da função.  
  
 `oldILOffset`  
 [in] O Microsoft intermediate language (MSIL) deslocamento o ponteiro de instrução na versão antiga da função.  
  
## <a name="remarks"></a>Comentários  
 Esse retorno de chamada oferece o depurador a oportunidade para remapear o ponteiro de instrução ao seu local apropriado na nova versão da função especificada chamando o [ICorDebugILFrame2::RemapFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) método. Se o depurador não chama `RemapFunction` antes de chamar o [icordebugcontroller:: continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) método, o tempo de execução continuarão a executar o código antigo e dispararão a outro `FunctionRemapOpportunity` retorno de chamada no próximo ponto de sequência.  
  
 Esse retorno de chamada será invocado para cada quadro que está executando uma versão mais antiga da função determinada até que o depurador Retorna S_OK.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [Interface ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
