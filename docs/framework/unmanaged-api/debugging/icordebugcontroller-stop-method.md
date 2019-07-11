---
title: Método ICorDebugController::Stop
ms.date: 03/30/2017
api_name:
- ICorDebugController.Stop
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Stop
helpviewer_keywords:
- Stop method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Stop method [.NET Framework debugging]
ms.assetid: c34e79be-a7fb-479e-8dec-d126a4c330e5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 83bb52f7f2035605914e2fe72ce2daf78de5bc1e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749908"
---
# <a name="icordebugcontrollerstop-method"></a>Método ICorDebugController::Stop
Executa uma parada cooperativa em todos os threads que estão executando o código gerenciado no processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `dwTimeoutIgnored`  
 Não usado.  
  
## <a name="remarks"></a>Comentários  
 `Stop` executa um código cooperativo parada em todos os threads em execução e gerenciado no processo. Durante uma sessão de depuração somente gerenciado, os threads não gerenciados podem continuar a executar (mas serão bloqueados durante a tentativa de chamar código gerenciado). Durante uma sessão de depuração de interoperabilidade, os threads não gerenciados também serão interrompidos. O `dwTimeoutIgnored` valor atualmente é ignorada e tratada como infinito (-1). Se a parada cooperativa falhar devido a um deadlock, todos os threads são suspensos e E_TIMEOUT será retornado.  
  
> [!NOTE]
>  `Stop` é o método síncrono somente na API de depuração. Quando `Stop` Retorna S_OK, o processo é interrompido. Nenhum retorno de chamada é fornecido para notificar os ouvintes da parada. O depurador deve chamar [icordebugcontroller:: continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) para permitir que o processo da continuar.  
  
 O depurador mantém um contador de parada. Quando o contador chega a zero, o controlador é retomado. Cada chamada para `Stop` ou cada retorno de chamada expedido incrementa o contador. Cada chamada para `ICorDebugController::Continue` diminui o contador.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
