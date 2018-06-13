---
title: Método ICorDebugVariableHome::GetArgumentIndex
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetArgumentIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetArgumentIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetArgumentiIndex method [.NET Framework debugging]
- GetArgumentIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: e86fcc72-388d-4009-ab21-8f9c3323e9a3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20f65218928ee07d67ea742154469ac3cbea9241
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421759"
---
# <a name="icordebugvariablehomegetargumentindex-method"></a>Método ICorDebugVariableHome::GetArgumentIndex
Obtém o índice de um argumento de função.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetArgumentIndex(  
    [out] ULONG32* pArgumentIndex  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pArgumentIndex`  
 [out] Um ponteiro para o índice do argumento.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna os seguintes valores.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|A chamada do método retornou um índice de argumento válido.|  
|`E_FAIL`|Atual [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instância representa uma variável local.|  
  
## <a name="remarks"></a>Comentários  
 O índice de argumento pode ser usado para recuperar metadados para esse argumento.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
