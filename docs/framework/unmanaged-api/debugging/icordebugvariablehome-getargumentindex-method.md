---
title: 'Método ICorDebugVariableHome:: GetArgumentIndex'
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
- ICorDebugVariableHome::GetArgumentIndex method [.NET Framework debugging]
- GetArgumentIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: e86fcc72-388d-4009-ab21-8f9c3323e9a3
topic_type:
- apiref
ms.openlocfilehash: 27a676fd1d2d7903943e44f8a7201b88af4fba89
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397002"
---
# <a name="icordebugvariablehomegetargumentindex-method"></a>Método ICorDebugVariableHome:: GetArgumentIndex

Obtém o índice de um argumento de função.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetArgumentIndex(
    [out] ULONG32* pArgumentIndex
);
```

## <a name="parameters"></a>Parâmetros

`pArgumentIndex`\
fora Um ponteiro para o índice de argumento.

## <a name="return-value"></a>Valor retornado

O método retorna os valores a seguir.

|Valor|Descrição|
|-----------|-----------------|
|`S_OK`|A chamada do método retornou um índice de argumento válido.|
|`E_FAIL`|A instância [ICorDebugVariableHome](icordebugvariablehome-interface.md) atual representa uma variável local.|

## <a name="remarks"></a>Comentários

O índice de argumento pode ser usado para recuperar metadados para esse argumento.

## <a name="requirements"></a>Requisitos

**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).

**Cabeçalho:** CorDebug.idl, CorDebug.h

**Biblioteca:** CorGuids.lib

**.NET Framework versões:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]

## <a name="see-also"></a>Veja também

- [Interface ICorDebugVariableHome](icordebugvariablehome-interface.md)
