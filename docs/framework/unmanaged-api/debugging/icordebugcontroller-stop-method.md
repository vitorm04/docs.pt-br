---
title: "Método ICorDebugController::Stop"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7a8699a54814b37cc03404b72330812f3eb2b2f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontrollerstop-method"></a>Método ICorDebugController::Stop
Executa uma parada cooperativa em todos os threads que estão executando o código gerenciado no processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwTimeoutIgnored`  
 Não usado.  
  
## <a name="remarks"></a>Comentários  
 `Stop`executa um código de parada cooperativo em todos os threads em execução gerenciada no processo. Durante uma sessão de depuração somente gerenciado, os threads gerenciados podem continuar em execução (mas será bloqueado ao tentar chamar código gerenciado). Durante uma sessão de depuração de interoperabilidade, os threads gerenciados também serão interrompidos. O `dwTimeoutIgnored` valor atualmente é ignorada e tratada como infinito (-1). Se a interrupção cooperativa falhar devido a um deadlock, todos os threads são suspensos e E_TIMEOUT é retornado.  
  
> [!NOTE]
>  `Stop`é o método síncrono apenas na API de depuração. Quando `Stop` Retorna S_OK, o processo foi interrompido. Nenhum retorno de chamada é fornecido para notificar os ouvintes da parada. O depurador deve chamar [Icordebugcontroller](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) para permitir que o processo continuar.  
  
 O depurador mantém um contador de parada. Quando o contador chega a zero, o controlador é retomado. Cada chamada para `Stop` ou cada retorno de chamada expedido incrementa o contador. Cada chamada para `ICorDebugController::Continue` diminui o contador.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 
