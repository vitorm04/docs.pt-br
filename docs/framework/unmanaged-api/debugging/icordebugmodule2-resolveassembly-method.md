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
# <a name="icordebugmodule2resolveassembly-method"></a><span data-ttu-id="38624-102">Método ICorDebugModule2::ResolveAssembly</span><span class="sxs-lookup"><span data-stu-id="38624-102">ICorDebugModule2::ResolveAssembly Method</span></span>

<span data-ttu-id="38624-103">Resolve o assembly referenciado pelo token de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="38624-103">Resolves the assembly referenced by the specified metadata token.</span></span>

## <a name="syntax"></a><span data-ttu-id="38624-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="38624-104">Syntax</span></span>

```cpp
HRESULT ResolveAssembly (
    [in]  mdToken             tkAssemblyRef,
    [out] ICorDebugAssembly   **ppAssembly
);
```

## <a name="parameters"></a><span data-ttu-id="38624-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="38624-105">Parameters</span></span>

`tkAssemblyRef`\
<span data-ttu-id="38624-106">no Um valor `mdToken` que faz referência ao assembly.</span><span class="sxs-lookup"><span data-stu-id="38624-106">[in] An `mdToken` value that references the assembly.</span></span>

`ppAssembly`\
<span data-ttu-id="38624-107">fora Um ponteiro para o endereço de um objeto ICorDebugAssembly que representa o assembly.</span><span class="sxs-lookup"><span data-stu-id="38624-107">[out] A pointer to the address of an ICorDebugAssembly object that represents the assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="38624-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="38624-108">Remarks</span></span>

<span data-ttu-id="38624-109">Se o assembly ainda não estiver carregado quando `ResolveAssembly` for chamado, um valor HRESULT de CORDBG_E_CANNOT_RESOLVE_ASSEMBLY será retornado.</span><span class="sxs-lookup"><span data-stu-id="38624-109">If the assembly is not already loaded when `ResolveAssembly` is called, an HRESULT value of CORDBG_E_CANNOT_RESOLVE_ASSEMBLY is returned.</span></span>

## <a name="requirements"></a><span data-ttu-id="38624-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="38624-110">Requirements</span></span>

<span data-ttu-id="38624-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38624-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="38624-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="38624-112">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="38624-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38624-113">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="38624-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38624-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
