---
title: "Método ICorDebugChain::GetCallee"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain.GetCallee
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain::GetCallee method
helpviewer_keywords:
- ICorDebugChain::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 19560c79-abdc-4bdf-a5fe-eb362a59edc0
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3b584929d99e641e361de916c402a0d5723e53c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchaingetcallee-method"></a>Método ICorDebugChain::GetCallee
Obtém a cadeia que foi chamada por essa cadeia.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppChain`  
 [out] Um ponteiro para o endereço de um objeto ICorDebugChain que representa a cadeia de chamada. Se esta cadeia está em execução (ou seja, se essa cadeia não estiver esperando por uma cadeia de chamada retornar), `ppChain` será nulo.  
  
## <a name="remarks"></a>Comentários  
 Esta cadeia de espera para a cadeia de chamada retornar antes de retomar a execução. A cadeia de chamada pode ser em outro thread no caso de chamadas empacotadas entre threads.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
