---
title: "Função FunctionIDMapper2"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionIDMapper2
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionIDMapper2
helpviewer_keywords: FunctionIDMapper2 function [.NET Framework profiling]
ms.assetid: 466ad51b-8f0c-41d9-81f7-371aac3374cb
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5da0acdd7622ad06879b57d8d4b2a9faeba10ca9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="functionidmapper2-function"></a><span data-ttu-id="01f57-102">Função FunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="01f57-102">FunctionIDMapper2 Function</span></span>
<span data-ttu-id="01f57-103">Notifica o criador de perfil que o identificador especificado de uma função pode ser mapeado novamente para uma ID alternativa a ser usado no [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), e [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), ou[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), e [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) retornos de chamada para essa função.</span><span class="sxs-lookup"><span data-stu-id="01f57-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), or[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) callbacks for that function.</span></span> <span data-ttu-id="01f57-104">`FunctionIDMapper2`também permite que o criador de perfil indicar se deseja receber retornos de chamada para essa função.</span><span class="sxs-lookup"><span data-stu-id="01f57-104">`FunctionIDMapper2` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01f57-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="01f57-105">Syntax</span></span>  
  
```  
UINT_PTR __stdcall FunctionIDMapper2 (  
    [in]  FunctionID  funcId,  
    [in]  void * clientData,  
    [out] BOOL       *pbHookFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="01f57-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="01f57-106">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="01f57-107">[in] O identificador de função a ser remapeados.</span><span class="sxs-lookup"><span data-stu-id="01f57-107">[in] The function identifier to be remapped.</span></span>  
  
 `clientData`  
 <span data-ttu-id="01f57-108">[in] Um ponteiro para dados que são usados para resolver a ambiguidade entre os tempos de execução.</span><span class="sxs-lookup"><span data-stu-id="01f57-108">[in] A pointer to data that is used to disambiguate among runtimes.</span></span>  
  
 `pbHookFunction`  
 <span data-ttu-id="01f57-109">[out] Um ponteiro para um valor que define o criador de perfil para `true` se deseja receber `FunctionEnter3`, `FunctionLeave3`, e `FunctionTailcall3`, ou `FunctionEnter3WithInfo`, `FunctionLeave3WithInfo`, e `FunctionTailcall3WithInfo` retornos de chamada; caso contrário, ele define esse valor como `false`.</span><span class="sxs-lookup"><span data-stu-id="01f57-109">[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter3`, `FunctionLeave3`, and `FunctionTailcall3`, or `FunctionEnter3WithInfo`, `FunctionLeave3WithInfo`, and `FunctionTailcall3WithInfo` callbacks; otherwise, it sets this value to `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="01f57-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="01f57-110">Return Value</span></span>  
 <span data-ttu-id="01f57-111">O criador de perfil retorna um valor que usa o mecanismo de execução como um identificador de função alternativos.</span><span class="sxs-lookup"><span data-stu-id="01f57-111">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="01f57-112">O valor de retorno não pode ser nulo, a menos que `false` é retornado no `pbHookFunction`.</span><span class="sxs-lookup"><span data-stu-id="01f57-112">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="01f57-113">Caso contrário, um valor de retorno nulo produz resultados imprevisíveis, incluindo possivelmente interromper o processo.</span><span class="sxs-lookup"><span data-stu-id="01f57-113">Otherwise, a null return value produces unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01f57-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="01f57-114">Remarks</span></span>  
 <span data-ttu-id="01f57-115">Este método estende o [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) função com um parâmetro adicional que é usado para passar dados do cliente.</span><span class="sxs-lookup"><span data-stu-id="01f57-115">This method extends the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function with an additional parameter that is used to pass client data.</span></span> <span data-ttu-id="01f57-116">Os dados do cliente são usados para resolver a ambiguidade entre os tempos de execução.</span><span class="sxs-lookup"><span data-stu-id="01f57-116">The client data is used to disambiguate among runtimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01f57-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="01f57-117">Requirements</span></span>  
 <span data-ttu-id="01f57-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01f57-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01f57-119">**Cabeçalho:** Corprof. idl</span><span class="sxs-lookup"><span data-stu-id="01f57-119">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="01f57-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01f57-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01f57-121">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01f57-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01f57-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="01f57-122">See Also</span></span>  
 [<span data-ttu-id="01f57-123">: Setfunctionidmapper</span><span class="sxs-lookup"><span data-stu-id="01f57-123">ICorProfilerInfo::SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="01f57-124">ICorProfilerInfo3::SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="01f57-124">ICorProfilerInfo3::SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [<span data-ttu-id="01f57-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="01f57-125">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="01f57-126">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="01f57-126">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="01f57-127">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="01f57-127">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="01f57-128">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="01f57-128">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="01f57-129">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="01f57-129">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="01f57-130">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="01f57-130">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="01f57-131">Funções estáticas globais de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="01f57-131">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
