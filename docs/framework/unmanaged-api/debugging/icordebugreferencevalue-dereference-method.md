---
title: Método ICorDebugReferenceValue::Dereference
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.Dereference
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::Dereference
helpviewer_keywords:
- ICorDebugReferenceValue::Dereference method [.NET Framework debugging]
- Dereference method [.NET Framework debugging]
ms.assetid: 5ec8cf76-3deb-4ce6-9a49-77a4c35d80b9
topic_type:
- apiref
ms.openlocfilehash: 7c64823e1a5c519eb74b508af093afeb1132e608
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210079"
---
# <a name="icordebugreferencevaluedereference-method"></a>Método ICorDebugReferenceValue::Dereference
Obtém o objeto que é referenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Dereference (  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ppValue`  
 fora Um ponteiro para o endereço de um ICorDebugValue que representa o objeto ao qual esse objeto ICorDebugReferenceValue aponta.  
  
## <a name="remarks"></a>Comentários  
 O `ICorDebugValue` objeto é válido somente enquanto sua referência ainda não foi desabilitada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
