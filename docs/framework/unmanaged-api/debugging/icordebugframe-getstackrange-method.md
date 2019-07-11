---
title: Método ICorDebugFrame::GetStackRange
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetStackRange
helpviewer_keywords:
- GetStackRange method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetStackRange method [.NET Framework debugging]
ms.assetid: fab037cb-fda6-40fb-9367-921e435dd5a0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c9f58e66286f5e3e169507efd2f87ce10e9d323b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754860"
---
# <a name="icordebugframegetstackrange-method"></a>Método ICorDebugFrame::GetStackRange
Obtém o intervalo de endereços absoluto deste quadro de pilha.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pStart`  
 [out] Um ponteiro para um `CORDB_ADDRESS` que especifica o endereço inicial do quadro de pilha representado por este `ICorDebugFrame` objeto.  
  
 `pEnd`  
 [out] Um ponteiro para um `CORDB_ADDRESS` que especifica o endereço final do quadro de pilha representado por este `ICorDebugFrame` objeto.  
  
## <a name="remarks"></a>Comentários  
 O intervalo de endereços da pilha é útil para reunir rastreamentos de pilha intercalados, coletados de vários mecanismos de depuração. O intervalo numérico não fornece informações sobre o conteúdo da estrutura de pilhas. Ele é significativo apenas para comparação dos locais de quadro de pilha.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
