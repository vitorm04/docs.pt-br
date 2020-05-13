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
ms.openlocfilehash: cacdccf5c27cd1d115134d49e754b4ace2870b72
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205158"
---
# <a name="icordebugframegetstackrange-method"></a>Método ICorDebugFrame::GetStackRange
Obtém o intervalo de endereços absoluto deste quadro de pilhas.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pStart`  
 fora Um ponteiro para um `CORDB_ADDRESS` que especifica o endereço inicial do quadro de pilha representado por esse `ICorDebugFrame` objeto.  
  
 `pEnd`  
 fora Um ponteiro para um `CORDB_ADDRESS` que especifica o endereço final do quadro de pilha representado por esse `ICorDebugFrame` objeto.  
  
## <a name="remarks"></a>Comentários  
 O intervalo de endereços da pilha é útil para compondo juntos rastreamentos de pilha intercalados coletados de vários mecanismos de depuração. O intervalo numérico não fornece informações sobre o conteúdo do quadro de pilhas. Só é significativo para a comparação de locais de quadros de pilhas.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
