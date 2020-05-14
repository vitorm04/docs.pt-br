---
title: 'Método ICorDebugVariableHome:: GetOffset'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetOffset
helpviewer_keywords:
- ICorDebugVariableHome::GetOffset method [.NET Framework debugging]
- GetOffset method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: f025c2e5-3f6c-4be8-9ffe-c8b214617dfe
topic_type:
- apiref
ms.openlocfilehash: 75a165e2fd517f36d779a934a5bdd9c41956411a
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396761"
---
# <a name="icordebugvariablehomegetoffset-method"></a>Método ICorDebugVariableHome:: GetOffset
Obtém o deslocamento do registro base de uma variável.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pOffset`  
 fora O deslocamento do registro base.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna os seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|A variável está em um local de memória relativa ao registro.|  
|`E_FAIL`|A variável não está em um local de memória relativa ao registro.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugVariableHome](icordebugvariablehome-interface.md)
