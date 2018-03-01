---
title: "Método ICorDebugController::Detach"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 59fe2c4bfbd91afd263a0ada1eb355aaa8914aa2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontrollerdetach-method"></a>Método ICorDebugController::Detach
Desanexa o depurador do domínio de aplicativo ou processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a>Comentários  
 O domínio de aplicativo ou processo continua a execução normalmente, mas o objeto "ICorDebugProcess" ou "ICorDebugAppDomain" não é mais válido e nenhum retorno de chamada mais ocorrerá.  
  
 O .NET Framework versão 2.0, se a depuração não gerenciada está habilitado, esse método irá falhar devido a limitações de sistema operacional.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 
