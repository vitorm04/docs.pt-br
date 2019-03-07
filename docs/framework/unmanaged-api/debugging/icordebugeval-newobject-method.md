---
title: Método ICorDebugEval::NewObject
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewObject
helpviewer_keywords:
- NewObject method [.NET Framework debugging]
- ICorDebugEval::NewObject method [.NET Framework debugging]
ms.assetid: ce3025e8-defa-4c5e-8298-f49d71fa5736
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 97217421d30ee4065aa1b2500e9486405e438902
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471362"
---
# <a name="icordebugevalnewobject-method"></a>Método ICorDebugEval::NewObject
Aloca uma nova instância de objeto e chama o método de construtor especificado.  
  
 Este método é obsoleto no .NET Framework versão 2.0. Use [ICorDebugEval2::NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) em vez disso.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pConstructor`  
 [in] O construtor seja chamado.  
  
 `nArgs`  
 [in] O tamanho do `ppArgs` matriz.  
  
 `ppArgs`  
 [in] Uma matriz de objetos ICorDebugValue, cada um deles representa um argumento a ser passado para o construtor.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** 1.1, 1.0  
  
## <a name="see-also"></a>Consulte também
- [Método NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)
