---
title: "Método ICorDebugChain::GetActiveFrame"
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
- ICorDebugChain.GetActiveFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetActiveFrame
helpviewer_keywords:
- ICorDebugChain::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 36887017-670b-4f21-b406-8fab956f84a3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7498e031b74bd904b908342b663e4421432e6d95
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchaingetactiveframe-method"></a>Método ICorDebugChain::GetActiveFrame
Obtém o ativo (ou seja, mais recente) quadro da cadeia.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppFrame`  
 [out] Um ponteiro para o endereço de um objeto ICorDebugFrame que representa o ativo (ou seja, mais recente) quadro da cadeia.  
  
## <a name="remarks"></a>Comentários  
 Se nenhum quadro de pilha gerenciada estiver disponível, `ppFrame` é definido como null.  
  
 Se o quadro ativo não estiver disponível, a chamada será bem-sucedida e `ppFrame` será nulo. Quadros ativa não estará disponíveis para cadeias iniciadas devido a CHAIN_ENTER_UNMANAGED e para algumas cadeias iniciadas devido a CHAIN_CLASS_INIT. Consulte a enumeração CorDebugChainReason.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
