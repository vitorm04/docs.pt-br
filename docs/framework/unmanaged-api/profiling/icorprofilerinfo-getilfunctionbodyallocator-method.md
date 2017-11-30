---
title: "Método ICorProfilerInfo::GetILFunctionBodyAllocator"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetILFunctionBodyAllocator
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetILFunctionBodyAllocator
helpviewer_keywords:
- GetILFunctionBodyAllocator method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBodyAllocator method [.NET Framework profiling]
ms.assetid: 5da1bf3d-dddf-4892-b266-578ee54d570b
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 45a50fc39f2df9d4998f8490ff4382c84c5aa9bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogetilfunctionbodyallocator-method"></a><span data-ttu-id="f5c66-102">Método ICorProfilerInfo::GetILFunctionBodyAllocator</span><span class="sxs-lookup"><span data-stu-id="f5c66-102">ICorProfilerInfo::GetILFunctionBodyAllocator Method</span></span>
<span data-ttu-id="f5c66-103">Obtém uma interface que fornece um método para alocar memória para ser usada para alternar o corpo de um método no código Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="f5c66-103">Gets an interface that provides a method to allocate memory to be used for swapping out the body of a method in Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5c66-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f5c66-104">Syntax</span></span>  
  
```  
HRESULT GetILFunctionBodyAllocator(  
    [in]  ModuleID      moduleId,  
    [out] IMethodMalloc **ppMalloc);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f5c66-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f5c66-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="f5c66-106">[in] A ID do módulo no qual reside o método.</span><span class="sxs-lookup"><span data-stu-id="f5c66-106">[in] The ID of the module in which the method resides.</span></span>  
  
 `ppMalloc`  
 <span data-ttu-id="f5c66-107">[out] Um ponteiro para um [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interface que fornece um método para alocar a memória.</span><span class="sxs-lookup"><span data-stu-id="f5c66-107">[out] A pointer to an [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interface that provides a method to allocate the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5c66-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="f5c66-108">Remarks</span></span>  
 <span data-ttu-id="f5c66-109">Um corpo de método no código MSIL deve estar localizado como um endereço virtual relativo (RVA), em relação ao módulo carregado, o que significa que ele segue o módulo dentro de 4 GB.</span><span class="sxs-lookup"><span data-stu-id="f5c66-109">A method body in MSIL code must be located as a relative virtual address (RVA), relative to the loaded module, which means that it follows the module within 4 GB.</span></span> <span data-ttu-id="f5c66-110">Para tornar mais fácil para uma ferramenta para alternar o corpo de um método, o `GetILFunctionBodyAllocator` método garante que a memória é alocada dentro desse intervalo.</span><span class="sxs-lookup"><span data-stu-id="f5c66-110">To make it easier for a tool to swap out the body of a method, the `GetILFunctionBodyAllocator` method ensures that memory is allocated within that range.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5c66-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f5c66-111">Requirements</span></span>  
 <span data-ttu-id="f5c66-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5c66-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5c66-113">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f5c66-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f5c66-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5c66-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5c66-115">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5c66-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5c66-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f5c66-116">See Also</span></span>  
 [<span data-ttu-id="f5c66-117">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="f5c66-117">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
