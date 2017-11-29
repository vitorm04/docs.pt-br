---
title: "Método ICorDebugChain::GetStackRange"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain.GetStackRange
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain::GetStackRange
helpviewer_keywords:
- ICorDebugChain::GetStackRange method [.NET Framework debugging]
- GetStackRange method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 554284e7-3f6c-4d40-8da5-1c9317fbd484
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ce5e42bb9374f22ad29ef0e97a141a796f087a98
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugchaingetstackrange-method"></a>Método ICorDebugChain::GetStackRange
Obtém o intervalo de endereços do segmento de pilha para essa cadeia.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pStart`  
 [out] Um ponteiro para um `CORDB_ADDRESS` valor que é o endereço inicial do segmento de pilha.  
  
 `pEnd`  
 [out] Um ponteiro para um `CORDB_ADDRESS` valor que é o endereço final do segmento de pilha.  
  
## <a name="remarks"></a>Comentários  
 O intervalo numérico é significativo apenas para comparação de locais de quadro de pilha. Você não pode fazer suposições sobre o que realmente está armazenado na pilha.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
