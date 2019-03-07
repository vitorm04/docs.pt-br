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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25861b2635605042acc1bf81f3f7a4739e678522
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57493104"
---
# <a name="icordebugassemblyenumnext-method"></a><span data-ttu-id="705ea-102">Método ICorDebugAssemblyEnum::Next</span><span class="sxs-lookup"><span data-stu-id="705ea-102">ICorDebugAssemblyEnum::Next Method</span></span>
<span data-ttu-id="705ea-103">Obtém o número especificado de assemblies de coleção, começando na posição atual do cursor.</span><span class="sxs-lookup"><span data-stu-id="705ea-103">Gets the specified number of assemblies from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="705ea-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="705ea-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugAssembly *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="705ea-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="705ea-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="705ea-106">[in] O número de assemblies a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="705ea-106">[in] The number of assemblies to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="705ea-107">[out] Uma matriz de ponteiros, cada um deles aponta para um objeto de ICorDebugAssembly que representa um assembly.</span><span class="sxs-lookup"><span data-stu-id="705ea-107">[out] An array of pointers, each of which points to an ICorDebugAssembly object that represents an assembly.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="705ea-108">[out] Um ponteiro para o número de assemblies, na verdade, é retornado.</span><span class="sxs-lookup"><span data-stu-id="705ea-108">[out] A pointer to the number of assemblies actually returned.</span></span> <span data-ttu-id="705ea-109">Esse valor pode ser nulo se `celt` é um.</span><span class="sxs-lookup"><span data-stu-id="705ea-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="705ea-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="705ea-110">Requirements</span></span>  
 <span data-ttu-id="705ea-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="705ea-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="705ea-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="705ea-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="705ea-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="705ea-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="705ea-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="705ea-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
