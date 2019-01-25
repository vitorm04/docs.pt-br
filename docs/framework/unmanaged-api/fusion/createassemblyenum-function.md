---
title: Função CreateAssemblyEnum
ms.date: 03/30/2017
api_name:
- CreateAssemblyEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyEnum
helpviewer_keywords:
- CreateAssemblyEnum function [.NET Framework fusion]
ms.assetid: 3506df38-6cea-42f6-946e-4287863bcfb3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d809bbfa17ed9e9ae16505852740e874ca11248c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54621780"
---
# <a name="createassemblyenum-function"></a><span data-ttu-id="60a60-102">Função CreateAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="60a60-102">CreateAssemblyEnum Function</span></span>
<span data-ttu-id="60a60-103">Obtém um ponteiro para um [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) instância que pode enumerar os objetos no assembly especificado [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md).</span><span class="sxs-lookup"><span data-stu-id="60a60-103">Gets a pointer to an [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) instance that can enumerate the objects in the assembly with the specified [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60a60-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="60a60-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="60a60-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="60a60-105">Parameters</span></span>  
 `pEnum`  
 <span data-ttu-id="60a60-106">[out] Ponteiro para um local de memória que contém o solicitada `IAssemblyEnum` ponteiro.</span><span class="sxs-lookup"><span data-stu-id="60a60-106">[out] Pointer to a memory location that contains the requested `IAssemblyEnum` pointer.</span></span>  
  
 `pUnkReserved`  
 <span data-ttu-id="60a60-107">[in] Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="60a60-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="60a60-108">`pUnkReserved` deve ser uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="60a60-108">`pUnkReserved` must be a null reference.</span></span>  
  
 `pName`  
 <span data-ttu-id="60a60-109">[in] O `IAssemblyName` do assembly solicitado.</span><span class="sxs-lookup"><span data-stu-id="60a60-109">[in] The `IAssemblyName` of the requested assembly.</span></span> <span data-ttu-id="60a60-110">Esse nome é usado para filtrar a enumeração.</span><span class="sxs-lookup"><span data-stu-id="60a60-110">This name is used to filter the enumeration.</span></span> <span data-ttu-id="60a60-111">Ele pode ser nulo para enumerar todos os assemblies no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="60a60-111">It can be null to enumerate all assemblies in the global assembly cache.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="60a60-112">[in] Sinalizadores para modificar o comportamento do enumerador.</span><span class="sxs-lookup"><span data-stu-id="60a60-112">[in] Flags for modifying the enumerator's behavior.</span></span> <span data-ttu-id="60a60-113">Este parâmetro contém exatamente um bit do [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="60a60-113">This parameter contains exactly one bit from the [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) enumeration.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="60a60-114">[in] Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="60a60-114">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="60a60-115">`pvReserved` deve ser uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="60a60-115">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60a60-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="60a60-116">Remarks</span></span>  
 <span data-ttu-id="60a60-117">O `dwFlags` parâmetro contém exatamente um bit do `ASM_CACHE_FLAGS` enumeração.</span><span class="sxs-lookup"><span data-stu-id="60a60-117">The `dwFlags` parameter contains exactly one bit from the `ASM_CACHE_FLAGS` enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60a60-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="60a60-118">Requirements</span></span>  
 <span data-ttu-id="60a60-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60a60-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60a60-120">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="60a60-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="60a60-121">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="60a60-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="60a60-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60a60-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60a60-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="60a60-123">See also</span></span>
- [<span data-ttu-id="60a60-124">Interface IAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="60a60-124">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
- [<span data-ttu-id="60a60-125">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="60a60-125">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="60a60-126">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="60a60-126">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
