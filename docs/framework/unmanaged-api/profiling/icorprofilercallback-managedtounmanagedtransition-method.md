---
title: Método ICorProfilerCallback::ManagedToUnmanagedTransition
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ManagedToUnmanagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ManagedToUnmanagedTransition
helpviewer_keywords:
- ManagedToUnmanagedTransition method [.NET Framework profiling]
- ICorProfilerCallback::ManagedToUnmanagedTransition method [.NET Framework profiling]
ms.assetid: ef3cd619-912d-40c5-a449-03ba02a39ee7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0a3d784aa9d6d71418e2a48f56c7de08d3fe3d80
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694474"
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a><span data-ttu-id="ec3cf-102">Método ICorProfilerCallback::ManagedToUnmanagedTransition</span><span class="sxs-lookup"><span data-stu-id="ec3cf-102">ICorProfilerCallback::ManagedToUnmanagedTransition Method</span></span>
<span data-ttu-id="ec3cf-103">Notifica o criador de perfil que ocorreu uma transição de código gerenciado para código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="ec3cf-103">Notifies the profiler that a transition from managed code to unmanaged code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec3cf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ec3cf-104">Syntax</span></span>  
  
```  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ec3cf-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ec3cf-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="ec3cf-106">[in] A ID da função que está sendo chamada.</span><span class="sxs-lookup"><span data-stu-id="ec3cf-106">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="ec3cf-107">[in] Um valor igual a [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) enumeração que indica se a transição ocorreu devido a uma chamada para código não gerenciado a partir do código gerenciado, ou devido a um retorno de uma função gerenciada chamada por uma não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="ec3cf-107">[in] A value of the [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into unmanaged code from managed code, or because of a return from a managed function called by an unmanaged one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec3cf-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="ec3cf-108">Remarks</span></span>  
 <span data-ttu-id="ec3cf-109">Se o valor de `reason` é COR_PRF_TRANSITION_CALL, a função ID é que da função não gerenciada, que nunca foram compilado usando o compilador just-in-time.</span><span class="sxs-lookup"><span data-stu-id="ec3cf-109">If the value of `reason` is COR_PRF_TRANSITION_CALL, the function ID is that of the unmanaged function, which will never have been compiled using the just-in-time compiler.</span></span> <span data-ttu-id="ec3cf-110">Funções não gerenciadas têm informações básicas associadas a eles, como um nome e alguns metadados.</span><span class="sxs-lookup"><span data-stu-id="ec3cf-110">Unmanaged functions have basic information associated with them, such as a name and some metadata.</span></span> <span data-ttu-id="ec3cf-111">Se a função não gerenciada foi chamada usando a plataforma implícita invocação (PInvoke), o tempo de execução não é possível determinar o destino da chamada e o valor de `functionId` será nulo.</span><span class="sxs-lookup"><span data-stu-id="ec3cf-111">If the unmanaged function was called by using implicit platform invoke (PInvoke), the runtime cannot determine the destination of the call and the value of `functionId` will be null.</span></span> <span data-ttu-id="ec3cf-112">Para obter mais informações sobre PInvoke implícita, consulte [usando Interop do C++ (PInvoke implícito)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).</span><span class="sxs-lookup"><span data-stu-id="ec3cf-112">For more information on implicit PInvoke, see [Using C++ Interop (Implicit PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec3cf-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ec3cf-113">Requirements</span></span>  
 <span data-ttu-id="ec3cf-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec3cf-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec3cf-115">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ec3cf-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ec3cf-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec3cf-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec3cf-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec3cf-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec3cf-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ec3cf-118">See also</span></span>
- [<span data-ttu-id="ec3cf-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="ec3cf-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="ec3cf-120">Método UnmanagedToManagedTransition</span><span class="sxs-lookup"><span data-stu-id="ec3cf-120">UnmanagedToManagedTransition Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)
- [<span data-ttu-id="ec3cf-121">Usando PInvoke explícito no C++ (atributo DllImport)</span><span class="sxs-lookup"><span data-stu-id="ec3cf-121">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
