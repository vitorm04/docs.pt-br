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
ms.openlocfilehash: 43532888d181adcb7a7e3760f2a5e3d8f664a35c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995807"
---
# <a name="icordebugframegetstackrange-method"></a>Método ICorDebugFrame::GetStackRange
Obtém o intervalo de endereços absoluto deste quadro de pilha.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
