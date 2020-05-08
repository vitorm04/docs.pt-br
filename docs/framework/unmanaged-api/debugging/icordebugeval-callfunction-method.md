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
ms.openlocfilehash: 1cf0080945ad78565fae3fedb454ceba7825cb4a
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976233"
---
# <a name="icordebugevalcallfunction-method"></a>Método ICorDebugEval::CallFunction

Define uma chamada para a função especificada.

Esse método é obsoleto no .NET Framework versão 2,0. Use [ICorDebugEval2:: CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md) em vez disso.

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
no Ponteiro para um objeto ICorDebugFunction que especifica a função a ser chamada.

`nArgs`\
no O número de argumentos para a função.

`ppArgs`\
no Uma matriz de ponteiros, cada um dos quais aponta para um objeto ICorDebugValue que especifica um argumento a ser passado para a função.

## <a name="remarks"></a>Comentários

Se a função for virtual, `CallFunction` executará o despacho virtual. Se a função estiver em um domínio de aplicativo diferente, uma transição ocorrerá contanto que todos os argumentos também estejam nesse domínio de aplicativo.

## <a name="requirements"></a>Requisitos

**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).

**Cabeçalho:** CorDebug.idl, CorDebug.h

**Biblioteca:** CorGuids.lib

**Versões do .NET Framework:** 1,1, 1,0

## <a name="see-also"></a>Consulte também

- [Método CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md)
