---
title: Método ICorProfilerCallback::JITInlining
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITInlining
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITInlining
helpviewer_keywords:
- JITInlining method [.NET Framework profiling]
- ICorProfilerCallback::JITInlining method [.NET Framework profiling]
ms.assetid: c2f45801-dd38-4b78-b6b7-64397dc73f83
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 60183291fda551e328ee1def03c02240314a71e4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598227"
---
# <a name="icorprofilercallbackjitinlining-method"></a><span data-ttu-id="36744-102">Método ICorProfilerCallback::JITInlining</span><span class="sxs-lookup"><span data-stu-id="36744-102">ICorProfilerCallback::JITInlining Method</span></span>
<span data-ttu-id="36744-103">Notifica o criador de perfil que o compilador just-in-time (JIT) está prestes a inserir uma função alinhada com outra função.</span><span class="sxs-lookup"><span data-stu-id="36744-103">Notifies the profiler that the just-in-time (JIT) compiler is about to insert a function in line with another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36744-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="36744-104">Syntax</span></span>  
  
```  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36744-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="36744-105">Parameters</span></span>  
 `callerId`  
 <span data-ttu-id="36744-106">[in] A ID da função na qual o `calleeId` função será inserida.</span><span class="sxs-lookup"><span data-stu-id="36744-106">[in] The ID of the function into which the `calleeId` function will be inserted.</span></span>  
  
 `calleeId`  
 <span data-ttu-id="36744-107">[in] A ID da função a ser inserido.</span><span class="sxs-lookup"><span data-stu-id="36744-107">[in] The ID of the function to be inserted.</span></span>  
  
 `pfShouldInline`  
 <span data-ttu-id="36744-108">[out] `true` para permitir a inserção ocorrer; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="36744-108">[out] `true` to allow the insertion to occur; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36744-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="36744-109">Remarks</span></span>  
 <span data-ttu-id="36744-110">O criador de perfil pode definir `pfShouldInline` à `false` para impedir que o `calleeId` função seja inserido no `callerId` função.</span><span class="sxs-lookup"><span data-stu-id="36744-110">The profiler can set `pfShouldInline` to `false` to prevent the `calleeId` function from being inserted into the `callerId` function.</span></span> <span data-ttu-id="36744-111">Além disso, o criador de perfil pode desativar globalmente a inserção embutido usando o valor COR_PRF_DISABLE_INLINING a [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="36744-111">Also, the profiler can globally disable inline insertion by using the COR_PRF_DISABLE_INLINING value of the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="36744-112">Funções inseridas embutido não acionar eventos para entrar ou sair.</span><span class="sxs-lookup"><span data-stu-id="36744-112">Functions inserted inline do not raise events for entering or leaving.</span></span> <span data-ttu-id="36744-113">Portanto, o criador de perfil deve definir `pfShouldInline` para `false` para produzir um gráfico de chamadas de preciso.</span><span class="sxs-lookup"><span data-stu-id="36744-113">Therefore, the profiler must set `pfShouldInline` to `false` in order to produce an accurate callgraph.</span></span> <span data-ttu-id="36744-114">Definindo `pfShouldInline` para `false` afetará o desempenho, porque a inserção embutidos geralmente aumenta a velocidade e reduz o número de eventos de compilação JIT separados para o método inserido.</span><span class="sxs-lookup"><span data-stu-id="36744-114">Setting `pfShouldInline` to `false` will affect performance, because inline insertion typically increases speed and reduces the number of separate JIT compilation events for the inserted method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36744-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="36744-115">Requirements</span></span>  
 <span data-ttu-id="36744-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36744-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36744-117">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="36744-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="36744-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36744-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36744-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36744-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36744-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36744-120">See also</span></span>

- [<span data-ttu-id="36744-121">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="36744-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
