---
title: Método ICorDebugHeapValue3::GetThreadOwningMonitorLock
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3.GetThreadOwningMonitorLock
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3::GetThreadOwningMonitorLock
helpviewer_keywords:
- GetThreadOwningMonitorLock method [.NET Framework debugging]
- ICorDebugHeapValue3::GetThreadOwningMonitorLock method [.NET Framework debugging]
ms.assetid: e06fc19d-2cf4-4cad-81a3-137a68af8969
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 361cc3b897b4c85297b597f80aaffc2a2760f88e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468467"
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a>Método ICorDebugHeapValue3::GetThreadOwningMonitorLock
Retorna o thread gerenciado que detém o bloqueio de monitor nesse objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ppThread`  
 [out] O thread gerenciado que detém o bloqueio de monitor nesse objeto.  
  
 `pAcquisitionCount`  
 [out] O número de vezes que esse thread terá de liberar o bloqueio antes de retornar ao que está sendo sem proprietário.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|S_FALSE|Nenhum thread gerenciado detém o bloqueio de monitor nesse objeto.|  
  
## <a name="exceptions"></a>Exceções  
  
## <a name="remarks"></a>Comentários  
 Se um thread gerenciado detém o bloqueio de monitor nesse objeto:  
  
-   O método retorna S_OK.  
  
-   O objeto de thread é válido até que o thread seja encerrado.  
  
 Se nenhum thread gerenciado detém o bloqueio de monitor nesse objeto `ppThread` e `pAcquisitionCount` forem alterados, e o método retorna S_FALSE.  
  
 Se `ppThread` ou `pAcquisitionCount` não for um ponteiro válido, o resultado será indefinido.  
  
 Se ocorrer um erro, de modo que ele não pode ser determinado que, se houver, o thread possui o bloqueio de monitor nesse objeto, o método retorna um HRESULT que indica falha.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
