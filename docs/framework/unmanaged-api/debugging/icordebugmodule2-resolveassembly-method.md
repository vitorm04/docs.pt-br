---
title: Método ICorDebugModule2::ResolveAssembly
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.ResolveAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::ResolveAssembly
helpviewer_keywords:
- ICorDebugModule2::ResolveAssembly method [.NET Framework debugging]
- ResolveAssembly method [.NET Framework debugging]
ms.assetid: ddf9085c-7161-44bd-9609-cd2732b9009f
topic_type:
- apiref
ms.openlocfilehash: 0809a149a5a5a5e9adea059140d7b4b456337ef3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125299"
---
# <a name="icordebugmodule2resolveassembly-method"></a>Método ICorDebugModule2::ResolveAssembly

Resolve o assembly referenciado pelo token de metadados especificado.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT ResolveAssembly (
    [in]  mdToken             tkAssemblyRef,
    [out] ICorDebugAssembly   **ppAssembly
);
```

## <a name="parameters"></a>Parâmetros

`tkAssemblyRef`\
no Um valor `mdToken` que faz referência ao assembly.

`ppAssembly`\
fora Um ponteiro para o endereço de um objeto ICorDebugAssembly que representa o assembly.

## <a name="remarks"></a>Comentários

Se o assembly ainda não estiver carregado quando `ResolveAssembly` for chamado, um valor HRESULT de CORDBG_E_CANNOT_RESOLVE_ASSEMBLY será retornado.

## <a name="requirements"></a>Requisitos

**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).

**Cabeçalho:** CorDebug.idl, CorDebug.h

**Biblioteca:** CorGuids.lib

**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
