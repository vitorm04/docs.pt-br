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
ms.openlocfilehash: e64e39d10d20f63430ffe9d2c4df8643e286a677
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210014"
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
no Um `mdToken` valor que faz referência ao assembly.

`ppAssembly`\
fora Um ponteiro para o endereço de um objeto ICorDebugAssembly que representa o assembly.

## <a name="remarks"></a>Comentários

Se o assembly ainda não estiver carregado quando `ResolveAssembly` for chamado, um valor HRESULT de CORDBG_E_CANNOT_RESOLVE_ASSEMBLY será retornado.

## <a name="requirements"></a>Requisitos

**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).

**Cabeçalho:** CorDebug.idl, CorDebug.h

**Biblioteca:** CorGuids.lib

**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
