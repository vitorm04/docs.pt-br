---
title: Método ICorDebugManagedCallback::ExitProcess
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitProcess
helpviewer_keywords:
- ExitProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::ExitProcess method [.NET Framework debugging]
ms.assetid: 63a7d47a-0d54-4e29-9767-9f09feaa38b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51162bfb6f9763d2ab4ac1f86e0ccdc15b601271
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59159868"
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a>Método ICorDebugManagedCallback::ExitProcess
Notifica o depurador que um processo foi encerrado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pProcess`  
 [in] Um ponteiro para um objeto ICorDebugProcess que representa o processo.  
  
## <a name="remarks"></a>Comentários  
 Você não pode continuar a partir um `ExitProcess` eventos. Esse evento pode disparar assincronamente a outros eventos, enquanto o processo parece ser interrompido. Isso pode ocorrer se o processo é encerrado enquanto estiver parado, geralmente devido a algumas force externo.  
  
 Se o common language runtime (CLR) já está distribuindo um retorno de chamada gerenciado, esse evento será atrasado até que esse retorno de chamada foi retornado.  
  
 O `ExitProcess` evento é o único evento de saída/unload é garantido que seja chamado no desligamento.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
