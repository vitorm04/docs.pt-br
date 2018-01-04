---
title: "Método IMethodMalloc::Alloc"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMethodMalloc.Alloc
api_location: mscorwks.dll
api_type: COM
f1_keywords: IMethodMalloc::Alloc
helpviewer_keywords:
- IMethodMalloc::Alloc method [.NET Framework profiling]
- Alloc method, IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8653bd4c-2290-43d2-a3e1-cbbd50033f4f
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 26998e8b2e8648b4fb175f188540e7bc33c580c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imethodmallocalloc-method"></a><span data-ttu-id="34fba-102">Método IMethodMalloc::Alloc</span><span class="sxs-lookup"><span data-stu-id="34fba-102">IMethodMalloc::Alloc Method</span></span>
<span data-ttu-id="34fba-103">Tenta alocar uma quantidade especificada de memória para um novo corpo de função do Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="34fba-103">Attempts to allocate a specified amount of memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34fba-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="34fba-104">Syntax</span></span>  
  
```  
PVOID Alloc (  
    [in] ULONG   cb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="34fba-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34fba-105">Parameters</span></span>  
 `cb`  
 <span data-ttu-id="34fba-106">[in] O número de bytes a ser alocada para o corpo do método.</span><span class="sxs-lookup"><span data-stu-id="34fba-106">[in] The number of bytes to allocate for the method body.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34fba-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="34fba-107">Remarks</span></span>  
 <span data-ttu-id="34fba-108">A memória alocada será iniciado em um maior que o endereço base do módulo que está associado este alocador de endereço.</span><span class="sxs-lookup"><span data-stu-id="34fba-108">The allocated memory will begin at an address greater than the base address of the module that is associated with this allocator.</span></span> <span data-ttu-id="34fba-109">Em outras palavras, cada alocador é criado para um módulo específico e tentará alocar memória em um deslocamento positivo de seu endereço base.</span><span class="sxs-lookup"><span data-stu-id="34fba-109">In other words, each allocator is created for a particular module, and will attempt to allocate memory at a positive offset from its base address.</span></span> <span data-ttu-id="34fba-110">Se `Alloc` Falha ao alocar o número solicitado de bytes em um endereço maior que o endereço base do módulo, ele retorna E_OUTOFMEMORY, independentemente da quantidade real de espaço de memória disponível.</span><span class="sxs-lookup"><span data-stu-id="34fba-110">If `Alloc` fails to allocate the requested number of bytes at an address greater than the base address of the module, it returns E_OUTOFMEMORY, regardless of the actual amount of memory space available.</span></span>  
  
 <span data-ttu-id="34fba-111">O `Alloc` método deve ser usado em conjunto com o [: Setilfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="34fba-111">The `Alloc` method should be used in conjunction with the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34fba-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="34fba-112">Requirements</span></span>  
 <span data-ttu-id="34fba-113">**Plataformas:** WindSee [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34fba-113">**Platforms:** WindSee [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34fba-114">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="34fba-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="34fba-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34fba-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34fba-116">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34fba-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34fba-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34fba-117">See Also</span></span>  
 [<span data-ttu-id="34fba-118">Interface IMethodMalloc</span><span class="sxs-lookup"><span data-stu-id="34fba-118">IMethodMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)
