---
title: "Método ICorDebugThread2::GetActiveFunctions"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread2.GetActiveFunctions
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread2::GetActiveFunctions
helpviewer_keywords:
- GetActiveFunctions method [.NET Framework debugging]
- ICorDebugThread2::GetActiveFunctions method [.NET Framework debugging]
ms.assetid: 27fae01a-ecec-423a-973e-24f8de55826c
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d1f7f416a5441b788394e93a98d274d02fa2ec2f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthread2getactivefunctions-method"></a>Método ICorDebugThread2::GetActiveFunctions
Obtém informações sobre a função active em cada um dos quadros desse segmento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetActiveFunctions (  
    [in]   ULONG32             cFunctions,  
    [out]  ULONG32             *pcFunctions,  
    [in, out, size_is(cFunctions), length_is(*pcFunctions)]  
        COR_ACTIVE_FUNCTION    pFunctions[]  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cFunctions`  
 [in] O tamanho do `pFunctions` matriz.  
  
 `pcFunctions`  
 [out] Um ponteiro para o número de objetos retornados na `pFunctions` matriz. O número de objetos retornados será igual ao número de quadros gerenciados na pilha.  
  
 `pFunctions`  
 [out no] Uma matriz de objetos COR_ACTIVE_FUNCTION, cada uma delas contém informações sobre as funções ativas em quadros desse segmento.  
  
 O primeiro elemento será usado para o quadro folha e assim por diante novamente para a raiz da pilha.  
  
## <a name="remarks"></a>Comentários  
 Se `pFunctions` for nulo na entrada, `GetActiveFunctions` retorna somente o número de funções que estão na pilha. Ou seja, se `pFunctions` for nulo na entrada, `GetActiveFunctions` retorna um valor somente em `pcFunctions`.  
  
 O `GetActiveFunctions` método destina-se como uma otimização em obter as mesmas informações de quadros em um rastreamento de pilha e inclui apenas os quadros que teria um objeto ICorDebugILFrame para eles no rastreamento de pilha completos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
