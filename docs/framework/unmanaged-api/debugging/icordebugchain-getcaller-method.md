---
title: Método ICorDebugChain::GetCaller
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCaller
helpviewer_keywords:
- ICorDebugChain::GetCaller method [.NET Framework debugging]
- GetCaller method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: d0b8ab4b-d7d2-4fa0-945f-3d2b87e7e991
topic_type:
- apiref
ms.openlocfilehash: 5a07550d44857526e8ab4ded9f1827ef12e3bba4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192131"
---
# <a name="icordebugchaingetcaller-method"></a>Método ICorDebugChain::GetCaller
Obtém a cadeia que chamou essa cadeia.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetCaller (  
    [out] ICorDebugChain      **ppChain  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ppChain`  
 fora Um ponteiro para o endereço de um objeto ICorDebugChain que representa a cadeia de chamada.  
  
 Se essa cadeia fosse chamada espontaneamente (como seria o caso, se essa cadeia ou o depurador inicializasse a pilha de chamadas), `ppChain` será NULL.  
  
## <a name="remarks"></a>Comentários  
 A cadeia de chamada pode estar em um thread diferente, se a chamada tiver sido empacotada entre threads.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
