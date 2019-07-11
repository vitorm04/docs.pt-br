---
title: Método ICorDebugEval2::NewParameterizedObjectNoConstructor
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedObjectNoConstructor
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObjectNoConstructor
helpviewer_keywords:
- NewParameterizedObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObjectNoConstructor method [.NET Framework debugging]
ms.assetid: f15b5b78-94f4-4eb9-b3b3-a621272f357c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4434f5d0eaa45c9cfcbadb20b29564f0643a2dc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754440"
---
# <a name="icordebugeval2newparameterizedobjectnoconstructor-method"></a>Método ICorDebugEval2::NewParameterizedObjectNoConstructor
Cria uma instância de um novo objeto de tipo parametrizado da classe especificada sem tentar chamar um método de construtor.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT NewParameterizedObjectNoConstructor (  
    [in] ICorDebugClass        *pClass,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pClass`  
 [in] Um ponteiro para um objeto ICorDebugClass que representa a classe do objeto a ser instanciado.  
  
 `nTypeArgs`  
 [in] O número de argumentos de tipo passado.  
  
 `ppTypeArgs`  
 [in] Uma matriz de ponteiros, cada um deles aponta para um objeto de ICorDebugType que representa um argumento de tipo para o objeto de instância está sendo criado.  
  
## <a name="remarks"></a>Comentários  
 O `NewParameterizedObjectNoConstructor` método irá falhar se um número incorreto de argumentos de tipo ou os tipos de errado de argumentos de tipo são passados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
