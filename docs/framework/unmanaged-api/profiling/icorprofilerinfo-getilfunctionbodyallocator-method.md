---
title: Método ICorProfilerInfo::GetILFunctionBodyAllocator
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILFunctionBodyAllocator
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILFunctionBodyAllocator
helpviewer_keywords:
- GetILFunctionBodyAllocator method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBodyAllocator method [.NET Framework profiling]
ms.assetid: 5da1bf3d-dddf-4892-b266-578ee54d570b
topic_type:
- apiref
ms.openlocfilehash: 8af2b6834ac8655c64a7738c65550b515a4b6675
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439052"
---
# <a name="icorprofilerinfogetilfunctionbodyallocator-method"></a><span data-ttu-id="75444-102">Método ICorProfilerInfo::GetILFunctionBodyAllocator</span><span class="sxs-lookup"><span data-stu-id="75444-102">ICorProfilerInfo::GetILFunctionBodyAllocator Method</span></span>
<span data-ttu-id="75444-103">Obtém uma interface que fornece um método para alocar memória a ser usada para alternar o corpo de um método no código MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="75444-103">Gets an interface that provides a method to allocate memory to be used for swapping out the body of a method in Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75444-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="75444-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILFunctionBodyAllocator(  
    [in]  ModuleID      moduleId,  
    [out] IMethodMalloc **ppMalloc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75444-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75444-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="75444-106">no A ID do módulo no qual o método reside.</span><span class="sxs-lookup"><span data-stu-id="75444-106">[in] The ID of the module in which the method resides.</span></span>  
  
 `ppMalloc`  
 <span data-ttu-id="75444-107">fora Um ponteiro para uma interface [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) que fornece um método para alocar a memória.</span><span class="sxs-lookup"><span data-stu-id="75444-107">[out] A pointer to an [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interface that provides a method to allocate the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75444-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="75444-108">Remarks</span></span>  
 <span data-ttu-id="75444-109">Um corpo de método no código MSIL deve estar localizado como um endereço virtual relativo (RVA), relativo ao módulo carregado, o que significa que ele segue o módulo dentro de 4 GB.</span><span class="sxs-lookup"><span data-stu-id="75444-109">A method body in MSIL code must be located as a relative virtual address (RVA), relative to the loaded module, which means that it follows the module within 4 GB.</span></span> <span data-ttu-id="75444-110">Para tornar mais fácil para uma ferramenta alternar o corpo de um método, o método `GetILFunctionBodyAllocator` garante que a memória seja alocada dentro desse intervalo.</span><span class="sxs-lookup"><span data-stu-id="75444-110">To make it easier for a tool to swap out the body of a method, the `GetILFunctionBodyAllocator` method ensures that memory is allocated within that range.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75444-111">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="75444-111">Requirements</span></span>  
 <span data-ttu-id="75444-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75444-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75444-113">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="75444-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="75444-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="75444-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75444-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75444-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75444-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="75444-116">See also</span></span>

- [<span data-ttu-id="75444-117">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="75444-117">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
