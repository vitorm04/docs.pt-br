---
title: Método ICorDebugManagedCallback::CreateProcess
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateProcess
helpviewer_keywords:
- ICorDebugManagedCallback::CreateProcess method [.NET Framework debugging]
- CreateProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
ms.assetid: 8e89d5ee-e4e3-4738-8302-0b7d1cf4846e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7693111427f3181adcd2127ad5ecb2a317e30921
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54515609"
---
# <a name="icordebugmanagedcallbackcreateprocess-method"></a>Método ICorDebugManagedCallback::CreateProcess
Notifica o depurador quando um processo foi anexado ou iniciado pela primeira vez.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CreateProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pProcess`  
 [in] Um ponteiro para um objeto ICorDebugProcess que representa o processo que foi anexado ou iniciado.  
  
## <a name="remarks"></a>Comentários  
 Esse método não é chamado até que o common language runtime é inicializado. A maioria dos [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) métodos retornarão CORDBG_E_NOTREADY antes do `CreateProcess` retorno de chamada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
