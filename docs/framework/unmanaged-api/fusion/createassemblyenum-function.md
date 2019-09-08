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
ms.openlocfilehash: 1db72c44b53b5abff9aee35094abc1e0e577fad4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795379"
---
# <a name="createassemblyenum-function"></a><span data-ttu-id="facfb-102">Função CreateAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="facfb-102">CreateAssemblyEnum Function</span></span>
<span data-ttu-id="facfb-103">Obtém um ponteiro para uma instância de [IAssemblyEnum](iassemblyenum-interface.md) que pode enumerar os objetos no assembly com o [IAssemblyName](iassemblyname-interface.md)especificado.</span><span class="sxs-lookup"><span data-stu-id="facfb-103">Gets a pointer to an [IAssemblyEnum](iassemblyenum-interface.md) instance that can enumerate the objects in the assembly with the specified [IAssemblyName](iassemblyname-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="facfb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="facfb-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="facfb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="facfb-105">Parameters</span></span>  
 `pEnum`  
 <span data-ttu-id="facfb-106">fora Ponteiro para um local de memória que contém o `IAssemblyEnum` ponteiro solicitado.</span><span class="sxs-lookup"><span data-stu-id="facfb-106">[out] Pointer to a memory location that contains the requested `IAssemblyEnum` pointer.</span></span>  
  
 `pUnkReserved`  
 <span data-ttu-id="facfb-107">no Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="facfb-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="facfb-108">`pUnkReserved`deve ser uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="facfb-108">`pUnkReserved` must be a null reference.</span></span>  
  
 `pName`  
 <span data-ttu-id="facfb-109">no O `IAssemblyName` do assembly solicitado.</span><span class="sxs-lookup"><span data-stu-id="facfb-109">[in] The `IAssemblyName` of the requested assembly.</span></span> <span data-ttu-id="facfb-110">Esse nome é usado para filtrar a enumeração.</span><span class="sxs-lookup"><span data-stu-id="facfb-110">This name is used to filter the enumeration.</span></span> <span data-ttu-id="facfb-111">Pode ser NULL para enumerar todos os assemblies no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="facfb-111">It can be null to enumerate all assemblies in the global assembly cache.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="facfb-112">no Sinalizadores para modificar o comportamento do enumerador.</span><span class="sxs-lookup"><span data-stu-id="facfb-112">[in] Flags for modifying the enumerator's behavior.</span></span> <span data-ttu-id="facfb-113">Esse parâmetro contém exatamente um bit da enumeração [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="facfb-113">This parameter contains exactly one bit from the [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) enumeration.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="facfb-114">no Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="facfb-114">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="facfb-115">`pvReserved`deve ser uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="facfb-115">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="facfb-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="facfb-116">Remarks</span></span>  
 <span data-ttu-id="facfb-117">O `dwFlags` parâmetro contém exatamente um bit `ASM_CACHE_FLAGS` da enumeração.</span><span class="sxs-lookup"><span data-stu-id="facfb-117">The `dwFlags` parameter contains exactly one bit from the `ASM_CACHE_FLAGS` enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="facfb-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="facfb-118">Requirements</span></span>  
 <span data-ttu-id="facfb-119">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="facfb-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="facfb-120">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="facfb-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="facfb-121">**Biblioteca** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="facfb-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="facfb-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="facfb-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="facfb-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="facfb-123">See also</span></span>

- [<span data-ttu-id="facfb-124">Interface IAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="facfb-124">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
- [<span data-ttu-id="facfb-125">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="facfb-125">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="facfb-126">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="facfb-126">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
