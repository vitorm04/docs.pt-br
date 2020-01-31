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
ms.openlocfilehash: b2fca16b3b859df8bd7409149eb5a3cf7b011c5c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864577"
---
# <a name="icorprofilerfunctioncontrolsetilinstrumentedcodemap-method"></a><span data-ttu-id="ca739-102">Método ICorProfilerFunctionControl::SetILInstrumentedCodeMap</span><span class="sxs-lookup"><span data-stu-id="ca739-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap Method</span></span>
<span data-ttu-id="ca739-103">Define um mapa de códigos para a função especificada usando as entradas de mapa Common Intermediate Language (CIL) especificadas.</span><span class="sxs-lookup"><span data-stu-id="ca739-103">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca739-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ca739-104">Syntax</span></span>  
  
```cpp  
HRESULT SetILInstrumentedCodeMap(  
    [in]   ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca739-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ca739-105">Parameters</span></span>  
 `cILMapEntries`  
 <span data-ttu-id="ca739-106">[in] O número de entradas no mapa.</span><span class="sxs-lookup"><span data-stu-id="ca739-106">[in] The number of entries in the map.</span></span>  
  
 `rgILMapEntries`  
 <span data-ttu-id="ca739-107">[in] A matriz alocada pelo chamador de entradas COR_IL_MAP.</span><span class="sxs-lookup"><span data-stu-id="ca739-107">[in] The caller-allocated array of COR_IL_MAP  entries.</span></span> <span data-ttu-id="ca739-108">A interpretação dessas entradas é a mesma do método [ICorProfilerInfo:: SetILInstrumentedCodeMap](icorprofilerinfo-setilinstrumentedcodemap-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ca739-108">The interpretation of these entries is the same as for the [ICorProfilerInfo::SetILInstrumentedCodeMap](icorprofilerinfo-setilinstrumentedcodemap-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca739-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="ca739-109">Remarks</span></span>  
 <span data-ttu-id="ca739-110">Definir o mapeamento chamando esse método permite que o depurador recupere o mapeamento chamando [ICorDebugILCode2:: GetInstrumentedILMap](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span><span class="sxs-lookup"><span data-stu-id="ca739-110">Setting the mapping by calling this method allows the debugger to retrieve the mapping by calling [ICorDebugILCode2::GetInstrumentedILMap](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span></span> <span data-ttu-id="ca739-111">Ele permite também que o depurador use o mapeamento internamente ao calcular deslocamentos de IL para rastreamentos de pilha e tempos de vida variáveis.</span><span class="sxs-lookup"><span data-stu-id="ca739-111">It also allows the debugger to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca739-112">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="ca739-112">Requirements</span></span>  
 <span data-ttu-id="ca739-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca739-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca739-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ca739-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ca739-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca739-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca739-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca739-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca739-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="ca739-117">See also</span></span>

- [<span data-ttu-id="ca739-118">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="ca739-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
