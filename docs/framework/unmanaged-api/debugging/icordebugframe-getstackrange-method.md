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
ms.openlocfilehash: 7a35ce025360e0ec8b7085d68e54548026b7c7fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178905"
---
# <a name="icordebugframegetstackrange-method"></a>Método ICorDebugFrame::GetStackRange
Obtém o alcance de endereço absoluto deste quadro de pilha.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `pStart`  
 [fora] Um ponteiro `CORDB_ADDRESS` para um que especifica o endereço inicial `ICorDebugFrame` do quadro de pilha representado por este objeto.  
  
 `pEnd`  
 [fora] Um ponteiro `CORDB_ADDRESS` para um que especifica o endereço final `ICorDebugFrame` do quadro de pilha representado por este objeto.  
  
## <a name="remarks"></a>Comentários  
 O intervalo de endereços da pilha é útil para juntar traços de pilha intercalados coletados de vários mecanismos de depuração. O intervalo numérico não fornece informações sobre o conteúdo do quadro de pilha. É significativo apenas para comparação de locais de quadro sumido.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
