---
title: Método ICorDebugAssemblyEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugAssemblyEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssemblyEnum::Next method
helpviewer_keywords:
- ICorDebugAssemblyEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugAssemblyEnum interface [.NET Framework debugging]
ms.assetid: b3e7d0c2-3baa-4ef8-8e3f-b865cf252940
topic_type:
- apiref
ms.openlocfilehash: 86fa44b609b4b89cfaa28f0bfa7bbdce6217623f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122865"
---
# <a name="icordebugassemblyenumnext-method"></a><span data-ttu-id="d2129-102">Método ICorDebugAssemblyEnum::Next</span><span class="sxs-lookup"><span data-stu-id="d2129-102">ICorDebugAssemblyEnum::Next Method</span></span>
<span data-ttu-id="d2129-103">Obtém o número especificado de assemblies da coleção, começando na posição atual do cursor.</span><span class="sxs-lookup"><span data-stu-id="d2129-103">Gets the specified number of assemblies from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2129-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d2129-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugAssembly *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2129-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d2129-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="d2129-106">no O número de assemblies a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="d2129-106">[in] The number of assemblies to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="d2129-107">fora Uma matriz de ponteiros, cada um dos quais aponta para um objeto ICorDebugAssembly que representa um assembly.</span><span class="sxs-lookup"><span data-stu-id="d2129-107">[out] An array of pointers, each of which points to an ICorDebugAssembly object that represents an assembly.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="d2129-108">fora Um ponteiro para o número de assemblies realmente retornados.</span><span class="sxs-lookup"><span data-stu-id="d2129-108">[out] A pointer to the number of assemblies actually returned.</span></span> <span data-ttu-id="d2129-109">Esse valor pode ser nulo se `celt` for um.</span><span class="sxs-lookup"><span data-stu-id="d2129-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2129-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d2129-110">Requirements</span></span>  
 <span data-ttu-id="d2129-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2129-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2129-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d2129-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d2129-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2129-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2129-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2129-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
