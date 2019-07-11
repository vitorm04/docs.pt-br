---
title: Método ICorDebugChain::GetCallee
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCallee method
helpviewer_keywords:
- ICorDebugChain::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 19560c79-abdc-4bdf-a5fe-eb362a59edc0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 79743b78ea3d19bab4756b580d2feddd07e0a23b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745014"
---
# <a name="icordebugchaingetcallee-method"></a>Método ICorDebugChain::GetCallee
Obtém a cadeia que foi chamada por essa cadeia.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ppChain`  
 [out] Um ponteiro para o endereço de um objeto de ICorDebugChain que representa a cadeia de chamada. Se esta cadeia está sendo executado (ou seja, se essa cadeia não está aguardando uma cadeia de chamada retornar), `ppChain` será nulo.  
  
## <a name="remarks"></a>Comentários  
 Esta cadeia aguardará para a cadeia de chamada retornar antes de retomar a execução. A cadeia de chamada pode ser em outro thread no caso de chamadas de com marshaling entre threads.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
