---
title: Método ICorProfilerFunctionControl::SetILInstrumentedCodeMap
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetIILInstrumentedCodeMap method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: ecf56646-7e5f-46c4-8340-f3a04e88920f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 81880f5f97d1c8f16c80f3e3cb2a1be506d44e2d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54571029"
---
# <a name="icorprofilerfunctioncontrolsetilinstrumentedcodemap-method"></a><span data-ttu-id="48275-102">Método ICorProfilerFunctionControl::SetILInstrumentedCodeMap</span><span class="sxs-lookup"><span data-stu-id="48275-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap Method</span></span>
<span data-ttu-id="48275-103">Define um mapa de códigos para a função especificada usando as entradas de mapa Common Intermediate Language (CIL) especificadas.</span><span class="sxs-lookup"><span data-stu-id="48275-103">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48275-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="48275-104">Syntax</span></span>  
  
```  
HRESULT SetILInstrumentedCodeMap(  
    [in]   ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="48275-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="48275-105">Parameters</span></span>  
 `cILMapEntries`  
 <span data-ttu-id="48275-106">[in] O número de entradas no mapa.</span><span class="sxs-lookup"><span data-stu-id="48275-106">[in] The number of entries in the map.</span></span>  
  
 `rgILMapEntries`  
 <span data-ttu-id="48275-107">[in] A matriz alocada pelo chamador de entradas COR_IL_MAP.</span><span class="sxs-lookup"><span data-stu-id="48275-107">[in] The caller-allocated array of COR_IL_MAP  entries.</span></span> <span data-ttu-id="48275-108">A interpretação dessas entradas é a mesma usada para o [ICorProfilerInfo:: Setilinstrumentedcodemap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="48275-108">The interpretation of these entries is the same as for the [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48275-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="48275-109">Remarks</span></span>  
 <span data-ttu-id="48275-110">Configuração do mapeamento chamando esse método permite que o depurador recuperar o mapeamento chamando [ICorDebugILCode2::GetInstrumentedILMap](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span><span class="sxs-lookup"><span data-stu-id="48275-110">Setting the mapping by calling this method allows the debugger to retrieve the mapping by calling [ICorDebugILCode2::GetInstrumentedILMap](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span></span> <span data-ttu-id="48275-111">Ele permite também que o depurador use o mapeamento internamente ao calcular deslocamentos de IL para rastreamentos de pilha e tempos de vida variáveis.</span><span class="sxs-lookup"><span data-stu-id="48275-111">It also allows the debugger to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48275-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="48275-112">Requirements</span></span>  
 <span data-ttu-id="48275-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48275-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48275-114">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="48275-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="48275-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48275-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48275-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48275-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48275-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="48275-117">See also</span></span>
- [<span data-ttu-id="48275-118">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="48275-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
