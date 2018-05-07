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
ms.openlocfilehash: 5da87071bc23ac17a3077049cd77f0fb8611439f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugframegetstackrange-method"></a>Método ICorDebugFrame::GetStackRange
Obtém o intervalo de endereços absolutos deste quadro de pilha.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pStart`  
 [out] Um ponteiro para um `CORDB_ADDRESS` que especifica o endereço inicial do quadro de pilhas representado por esse `ICorDebugFrame` objeto.  
  
 `pEnd`  
 [out] Um ponteiro para um `CORDB_ADDRESS` que especifica o endereço final do quadro de pilhas representado por esse `ICorDebugFrame` objeto.  
  
## <a name="remarks"></a>Comentários  
 O intervalo de endereços da pilha é útil para juntando rastreamentos de pilha intercalada coletados a partir de vários mecanismos de depuração. O intervalo numérico não fornece nenhuma informação sobre o conteúdo do quadro de pilhas. Faz sentido somente para comparação de locais de quadro de pilha.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
