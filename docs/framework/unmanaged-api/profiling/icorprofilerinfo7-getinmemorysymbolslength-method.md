---
title: Método ICorProfilerInfo7::GetInMemorySymbolsLength
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.GetInMemorySymbolsLength
api_location:
- mscorwks.dll
- icorprof.idl
api_type:
- COM
ms.assetid: d62c4a4c-8a62-45aa-8f01-a8387cf36159
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 64289ee7fbdc440a87df6c8e506317f23e780912
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722849"
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a><span data-ttu-id="30eec-102">Método ICorProfilerInfo7::GetInMemorySymbolsLength</span><span class="sxs-lookup"><span data-stu-id="30eec-102">ICorProfilerInfo7::GetInMemorySymbolsLength Method</span></span>
<span data-ttu-id="30eec-103">[Com suporte no .NET Framework 4.6.1 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="30eec-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="30eec-104">Retorna o comprimento de um fluxo de símbolo na memória.</span><span class="sxs-lookup"><span data-stu-id="30eec-104">Returns the length of an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30eec-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="30eec-105">Syntax</span></span>  
  
```  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="30eec-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="30eec-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="30eec-107">[in] O identificador do módulo que contém o fluxo de memória.</span><span class="sxs-lookup"><span data-stu-id="30eec-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 <span data-ttu-id="30eec-108">pCountSymbolBytes</span><span class="sxs-lookup"><span data-stu-id="30eec-108">pCountSymbolBytes</span></span>  
 <span data-ttu-id="30eec-109">[out] Um ponteiro para um `DWORD` valor que, quando o método retorna, contém o comprimento do fluxo em bytes.</span><span class="sxs-lookup"><span data-stu-id="30eec-109">[out] A pointer to a `DWORD` value that, when the method returns, contains the length of the stream in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="30eec-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="30eec-110">Return Value</span></span>  
 <span data-ttu-id="30eec-111">O método retorna `S_OK` se o comprimento do fluxo de memória pode ser determinado, mesmo se for zero (0).</span><span class="sxs-lookup"><span data-stu-id="30eec-111">The method returns `S_OK` if the length of the memory stream can be determined, even if it is zero (0).</span></span>  
  
 <span data-ttu-id="30eec-112">O método retornará `CORPROF_E_MODULE_IS_DYNAMIC` se o método foi criado usando <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="30eec-112">The method returns `CORPROF_E_MODULE_IS_DYNAMIC` if the method was created using <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30eec-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="30eec-113">Remarks</span></span>  
 <span data-ttu-id="30eec-114">Se o módulo tiver símbolos na memória, o comprimento do fluxo é colocado no `pCountSymbolBytes`.</span><span class="sxs-lookup"><span data-stu-id="30eec-114">If the module has in-memory symbols, the length of the stream is placed in `pCountSymbolBytes`.</span></span> <span data-ttu-id="30eec-115">Se o módulo não tem símbolos na memória, `*pCountSymbolBytes = 0`.</span><span class="sxs-lookup"><span data-stu-id="30eec-115">If the module doesn't have in-memory     symbols, `*pCountSymbolBytes = 0`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30eec-116">A implementação atual não oferece suporte a Reflection. Emit.</span><span class="sxs-lookup"><span data-stu-id="30eec-116">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="30eec-117">Se o módulo foi criado usando Reflection. Emit, o método retorna `CORPROF_E_MODULE_IS_DYNAMIC`.</span><span class="sxs-lookup"><span data-stu-id="30eec-117">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30eec-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="30eec-118">Requirements</span></span>  
 <span data-ttu-id="30eec-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30eec-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30eec-120">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="30eec-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="30eec-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30eec-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30eec-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30eec-122">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30eec-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30eec-123">See also</span></span>
- [<span data-ttu-id="30eec-124">Interface ICorProfilerInfo7</span><span class="sxs-lookup"><span data-stu-id="30eec-124">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
