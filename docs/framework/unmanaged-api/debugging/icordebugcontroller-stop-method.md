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
ms.openlocfilehash: 363d8f7d8cf960fb23210225c4545f73d597d663
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912837"
---
# <a name="icordebugcontrollerstop-method"></a>Método ICorDebugController::Stop
Executa uma parada cooperativa em todos os threads que estão executando código gerenciado no processo.  
  
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
 `Stop`executa uma parada cooperativa em todos os threads que executam código gerenciado no processo. Durante uma sessão de depuração somente gerenciada, threads não gerenciados podem continuar em execução (mas serão bloqueados ao tentar chamar código gerenciado). Durante uma sessão de depuração de interoperabilidade, os threads não gerenciados também serão interrompidos. O `dwTimeoutIgnored` valor é ignorado no momento e tratado como infinito (-1). Se a parada cooperativa falhar devido a um deadlock, todos os threads serão suspensos e E_TIMEOUT será retornado.  
  
> [!NOTE]
> `Stop`é o único método síncrono na API de depuração. Quando `Stop` retorna S_OK, o processo é interrompido. Nenhum retorno de chamada é fornecido para notificar os ouvintes da parada. O depurador deve chamar [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) para permitir que o processo retome.  
  
 O depurador mantém um contador de parada. Quando o contador chega a zero, o controlador é retomado. Cada chamada para `Stop` ou cada retorno de chamada despachado incrementa o contador. Cada chamada para `ICorDebugController::Continue` Decrementa o contador.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
