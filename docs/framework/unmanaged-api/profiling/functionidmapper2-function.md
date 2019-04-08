---
title: Função FunctionIDMapper2
ms.date: 03/30/2017
api_name:
- FunctionIDMapper2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper2
helpviewer_keywords:
- FunctionIDMapper2 function [.NET Framework profiling]
ms.assetid: 466ad51b-8f0c-41d9-81f7-371aac3374cb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1a236dcae29d00afe3b72dce8f81d657fb4fac28
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59082497"
---
# <a name="functionidmapper2-function"></a><span data-ttu-id="d6c81-102">Função FunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="d6c81-102">FunctionIDMapper2 Function</span></span>
<span data-ttu-id="d6c81-103">Notifica o criador de perfil que o identificador fornecido de uma função pode ser remapeado para uma ID alternativa a ser usado na [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), e [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), ou[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), e [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) retornos de chamada para essa função.</span><span class="sxs-lookup"><span data-stu-id="d6c81-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), or[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) callbacks for that function.</span></span> `FunctionIDMapper2` <span data-ttu-id="d6c81-104">também permite que o criador de perfil indicar se deseja receber retornos de chamada para essa função.</span><span class="sxs-lookup"><span data-stu-id="d6c81-104">also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6c81-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d6c81-105">Syntax</span></span>  
  
```  
UINT_PTR __stdcall FunctionIDMapper2 (  
    [in]  FunctionID  funcId,  
    [in]  void * clientData,  
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6c81-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d6c81-106">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="d6c81-107">[in] O identificador de função a ser remapeado.</span><span class="sxs-lookup"><span data-stu-id="d6c81-107">[in] The function identifier to be remapped.</span></span>  
  
 `clientData`  
 <span data-ttu-id="d6c81-108">[in] Um ponteiro para dados que são usados para resolver a ambiguidade os tempos de execução.</span><span class="sxs-lookup"><span data-stu-id="d6c81-108">[in] A pointer to data that is used to disambiguate among runtimes.</span></span>  
  
 `pbHookFunction`  
 <span data-ttu-id="d6c81-109">[out] Um ponteiro para um valor que o criador de perfil define como `true` se desejar receber `FunctionEnter3`, `FunctionLeave3`, e `FunctionTailcall3`, ou `FunctionEnter3WithInfo`, `FunctionLeave3WithInfo`, e `FunctionTailcall3WithInfo` retornos de chamada; caso contrário, ele define esse valor para `false`.</span><span class="sxs-lookup"><span data-stu-id="d6c81-109">[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter3`, `FunctionLeave3`, and `FunctionTailcall3`, or `FunctionEnter3WithInfo`, `FunctionLeave3WithInfo`, and `FunctionTailcall3WithInfo` callbacks; otherwise, it sets this value to `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6c81-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d6c81-110">Return Value</span></span>  
 <span data-ttu-id="d6c81-111">O criador de perfil retorna um valor que o mecanismo de execução usa como um identificador de função alternativa.</span><span class="sxs-lookup"><span data-stu-id="d6c81-111">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="d6c81-112">O valor de retorno não pode ser nulo, a menos que `false` é retornado no `pbHookFunction`.</span><span class="sxs-lookup"><span data-stu-id="d6c81-112">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="d6c81-113">Caso contrário, um valor de retorno nulo produz resultados imprevisíveis, incluindo, possivelmente, a interrupção do processo.</span><span class="sxs-lookup"><span data-stu-id="d6c81-113">Otherwise, a null return value produces unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6c81-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="d6c81-114">Remarks</span></span>  
 <span data-ttu-id="d6c81-115">Este método estende o [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) função com um parâmetro adicional que é usado para transmitir dados do cliente.</span><span class="sxs-lookup"><span data-stu-id="d6c81-115">This method extends the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function with an additional parameter that is used to pass client data.</span></span> <span data-ttu-id="d6c81-116">Os dados do cliente são usados para resolver a ambiguidade os tempos de execução.</span><span class="sxs-lookup"><span data-stu-id="d6c81-116">The client data is used to disambiguate among runtimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6c81-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d6c81-117">Requirements</span></span>  
 <span data-ttu-id="d6c81-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6c81-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6c81-119">**Cabeçalho:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="d6c81-119">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="d6c81-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6c81-120">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d6c81-121">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="d6c81-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d6c81-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6c81-122">See also</span></span>

- [<span data-ttu-id="d6c81-123">ICorProfilerInfo::SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="d6c81-123">ICorProfilerInfo::SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="d6c81-124">ICorProfilerInfo3::SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="d6c81-124">ICorProfilerInfo3::SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="d6c81-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="d6c81-125">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="d6c81-126">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="d6c81-126">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="d6c81-127">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="d6c81-127">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="d6c81-128">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="d6c81-128">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="d6c81-129">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="d6c81-129">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="d6c81-130">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="d6c81-130">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="d6c81-131">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="d6c81-131">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
