---
title: Método ICorDebugChain::GetActiveFrame
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c79f3b3b976b83eb99f8aa26d38a1fe316de471a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744990"
---
# <a name="icordebugchaingetactiveframe-method"></a>Método ICorDebugChain::GetActiveFrame
Obtém o ativo (ou seja, mais recente) quadro da cadeia.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ppFrame`  
 [out] Um ponteiro para o endereço de um objeto ICorDebugFrame que representa o ativo (ou seja, mais recente) quadro da cadeia.  
  
## <a name="remarks"></a>Comentários  
 Se nenhum quadro de pilha gerenciada estiver disponível, `ppFrame` é definido como null.  
  
 Se o quadro ativo não estiver disponível, a chamada será bem-sucedida e `ppFrame` será nulo. Quadros ativa não estará disponíveis para cadeias de iniciada devido ao CHAIN_ENTER_UNMANAGED e para algumas cadeias iniciadas devido ao CHAIN_CLASS_INIT. Consulte a enumeração CorDebugChainReason.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
