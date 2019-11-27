---
title: Método ICorProfilerCallback::UnmanagedToManagedTransition
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.UnmanagedToManagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition
helpviewer_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition method [.NET Framework profiling]
- UnmanagedToManagedTransition method [.NET Framework profiling]
ms.assetid: ade2cc01-9b81-4e09-a5f9-b3b9dda27e96
topic_type:
- apiref
ms.openlocfilehash: 8c4e132b90fa1f51bc6f858d75c159af212ec019
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439897"
---
# <a name="icorprofilercallbackunmanagedtomanagedtransition-method"></a><span data-ttu-id="b4076-102">Método ICorProfilerCallback::UnmanagedToManagedTransition</span><span class="sxs-lookup"><span data-stu-id="b4076-102">ICorProfilerCallback::UnmanagedToManagedTransition Method</span></span>
<span data-ttu-id="b4076-103">Notifica o criador de perfil de que uma transição de código não gerenciado para código gerenciado ocorreu.</span><span class="sxs-lookup"><span data-stu-id="b4076-103">Notifies the profiler that a transition from unmanaged code to managed code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4076-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b4076-104">Syntax</span></span>  
  
```cpp  
HRESULT UnmanagedToManagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4076-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b4076-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="b4076-106">no A ID da função que está sendo chamada.</span><span class="sxs-lookup"><span data-stu-id="b4076-106">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="b4076-107">no Um valor da enumeração [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) que indica se a transição ocorreu devido a uma chamada em código gerenciado a partir de código não gerenciado ou por causa de um retorno de uma função não gerenciada chamada por um gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b4076-107">[in] A value of the [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into managed code from unmanaged code, or because of a return from an unmanaged function called by a managed one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4076-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="b4076-108">Remarks</span></span>  
 <span data-ttu-id="b4076-109">Se o valor de `reason` for COR_PRF_TRANSITION_RETURN e `functionId` não for NULL, a ID da função será a da função não gerenciada e nunca terá sido compilada usando o compilador JIT (just-in-time).</span><span class="sxs-lookup"><span data-stu-id="b4076-109">If the value of `reason` is COR_PRF_TRANSITION_RETURN and `functionId` is not null, the function ID is that of the unmanaged function, and will never have been compiled using the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="b4076-110">As funções não gerenciadas têm algumas informações básicas associadas a elas, como um nome e alguns metadados.</span><span class="sxs-lookup"><span data-stu-id="b4076-110">Unmanaged functions have some basic information associated with them, such as a name and some metadata.</span></span>  
  
 <span data-ttu-id="b4076-111">Se o valor de `reason` for COR_PRF_TRANSITION_CALL, talvez seja possível que a função chamada (ou seja, a função gerenciada) ainda não tenha sido compilada por JIT.</span><span class="sxs-lookup"><span data-stu-id="b4076-111">If the value of `reason` is COR_PRF_TRANSITION_CALL, it may be possible that the called function (that is, the managed function) has not yet been JIT-compiled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4076-112">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="b4076-112">Requirements</span></span>  
 <span data-ttu-id="b4076-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4076-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4076-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b4076-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b4076-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4076-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4076-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4076-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4076-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b4076-117">See also</span></span>

- [<span data-ttu-id="b4076-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="b4076-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="b4076-119">Método ManagedToUnmanagedTransition</span><span class="sxs-lookup"><span data-stu-id="b4076-119">ManagedToUnmanagedTransition Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)
- [<span data-ttu-id="b4076-120">Usando PInvoke explícito no C++ (atributo DllImport)</span><span class="sxs-lookup"><span data-stu-id="b4076-120">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
- [<span data-ttu-id="b4076-121">Usando interop do C++ (PInvoke implícito)</span><span class="sxs-lookup"><span data-stu-id="b4076-121">Using C++ Interop (Implicit PInvoke)</span></span>](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)
