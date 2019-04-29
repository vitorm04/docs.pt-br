---
title: Método ICorDebugEval::CallFunction
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CallFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CallFunction
helpviewer_keywords:
- ICorDebugEval::CallFunction method [.NET Framework debugging]
- CallFunction method [.NET Framework debugging]
ms.assetid: 7f470c5c-e1c0-4d8d-aad8-830f113ae751
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 66e51dc15f7d44ede26634571fa04c58e9735694
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934765"
---
# <a name="icordebugevalcallfunction-method"></a>Método ICorDebugEval::CallFunction

Define uma chamada para a função especificada.

Este método é obsoleto no .NET Framework versão 2.0. Use [ICorDebugEval2::CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md) em vez disso.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT CallFunction (
    [in] ICorDebugFunction  *pFunction,
    [in] ULONG32            nArgs,
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]
);
```

## <a name="parameters"></a>Parâmetros

`pFunction`\
[in] Ponteiro para um objeto de ICorDebugFunction que especifica a função a ser chamado.

`nArgs`\
[in] O número de argumentos da função.

`ppArgs`\
[in] Uma matriz de ponteiros, cada um deles aponta para um objeto de ICorDebugValue que especifica um argumento a ser passado para a função.

## <a name="remarks"></a>Comentários

Se a função é virtual, `CallFunction` executará a expedição virtual. Se a função está em um domínio de aplicativo diferente, uma transição ocorrerá desde que todos os argumentos também estão no domínio do aplicativo.

## <a name="requirements"></a>Requisitos

**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).

**Cabeçalho:** CorDebug.idl, CorDebug.h

**Biblioteca:** CorGuids.lib

**Versões do .NET framework:** 1.1, 1.0

## <a name="see-also"></a>Consulte também

- [Método CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md)