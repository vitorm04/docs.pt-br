---
title: Método ICorDebugHeapValue2::CreateHandle
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue2.CreateHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue2::CreateHandle
helpviewer_keywords:
- CreateHandle method [.NET Framework debugging]
- ICorDebugHeapValue2::CreateHandle method [.NET Framework debugging]
ms.assetid: fbc418e8-fa22-420d-84ec-e0e1800db041
topic_type:
- apiref
ms.openlocfilehash: c7a1bf3cb10cbc8cdae2788b45e1badaf66a9dbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178873"
---
# <a name="icordebugheapvalue2createhandle-method"></a>Método ICorDebugHeapValue2::CreateHandle
Cria uma alça do tipo especificado para o valor de pilha representado por este objeto ICorDebugHeapValue2.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `type`  
 [em] Um valor da enumeração CorDebugHandleType que especifica o tipo de alça a ser criada.  
  
 `ppHandle`  
 [fora] Um ponteiro para o endereço de um objeto ICorDebugHandleValue que representa a nova alça para este valor de pilha.  
  
## <a name="remarks"></a>Comentários  
 A alça será criada no domínio do aplicativo que está associado ao valor de pilha e se tornará inválida se o domínio do aplicativo for descarregado.  
  
 Várias chamadas para esta função para o mesmo valor de pilha criarão várias alças. Como as alças afetam o desempenho do coletor de lixo, o depurador deve limitar-se a um número relativamente pequeno de alças (cerca de 256) que estão ativas por vez.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
