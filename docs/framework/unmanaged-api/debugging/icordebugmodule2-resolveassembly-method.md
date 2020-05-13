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
# <a name="icordebugmodule2resolveassembly-method"></a><span data-ttu-id="2f2be-102">Método ICorDebugModule2::ResolveAssembly</span><span class="sxs-lookup"><span data-stu-id="2f2be-102">ICorDebugModule2::ResolveAssembly Method</span></span>

<span data-ttu-id="2f2be-103">Resolve o assembly referenciado pelo token de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="2f2be-103">Resolves the assembly referenced by the specified metadata token.</span></span>

## <a name="syntax"></a><span data-ttu-id="2f2be-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2f2be-104">Syntax</span></span>

```cpp
HRESULT ResolveAssembly (
    [in]  mdToken             tkAssemblyRef,
    [out] ICorDebugAssembly   **ppAssembly
);
```

## <a name="parameters"></a><span data-ttu-id="2f2be-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2f2be-105">Parameters</span></span>

`tkAssemblyRef`\
<span data-ttu-id="2f2be-106">no Um `mdToken` valor que faz referência ao assembly.</span><span class="sxs-lookup"><span data-stu-id="2f2be-106">[in] An `mdToken` value that references the assembly.</span></span>

`ppAssembly`\
<span data-ttu-id="2f2be-107">fora Um ponteiro para o endereço de um objeto ICorDebugAssembly que representa o assembly.</span><span class="sxs-lookup"><span data-stu-id="2f2be-107">[out] A pointer to the address of an ICorDebugAssembly object that represents the assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="2f2be-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="2f2be-108">Remarks</span></span>

<span data-ttu-id="2f2be-109">Se o assembly ainda não estiver carregado quando `ResolveAssembly` for chamado, um valor HRESULT de CORDBG_E_CANNOT_RESOLVE_ASSEMBLY será retornado.</span><span class="sxs-lookup"><span data-stu-id="2f2be-109">If the assembly is not already loaded when `ResolveAssembly` is called, an HRESULT value of CORDBG_E_CANNOT_RESOLVE_ASSEMBLY is returned.</span></span>

## <a name="requirements"></a><span data-ttu-id="2f2be-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2f2be-110">Requirements</span></span>

<span data-ttu-id="2f2be-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f2be-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="2f2be-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2f2be-112">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="2f2be-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f2be-113">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="2f2be-114">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f2be-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
