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
ms.openlocfilehash: 38cc98f1bfd966d1f764e43b30003a2bae66297d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793465"
---
# <a name="icordebugevalnewobject-method"></a>Método ICorDebugEval::NewObject
Aloca uma nova instância de objeto e chama o método de Construtor especificado.  
  
 Esse método é obsoleto no .NET Framework versão 2,0. Use [ICorDebugEval2:: NewParameterizedObject](icordebugeval2-newparameterizedobject-method.md) em vez disso.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pConstructor`  
 no O Construtor a ser chamado.  
  
 `nArgs`  
 no O tamanho da matriz de `ppArgs`.  
  
 `ppArgs`  
 no Uma matriz de objetos ICorDebugValue, cada um dos quais representa um argumento a ser passado para o construtor.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** 1,1, 1,0  
  
## <a name="see-also"></a>Veja também

- [Método NewParameterizedObject](icordebugeval2-newparameterizedobject-method.md)
