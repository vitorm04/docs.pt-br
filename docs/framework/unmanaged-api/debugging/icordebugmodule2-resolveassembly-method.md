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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd899422287d34407778f67e5b4dfd2f33ffd00c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994819"
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
[in] Um `mdToken` valor que faz referência ao assembly.

`ppAssembly`\
[out] Um ponteiro para o endereço de um objeto ICorDebugAssembly que representa o assembly.

## <a name="remarks"></a>Comentários

Se o assembly não está carregado quando `ResolveAssembly` é chamado, um HRESULT valor CORDBG_E_CANNOT_RESOLVE_ASSEMBLY será retornado.

## <a name="requirements"></a>Requisitos

**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).

**Cabeçalho:** CorDebug.idl, CorDebug.h

**Biblioteca:** CorGuids.lib

**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
