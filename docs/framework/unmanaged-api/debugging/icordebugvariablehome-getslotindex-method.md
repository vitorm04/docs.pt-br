---
title: 'Método ICorDebugVariableHome:: GetSlotIndex'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetSlotIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetSlotIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetSlotIndex method [.NET Framework debugging]
- GetSlotIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 966da50d-5665-4fff-bf7b-1c72bbadd9a4
topic_type:
- apiref
ms.openlocfilehash: 0bffd2db0a4a061a8629ff50a03a319feec6d836
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396559"
---
# <a name="icordebugvariablehomegetslotindex-method"></a>Método ICorDebugVariableHome:: GetSlotIndex
Obtém o índice de slot gerenciado de uma variável local.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pSlotIndex`  
 fora Um ponteiro para o índice de slot de uma variável local.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna os valores a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|A chamada de método retornou um valor de índice de slot em `pSlotIndex` .|  
|`E_FAIL`|A instância [ICorDebugVariableHome](icordebugvariablehome-interface.md) atual representa um argumento de função.|  
  
## <a name="remarks"></a>Comentários  
 O slot-index pode ser usado para recuperar os metadados para essa variável local.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugVariableHome](icordebugvariablehome-interface.md)
