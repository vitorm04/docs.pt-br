---
title: "Método ICorProfilerInfo::SetILFunctionBody"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.SetILFunctionBody
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerInfo::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method [.NET Framework profiling]
ms.assetid: b159c712-00f4-4fc7-a990-40bf9f642e8f
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6d97827555ecefb775323fdf9dbd6577f941f1e9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfosetilfunctionbody-method"></a><span data-ttu-id="6c93b-102">Método ICorProfilerInfo::SetILFunctionBody</span><span class="sxs-lookup"><span data-stu-id="6c93b-102">ICorProfilerInfo::SetILFunctionBody Method</span></span>
<span data-ttu-id="6c93b-103">Substitui o corpo da função especificada no módulo especificado.</span><span class="sxs-lookup"><span data-stu-id="6c93b-103">Replaces the body of the specified function in the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c93b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6c93b-104">Syntax</span></span>  
  
```  
HRESULT SetILFunctionBody(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodid,  
    [in] LPCBYTE     pbNewILMethodHeader);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c93b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6c93b-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="6c93b-106">[in] A ID do módulo no qual a função reside.</span><span class="sxs-lookup"><span data-stu-id="6c93b-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodid`  
 <span data-ttu-id="6c93b-107">[in] O token da função para o qual substituir o corpo.</span><span class="sxs-lookup"><span data-stu-id="6c93b-107">[in] The token of the function for which to replace the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="6c93b-108">[in] O novo cabeçalho para a função.</span><span class="sxs-lookup"><span data-stu-id="6c93b-108">[in] The new header for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c93b-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="6c93b-109">Remarks</span></span>  
 <span data-ttu-id="6c93b-110">O `SetILFunctionBody` método substitui o endereço virtual relativo da função de metadados para que ele aponta para o corpo da nova função e ajusta as estruturas de dados interno conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="6c93b-110">The `SetILFunctionBody` method replaces the relative virtual address of the function in the metadata so that it points to the new function body, and adjusts any internal data structures as required.</span></span>  
  
 <span data-ttu-id="6c93b-111">O `SetILFunctionBody` método pode ser chamado em apenas as funções que nunca foi compiladas por um compilador just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="6c93b-111">The `SetILFunctionBody` method can be called on only those functions that have never been compiled by a just-in-time (JIT) compiler.</span></span>  
  
 <span data-ttu-id="6c93b-112">Use o [: Getilfunctionbodyallocator](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md) método para alocar espaço para o novo método garantir que o buffer é compatível.</span><span class="sxs-lookup"><span data-stu-id="6c93b-112">Use the [ICorProfilerInfo::GetILFunctionBodyAllocator](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md) method to allocate space for the new method to ensure that the buffer is compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c93b-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6c93b-113">Requirements</span></span>  
 <span data-ttu-id="6c93b-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c93b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c93b-115">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6c93b-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6c93b-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c93b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c93b-117">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c93b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c93b-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6c93b-118">See Also</span></span>  
 [<span data-ttu-id="6c93b-119">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="6c93b-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
