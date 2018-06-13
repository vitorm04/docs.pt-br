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
ms.openlocfilehash: dc900ca20ac87ddecfd8f7adf0894af21ca5d2f0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418084"
---
# <a name="icordebugmanagedcallback2functionremapopportunity-method"></a>Método ICorDebugManagedCallback2::FunctionRemapOpportunity
Notifica o depurador que a execução de código atingiu um ponto de sequência em uma versão anterior de uma função editada.  
  
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
  
#### <a name="parameters"></a>Parâmetros  
 `pAppDomain`  
 [in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo que contém a função editada.  
  
 `pThread`  
 [in] Um ponteiro para um objeto ICorDebugThread que representa o thread em que o ponto de interrupção remapear foi encontrado.  
  
 `pOldFunction`  
 [in] Um ponteiro para um objeto ICorDebugFunction que representa a versão da função que está sendo executada no thread.  
  
 `pNewFunction`  
 [in] Um ponteiro para um objeto ICorDebugFunction que representa a versão mais recente da função.  
  
 `oldILOffset`  
 [in] O deslocamento de intermediate language (MSIL) da Microsoft do ponteiro de instrução na versão antiga da função.  
  
## <a name="remarks"></a>Comentários  
 Esse retorno de chamada de depurador uma oportunidade para remapear o ponteiro de instrução para seus devidos lugares na nova versão da função especificada, chamando o [Icordebugilframe2](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) método. Se o depurador não chamar `RemapFunction` antes de chamar o [Icordebugcontroller](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) método, o tempo de execução continuará a executar o código antigo e disparam outro `FunctionRemapOpportunity` retorno de chamada no próximo ponto de sequência.  
  
 Esse retorno de chamada será invocado para todos os quadros que está executando uma versão mais antiga da função dada até que o depurador Retorna S_OK.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [Interface ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
