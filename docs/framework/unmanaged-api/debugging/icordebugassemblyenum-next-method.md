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
ms.openlocfilehash: 00adc852a0940766cdd4188ffa5d6be2b472e51f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744881"
---
# <a name="icordebugassemblyenumnext-method"></a><span data-ttu-id="e175f-102">Método ICorDebugAssemblyEnum::Next</span><span class="sxs-lookup"><span data-stu-id="e175f-102">ICorDebugAssemblyEnum::Next Method</span></span>
<span data-ttu-id="e175f-103">Obtém o número especificado de assemblies de coleção, começando na posição atual do cursor.</span><span class="sxs-lookup"><span data-stu-id="e175f-103">Gets the specified number of assemblies from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e175f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e175f-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugAssembly *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e175f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e175f-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="e175f-106">[in] O número de assemblies a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="e175f-106">[in] The number of assemblies to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="e175f-107">[out] Uma matriz de ponteiros, cada um deles aponta para um objeto de ICorDebugAssembly que representa um assembly.</span><span class="sxs-lookup"><span data-stu-id="e175f-107">[out] An array of pointers, each of which points to an ICorDebugAssembly object that represents an assembly.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="e175f-108">[out] Um ponteiro para o número de assemblies, na verdade, é retornado.</span><span class="sxs-lookup"><span data-stu-id="e175f-108">[out] A pointer to the number of assemblies actually returned.</span></span> <span data-ttu-id="e175f-109">Esse valor pode ser nulo se `celt` é um.</span><span class="sxs-lookup"><span data-stu-id="e175f-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e175f-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e175f-110">Requirements</span></span>  
 <span data-ttu-id="e175f-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e175f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e175f-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e175f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e175f-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e175f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e175f-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e175f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
