---
title: Método ICorDebugEval2::CreateValueForType
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CreateValueForType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CreateValueForType
helpviewer_keywords:
- CreateValueForType method [.NET Framework debugging]
- ICorDebugEval2::CreateValueForType method [.NET Framework debugging]
ms.assetid: ea38ae20-7e0a-427a-be77-d78fae719d82
topic_type:
- apiref
ms.openlocfilehash: 8632799b68ae8f92835d1774472bc1432d886f3b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793478"
---
# <a name="icordebugeval2createvaluefortype-method"></a>Método ICorDebugEval2::CreateValueForType
Obtém um ponteiro para um novo ICorDebugValue do tipo especificado, com um valor inicial de zero ou NULL.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pType`  
 no Ponteiro para um objeto ICorDebugType que representa o tipo.  
  
 `ppValue`  
 fora Ponteiro para o endereço de um objeto de `ICorDebugValue` que representa o valor.  
  
## <a name="remarks"></a>Comentários  
 `CreateValueForType` generaliza [ICorDebugEval:: CreateValue](icordebugeval-createvalue-method.md) permitindo que você especifique um tipo de objeto arbitrário, incluindo tipos construídos, como `List<int>`. A única finalidade desse método é gerar um valor que possa ser passado para uma avaliação de função.  
  
 O tipo deve ser uma classe ou um tipo de valor. Você não pode usar esse método para criar valores de matriz ou de cadeia de caracteres.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
