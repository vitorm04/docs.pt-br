---
title: Método ICorDebugProcess::GetHelperThreadID
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHelperThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHelperThreadID
helpviewer_keywords:
- GetHelperThreadID method [.NET Framework debugging]
- ICorDebugProcess::GetHelperThreadID method [.NET Framework debugging]
ms.assetid: 84e1e605-37c1-49a5-8e12-35db85654622
topic_type:
- apiref
ms.openlocfilehash: d38a59b23d47cbaf57dc21e121d56530a514d354
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128855"
---
# <a name="icordebugprocessgethelperthreadid-method"></a>Método ICorDebugProcess::GetHelperThreadID
Obtém a ID do thread do sistema operacional (SO) do thread auxiliar interno do depurador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pThreadID`  
 fora Um ponteiro para a ID de thread do sistema operacional do thread auxiliar interno do depurador.  
  
## <a name="remarks"></a>Comentários  
 Durante a depuração gerenciada e não gerenciada, é responsabilidade do depurador garantir que o thread com a ID especificada permaneça em execução se atingir um ponto de interrupção colocado pelo depurador. Um depurador também pode desejar ocultar esse thread do usuário. Se nenhum thread auxiliar existir no processo ainda, o método `GetHelperThreadID` retornará zero em *`pThreadID`.  
  
 Não é possível armazenar em cache a ID do thread auxiliar, pois ela pode mudar ao longo do tempo. Você deve consultar novamente a ID do thread em cada evento de parada.  
  
 A ID de thread do thread auxiliar do depurador estará correta em cada evento [ICorDebugManagedCallback:: CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) não gerenciado, permitindo que um depurador determine a ID do thread do seu thread auxiliar e o oculte do usuário. Um thread que é identificado como um thread auxiliar durante um evento de `ICorDebugManagedCallback::CreateThread` não gerenciado nunca executará código de usuário gerenciado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug. idl. CorDebug. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
