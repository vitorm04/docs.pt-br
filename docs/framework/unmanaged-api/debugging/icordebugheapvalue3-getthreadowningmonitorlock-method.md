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
ms.openlocfilehash: 7ba09991e9452a86c6b7a1cbb08a38a71ba2aeaa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416758"
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a>Método ICorDebugHeapValue3::GetThreadOwningMonitorLock
Retorna o thread gerenciado que possui o bloqueio de monitor nesse objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppThread`  
 [out] O thread gerenciado que possui o bloqueio de monitor nesse objeto.  
  
 `pAcquisitionCount`  
 [out] O número de vezes que esse thread precisa liberar o bloqueio antes de retornar para sendo sem proprietário.  
  
## <a name="return-value"></a>Valor de retorno  
 Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|S_FALSE|Nenhum thread gerenciado possui o bloqueio de monitor nesse objeto.|  
  
## <a name="exceptions"></a>Exceções  
  
## <a name="remarks"></a>Comentários  
 Se um thread gerenciado possui o bloqueio de monitor nesse objeto:  
  
-   O método retorna S_OK.  
  
-   O objeto de thread é válido até que o thread será encerrado.  
  
 Se nenhum thread gerenciado possui o bloqueio de monitor nesse objeto `ppThread` e `pAcquisitionCount` foram modificados, e o método retornará S_FALSE.  
  
 Se `ppThread` ou `pAcquisitionCount` não é um ponteiro válido, o resultado é indefinido.  
  
 Se ocorrer um erro, de modo que ele não pode ser determinado que, se houver, thread possui o bloqueio de monitor nesse objeto, o método retorna um HRESULT que indica falha.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
