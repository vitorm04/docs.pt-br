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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f20c24984aadd05139d1a427b75bc65438539ff1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugeval2newparameterizedobject-method"></a>Método ICorDebugEval2::NewParameterizedObject
Cria um novo objeto de tipo parametrizado e chama o método de construtor do objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT NewParameterizedObject (  
    [in] ICorDebugFunction     *pConstructor,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pConstructor`  
 [in] Um ponteiro para um objeto ICorDebugFunction que representa o construtor do objeto a ser instanciado.  
  
 `nTypeArgs`  
 [in] O número de argumentos de tipo passado.  
  
 `ppTypeArgs`  
 [in] Uma matriz de ponteiros, cada um deles aponta para um objeto ICorDebugType que representa um argumento de tipo para o objeto que está sendo criado.  
  
 `nArgs`  
 [in] O número de argumentos passados para o construtor.  
  
 `ppArgs`  
 [in] Uma matriz de ponteiros, cada um deles aponta para um objeto ICorDebugValue que representa um valor de argumento que é passado para o construtor.  
  
## <a name="remarks"></a>Comentários  
 O construtor do objeto pode levar <xref:System.Type> parâmetros.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
