---
title: Método ICorDebugEval2::NewParameterizedObject
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObject
helpviewer_keywords:
- NewParameterizedObject method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObject method [.NET Framework debugging]
ms.assetid: 3d705463-e640-4249-8036-4e8206d03cfe
topic_type:
- apiref
ms.openlocfilehash: f6ede42ac90f65f934e285f879bcef62d13b65cb
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976090"
---
# <a name="icordebugeval2newparameterizedobject-method"></a>Método ICorDebugEval2::NewParameterizedObject
Cria uma instância de um novo objeto de tipo com parâmetros e chama o método de construtor do objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT NewParameterizedObject (  
    [in] ICorDebugFunction     *pConstructor,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pConstructor`  
 no Um ponteiro para um objeto ICorDebugFunction que representa o construtor do objeto a ser instanciado.  
  
 `nTypeArgs`  
 no O número de argumentos de tipo passado.  
  
 `ppTypeArgs`  
 no Uma matriz de ponteiros, cada um dos quais aponta para um objeto ICorDebugType que representa um argumento de tipo para o objeto que está sendo instanciado.  
  
 `nArgs`  
 no O número de argumentos passados para o construtor.  
  
 `ppArgs`  
 no Uma matriz de ponteiros, cada um dos quais aponta para um objeto ICorDebugValue que representa um valor de argumento que é passado para o construtor.  
  
## <a name="remarks"></a>Comentários  
 O construtor do objeto pode ter <xref:System.Type> parâmetros.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
