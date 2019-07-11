---
title: Método ICorDebugController::Detach
ms.date: 03/30/2017
api_name:
- ICorDebugController.Detach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Detach
helpviewer_keywords:
- Detach method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Detach method [.NET Framework debugging]
ms.assetid: 06fae364-f2c6-4a50-aa7e-3da9f2684dc3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f687e48413cb227ad715720e24bd645065309553
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748848"
---
# <a name="icordebugcontrollerdetach-method"></a>Método ICorDebugController::Detach
Desanexa o depurador do domínio de aplicativo ou processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a>Comentários  
 O domínio de aplicativo ou processo continua normalmente, a execução, mas o objeto "ICorDebugProcess" ou "ICorDebugAppDomain" não é mais válido e mais nenhum retorno de chamada será feita.  
  
 No .NET Framework versão 2.0, se a depuração não gerenciada está habilitada, esse método irá falhar devido a limitações de sistema operacional.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
